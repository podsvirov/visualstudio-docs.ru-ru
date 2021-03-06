---
title: Приоритет проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b012136c30f72cfdddadfc1a370ed76f567afffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429916"
---
# <a name="project-priority"></a>Приоритет проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Элемент проекта обычно является членом только одного проекта в решении. Таким образом, интегрированная среда разработки может легко определить, какой проект используется для открытия элемента. Однако если элемент является членом более чем одного проекта, интегрированная среда разработки использует схему приоритета для определения лучшего проекта для открытия элемента.  
  
 В следующем списке показана схема приоритета проекта.  
  
- Интегрированная среда разработки вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> метод для каждого проекта в решении, чтобы определить, является ли документ членом этого проекта.  
  
- Если документ является членом проекта, проект отвечает с приоритетом, который назначается проектом в соответствии с его обработкой этого документа. Например, языковой проект реагирует с высоким приоритетом для исходных файлов языка, но отвечает с более низким приоритетом для неопознанного типа файла, который не используется в процессе сборки.  
  
- Проекты, предоставляющие пользовательские редакторы или конструкторы для конкретного проекта, также получают высокий приоритет.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>Перечисление предоставляет значения приоритета документа.  
  
- Проект, указывающий наивысший приоритет, получает контекст для открытия документа. Если два проекта возвращают одинаковые значения приоритета, предпочтительным является активный проект. Если ни один из проектов в решении не отвечает, что он может открыть документ, интегрированная среда разработки помещает документ в проект "Прочие файлы". Дополнительные сведения см. в разделе [проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>См. также:  
 [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)   
 [Руководство. открытие редакторов для открытых документов](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)
