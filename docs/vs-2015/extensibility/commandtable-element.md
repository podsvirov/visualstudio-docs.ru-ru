---
title: Элемент Коммандтабле | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bb2b874f7bbe94e383e9e7fba755dcc373a93150
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "77477048"
---
# <a name="commandtable-element"></a>Элемент CommandTable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Коммандтабле — это корневой элемент vsct-файла. Это файл, который определяет фактический макет и тип команд, которые пакет VSPackage предоставляет интегрированной среде разработки. Команды могут включать пункты меню, меню, панели инструментов и поля со списком. Дополнительные сведения см. в разделе [Visual Studio Command Table (.Vsct) Files](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
| Атрибут |                                                                                                                   Описание                                                                                                                   |
|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   xmlns   |                                   Обязательный. Пространства имен XML:<br /><br /> `xmlns="<http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable>"`<br /><br /> `xmlns:xs="<http://www.w3.org/2001/XMLSchema>"`                                   |
| язык  | Необязательный элемент. Атрибут Language можно использовать для указания языка по умолчанию для всех \<Strings> элементов в командной таблице.  Если язык не указан, будет использоваться язык текущего процесса:<br /><br /> Language = "en-US" |
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Extern](../extensibility/extern-element.md)|Необязательный элемент. Содержит директивы препроцессора для компилятора.|  
|[Включить элемент](../extensibility/include-element.md)|Необязательный элемент. Содержит пути к любым файлам, которые необходимо включить в компиляцию.|  
|[Элемент Define](../extensibility/define-element.md)|Необязательный элемент. Определяет символ с учетом его имени и значения.|  
|[Commands, элемент](../extensibility/commands-element.md)|Необязательный элемент. Родительский элемент, определяющий все команды для VSPackage, которые содержат все остальные элементы.|  
|[Элемент CommandPlacements](../extensibility/commandplacements-element.md)|Необязательный элемент. Определяет, где на панели команд должны размещаться команды.|  
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Необязательный элемент. Определяет статическую видимость команд и панелей инструментов.|  
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Необязательный элемент. Задает сочетания клавиш, если они есть, для команд.|  
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Необязательный элемент. Позволяет пакету VSPackage при необходимости реализовать собственную версию функциональности, изначально поддерживаемую другими пакетами VSPackage.|  
|[Элемент Symbols](https://msdn.microsoft.com/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Необязательный элемент. Содержит любые символьные данные — идентификаторы GUID, идентификаторы и т. д. для компилятора.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|None||  
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
