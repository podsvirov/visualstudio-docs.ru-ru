---
title: Инкрементные сборки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb11467d8d59e7af11741d7719da2858ac1a784c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192892"
---
# <a name="incremental-builds"></a>Инкрементные построения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Инкрементные сборки — это сборки, оптимизированные таким образом, чтобы целевые объекты с выходными файлами, которые актуальны в отношении соответствующих входных файлов, не выполнялись. Целевой элемент может иметь оба атрибута `Inputs` и `Outputs`, указывающих, какие элементы целевой объект ожидает в качестве входных данных и какие элементы создает в качестве выходных. MSBuild пытается найти однозначное соответствие между значениями этих атрибутов. Если однозначное соответствие существует, MSBuild сравнивает метку времени каждого входного элемента с меткой времени соответствующего выходного элемента. Выходные файлы без однозначного соответствия сравниваются со всеми входными файлами. Элемент считается актуальным, если возраст его выходного файла меньше или равен возрасту его входных файлов.  
  
 Если все выходные элементы актуальны, MSBuild пропускает этот целевой объект. Такая *инкрементная сборка* целевого объекта может значительно ускорить сборку. Если актуальны лишь некоторые файлы, MSBuild выполняет целевой объект, пропуская актуальные элементы. В результате все элементы становятся актуальными. Это называется *частичной инкрементной сборкой*.  
  
 Однозначные соответствия обычно обеспечиваются преобразованиями элементов. Дополнительные сведения см. в статье [Преобразования](../msbuild/msbuild-transforms.md).  
  
 Рассмотрим следующий целевой объект.  
  
```  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 Набор файлов, представленный типом элемента `Compile`, копируется в каталог резервных копий. Файлы резервных копий имеют расширение BAK. Если файлы, представленные типом элемента `Compile`, или соответствующие файлы резервных копий не удаляются и не изменяются после выполнения целевого объекта резервной копии, то при последующих сборках этот целевой объект пропускается.  
  
## <a name="output-inference"></a>Определение выходных параметров  
 MSBuild сравнивает атрибуты `Inputs` и `Outputs` целевого объекта, чтобы определить, нужно ли его выполнять. В идеальном случае набор файлов, полученный после завершения инкрементной сборки, должен остаться прежним независимо от того, выполняются ли связанные целевые объекты. Так как свойства и элементы, которые были созданы или изменены задачами, могут повлиять на сборку, система MSBuild должна выводить их значения, даже если затрагивающий их целевой объект пропускается. Это называется *определением выходных параметров*.  
  
 Могут возникнуть три ситуации:  
  
- Целевой объект имеет атрибут `Condition`, который при вычислении дает значение `false`. В этом случае целевой объект не запускается и не влияет на сборку.  
  
- Целевой объект имеет устаревшие выходные параметры и выполняется, чтобы сделать их снова актуальными.  
  
- У целевого объекта нет устаревших выходных параметров, поэтому он пропускается. MSBuild вычисляет целевой объект и вносит изменения в элементы и свойства, как если бы целевой объект выполнялся.  
  
  Для поддержки инкрементной компиляции задачи должны обеспечить, чтобы значение атрибута `TaskParameter` для любого элемента `Output` было равно входному параметру задачи. Вот несколько примеров:  
  
```  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 Создает свойство Easy, которое имеет значение "123" независимо от того, выполняется или пропускается целевой.  
  
```  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 Создает тип элемента Simple, который содержит два элемента ("a.cs" и "b.cs") независимо от того, выполняется или пропускается целевой объект.  
  
 Начиная с версии MSBuild 3.5, определение выходных параметров выполняется автоматически для групп элементов и свойств в целевом объекте. Задачи `CreateItem` в целевом объекте не требуются, и их следует избегать. Кроме того, задачи `CreateProperty` следует использовать только в целевом объекте, чтобы определить, выполнялся ли он.  
  
## <a name="determining-whether-a-target-has-been-run"></a>Определение того, выполнялся ли целевой объект  
 Из-за определения выходных параметров в целевой объект нужно добавить задачу `CreateProperty` для изучения свойств и элементов, чтобы можно было определить, выполнялся ли целевой объект. Добавьте задачу `CreateProperty` в целевой объект и присвойте ей элемент `Output`, у которого `TaskParameter` имеет значение "ValueSetByTask".  
  
```  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 Создает свойство CompileRan и присваивает ему значение `true`, но только в случае выполнения целевого объекта. В случае пропуска целевого объекта свойство CompileRan не создается.  
  
## <a name="see-also"></a>См. также:  
 [Целевые объекты](../msbuild/msbuild-targets.md)
