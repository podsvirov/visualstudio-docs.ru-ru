---
title: Общеизвестные метаданные элементов MSBuild | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bb2e53102221194dc829df162c44bbf04378b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154088"
---
# <a name="msbuild-well-known-item-metadata"></a>Общеизвестные метаданные элементов MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В следующей таблице описаны метаданные, которые назначаются каждому элементу при его создании. В каждом примере для включения в проект файла `C:\MyProject\Source\Program.cs` используется следующее объявление элемента.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Метаданные элементов|Описание|  
|-------------------|-----------------|  
|%(FullPath)|Содержит полный путь к элементу. Пример:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Содержит корневой каталог элемента. Пример:<br /><br /> `C:\`|  
|%(Filename)|Содержит имя файла элемента без расширения. Пример:<br /><br /> `Program`|  
|%(Extension)|Содержит расширение имени файла элемента. Пример:<br /><br /> `.cs`|  
|%(RelativeDir)|Содержит путь, указанный в атрибуте `Include`, до последней обратной косой черты (\\). Пример:<br /><br /> `Source\`|  
|%(Directory)|Содержит каталог элемента без корневого каталога. Пример:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Если атрибут `Include` содержит подстановочный знак \*\*, эти метаданные определяют путь, который используется вместо подстановочного знака. Дополнительные сведения об подстановочных знаках см. в разделе [как выбрать файлы для сборки](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Если папка *к:\мисолутион\мипрожект\саурце \\ * содержит файл Program.cs, а файл проекта содержит этот элемент:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> то параметр `%(MyItem.RecursiveDir)` принимает значение *MySolution\MyProject\Source\\* .|  
|%(Identity)|Элемент, заданный в атрибуте `Include`. Пример:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Содержит метку времени, соответствующую времени последнего изменения элемента. Пример:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Содержит метку времени, соответствующую времени создания элемента. Пример:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Содержит метку времени, соответствующую времени последнего доступа к элементу.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>См. также:  
 [Файлов](../msbuild/msbuild-items.md)   
 [Пакетной обработки](../msbuild/msbuild-batching.md)   
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)
