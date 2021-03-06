---
title: Элемент Task (MSBuild) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6683aac3c5a4314df6fde3d72dd9085b6608d8a3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202270"
---
# <a name="task-element-msbuild"></a>Элемент Task (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Создает и выполняет экземпляр задачи [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Имя элемента определяется именем создаваемой задачи.  
  
 \<Project>  
 \<Target>  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Task Parameter1="Value1"... ParameterN="ValueN"  
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"  
    Condition="'String A' == 'String B'" >  
    <Output... />  
</Task>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Condition`|Необязательный атрибут. Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Необязательный атрибут. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое задачи последующие задачи в [целевом](../msbuild/target-element-msbuild.md) элементе и сборке продолжают выполняться, и все ошибки из задачи обрабатываются как предупреждения.<br />-   **Еррорандконтинуе**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (по умолчанию). При сбое задачи остальные задачи в элементе `Target` и сборке не выполняются, и считается, что возник сбой всего элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. [в разделе инструкции. игнорирование ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md).|  
|`Parameter`|Требуется, если класс задачи содержит одно или несколько свойств с атрибутом `[Required]`.<br /><br /> Определяемый пользователем параметр задачи, значением которого является значение параметра. В элементе `Task` может существовать любое число параметров, и каждый атрибут соответствует свойству .NET в классе задачи.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Выходные данные](../msbuild/output-element-msbuild.md)|Сохраняет выходные данные задачи в файле проекта. Задача может содержать нуль и более элементов `Output`.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Цель](../msbuild/target-element-msbuild.md)|Элемент контейнера для задач [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="remarks"></a>Remarks  
 Элемент `Task` в файле проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] создает экземпляр задачи, устанавливает для него свойства и выполняет его. Элемент `Output` сохраняет выходные параметры в свойствах или элементах, которые будут использоваться в другом месте в файле проекта.  
  
 Если в родительском элементе `Target` задачи существуют элементы [OnError](../msbuild/onerror-element-msbuild.md), они будут обрабатываться даже в случае сбоя задачи, когда `ContinueOnError` имеет значение `false`. Дополнительные сведения о задачах см. в разделе [Задачи](../msbuild/msbuild-tasks.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода создает экземпляр класса [задачи Csc](../msbuild/csc-task.md), устанавливает шесть свойств и выполняет задачу. После выполнения значение свойства `OutputAssembly` этого объекта помещается в список элементов с именем `FinalAssemblyName`.  
  
```  
<Target Name="Compile" DependsOnTarget="Resources" >  
    <Csc Sources="@(CSFile)"  
          TargetType="library"  
          Resources="@(CompiledResources)"  
          EmitDebugInformation="$(includeDebugInformation)"  
          References="@(Reference)"  
          DebugType="$(debuggingType)" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
