---
title: Контракты команд в сборках взаимодействия | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command handling with interop assemblies, command contracts
- interop assemblies, command contracts
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50d48d3a8ff55559cce1c3a40142e31b8eebd85f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195126"
---
# <a name="command-contracts-in-interop-assemblies"></a>Контракты команд в сборках взаимодействия
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Базовый контракт для обработки команд через <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс заключается в том, что среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, чтобы определить, поддерживается ли команда, и, если она поддерживается, для определения ее состояния и текста. Затем среда вызывает <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для выполнения команды.  
  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>Метод обрабатывается одинаково для всех команд. Дальнейшая связь, если это необходимо (например, с раскрывающимися списками), управляется путем вызова <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метода с соответствующими параметрами. Интерпретация этих параметров зависит от указанной команды.  
  
 Если целевой объект команды возвращает значения в параметре OUTPUT, вызывающий объект всегда отвечает за освобождение всех выделенных ресурсов. Поскольку этот параметр является вариантом, очистка варианта освобождает ресурсы.  
  
 В случаях, когда команды должны работать в окне иерархии, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> необходимо использовать интерфейс. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>Интерфейс имеет похожий контракт с аналогичными методами: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .  
  
## <a name="see-also"></a>См. также:  
 [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакетах VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Реализация](../../extensibility/internals/command-implementation.md)
