---
title: Справочные сведения о схеме файлов проектов MSBuild | Документы Майкрософт
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
- MSBuild, file schema
ms.assetid: d9a68146-1f43-4621-ac78-2c8c3f400936
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 847fa53acad63cec151222521ed8f85090c52080
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158856"
---
# <a name="msbuild-project-file-schema-reference"></a>Справочные сведения о схеме файлов проектов MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представлена таблица, содержащая все элементы XML-схемы [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], доступные атрибуты элементов и дочерние элементы.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] использует файлы проекта для указания механизму сборки, что собирать и как делать это. Файлы проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] представляют собой XML-файлы, которые подчиняются XML-схеме [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. В данном разделе описывается содержимое файла определений XML-схемы (XSD) для [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="msbuild-xml-schema-elements"></a>Элементы XML-схемы MSBuild  
 В следующей таблице перечислены все элементы XML-схемы [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], а также их дочерние элементы и атрибуты.  
  
|Элемент|Дочерние элементы|Атрибуты|  
|-------------|--------------------|----------------|  
|[Элемент Choose (MSBuild)](../msbuild/choose-element-msbuild.md)|Otherwise<br /><br /> When|--|  
|[Элемент Import (MSBuild)](../msbuild/import-element-msbuild.md)|--|Условие<br /><br /> Project|  
|[ImportGroup, элемент](../msbuild/importgroup-element.md)|Импорт|Условие|  
|[Элемент Item (MSBuild)](../msbuild/item-element-msbuild.md)|*ItemMetaData*|Условие<br /><br /> Исключить<br /><br /> Включение<br /><br /> Удалить|  
|[Элемент ItemDefinitionGroup (MSBuild)](../msbuild/itemdefinitiongroup-element-msbuild.md)|*Item*|Условие|  
|[Элемент ItemGroup (MSBuild)](../msbuild/itemgroup-element-msbuild.md)|*Item*|Условие|  
|[Элемент ItemMetadata (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)|*Item*|Условие|  
|[Элемент OnError (MSBuild)](../msbuild/onerror-element-msbuild.md)|--|Условие<br /><br /> ExecuteTargets|  
|[Элемент Otherwise (MSBuild)](../msbuild/otherwise-element-msbuild.md)|Нажмите кнопку<br /><br /> ItemGroup<br /><br /> PropertyGroup|--|  
|[Элемент Output (MSBuild)](../msbuild/output-element-msbuild.md)|--|Условие<br /><br /> Название товара<br /><br /> PropertyName<br /><br /> TaskParameter|  
|[Элемент Parameter](../msbuild/parameter-element.md)|--|Выходные данные<br /><br /> ParameterType<br /><br /> Обязательно|  
|[ParameterGroup, элемент](../msbuild/parametergroup-element.md)|*Параметр*|--|  
|[Элемент Project (MSBuild)](../msbuild/project-element-msbuild.md)|Нажмите кнопку<br /><br /> Импорт<br /><br /> ItemGroup<br /><br /> ProjectExtensions<br /><br /> PropertyGroup<br /><br /> Назначение<br /><br /> UsingTask|DefaultTargets<br /><br /> InitialTargets<br /><br /> ToolsVersion<br /><br /> TreatAsLocalProperty<br /><br /> xmlns|  
|[Элемент ProjectExtensions (MSBuild)](../msbuild/projectextensions-element-msbuild.md)|--|--|  
|[Элемент Property (MSBuild)](../msbuild/property-element-msbuild.md)|--|Условие|  
|[Элемент PropertyGroup (MSBuild)](../msbuild/propertygroup-element-msbuild.md)|*Свойство*|Условие|  
|[Элемент Target (MSBuild)](../msbuild/target-element-msbuild.md)|OnError<br /><br /> *Задача*|AfterTargets<br /><br /> BeforeTargets<br /><br /> Условие<br /><br /> DependsOnTargets<br /><br /> Входные данные<br /><br /> KeepDuplicateOutputs<br /><br /> Имя<br /><br /> Выходные данные<br /><br /> Возвращаемое значение|  
|[Элемент Task (MSBuild)](../msbuild/task-element-msbuild.md)|Выходные данные|Условие<br /><br /> ContinueOnError<br /><br /> *Параметр*|  
|[Элемент TaskBody (MSBuild)](../msbuild/taskbody-element-msbuild.md)|*Data*|Evaluate|  
|[Элемент UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md)|ParameterGroup<br /><br /> TaskBody|AssemblyFile<br /><br /> AssemblyName<br /><br /> Условие<br /><br /> TaskFactory<br /><br /> TaskName|  
|[Элемент When (MSBuild)](../msbuild/when-element-msbuild.md)|Нажмите кнопку<br /><br /> ItemGroup<br /><br /> PropertyGroup|Условие|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)   
 [Состоянии](../msbuild/msbuild-conditions.md)   
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)  
 [MSBuild](msbuild.md)
