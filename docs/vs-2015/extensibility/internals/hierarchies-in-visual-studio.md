---
title: Иерархии
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22943d3049ff0e24d00c7c29750e7dcd0efaf846
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158360"
---
# <a name="hierarchies-in-visual-studio"></a>Иерархии в Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среде разработки (IDE) проект отображается как *Иерархия*. В интегрированной среде разработки иерархия — это дерево узлов, в котором каждый узел имеет набор связанных свойств. *Иерархия проектов* — это контейнер, который содержит элементы проекта, связи элементов и связанные свойства и команды элементов.

 В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среде иерархии проектов можно управлять с помощью интерфейса иерархии <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Интерфейс перенаправляет команды, которые вызываются из элементов проекта, в соответствующее окно иерархии вместо стандартного обработчика команд.

## <a name="project-hierarchies"></a>Иерархии проектов
 Каждая иерархия проектов содержит элементы, которые можно просматривать и изменять. Эти элементы зависят от типа проекта. Например, проект базы данных может содержать хранимые процедуры, представления баз данных и таблицы базы данных. С другой стороны, проект на языке программирования, скорее всего, будет включать исходные файлы и файлы ресурсов для точечных рисунков и диалоговых окон. Иерархии могут быть вложенными, что обеспечивает дополнительную гибкость при создании иерархии проектов.

 При создании нового типа проекта тип проекта управляет полным набором элементов, которые могут быть изменены в нем. Однако проекты могут содержать элементы, для которых они не поддерживают редактирование. Например, Visual C++ проекты могут содержать HTML-файлы, хотя Visual C++ не предоставляет настроенный редактор для типа файлов HTML.

 Иерархии управляют сохраняемостью элементов, которые они содержат. Реализация иерархии должна управлять любыми специальными свойствами, влияющими на сохраняемость элементов в иерархии. Например, если элементы представляют объекты в репозитории вместо файлов, реализация иерархии должна управлять сохранением этих объектов. Сама интегрированная среда разработки направляет иерархию для сохранения элементов в соответствии с введенными пользователем данными, но интегрированная среда разработки не контролирует действия, необходимые для сохранения этих элементов. Вместо этого проект находится в элементе управления.

 Когда пользователь открывает элемент в редакторе, иерархия, управляющая этим элементом, выбирается и становится активной иерархией. Выбранная иерархия определяет набор команд, доступных для работы с элементом. Отслеживание фокуса пользователя таким образом позволяет иерархии отражать текущий контекст пользователя.

## <a name="see-also"></a>См. также:
 Выбор [типа проекта](../../extensibility/internals/project-types.md) [и валюты в](../../extensibility/internals/selection-and-currency-in-the-ide.md) [примерах IDE VSSDK](../../misc/vssdk-samples.md)
