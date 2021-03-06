---
title: Обработка ошибок и возвращаемые значения | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74e61e60384b3e98bf26eb8208696ecb9223efa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696333"
---
# <a name="error-handling-and-return-values"></a>Обработка ошибок и возвращаемые значения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Пакеты VSPackage и COM используют одну и ту же архитектуру для ошибок. `SetErrorInfo`Функции и `GetErrorInfo` являются частью прикладного программного интерфейса (API) Win32. Любой пакет VSPackage в интегрированной среде разработки (IDE) может вызывать эти глобальные API-интерфейсы Win32 для записи подробных сведений об ошибках при получении уведомления об ошибке. [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Предоставляет сборки взаимодействия для управления сведениями об ошибках.  
  
## <a name="interop-methods"></a>Методы взаимодействия  
 Для удобства интегрированная среда разработки предоставляет метод, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> для использования вместо вызова API-интерфейсов Win32. В управляемом коде используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . При возникновении ошибки `HRESULT` на уровне, на котором должно отображаться сообщение об ошибке (часто это объект, реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> обработчик команд), в интегрированной среде разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> для отображения соответствующего окна сообщения используется другой метод. В управляемом коде используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> метод.  
  
 Как средство реализации VSPackage, объекты COM обычно реализуют `ISupportErrorInfo` . `ISupportErrorInfo`Интерфейс гарантирует, что подробные сведения об ошибках можно будет перемещать по цепочке вызовов по вертикали. Объекты, которые могут использоваться в процессах или в потоках, должны поддерживать `ISupportErrorInfo` , чтобы обеспечить правильную упаковку данных об ошибках обратно в вызывающий объект.  
  
 Все объекты, связанные с VSPackage и участвующие в расширении интегрированной среды разработки, включая фабрики, редакторы, иерархии и предлагаемые службы, должны поддерживать подробные сведения об ошибках. Хотя интегрированная среда разработки не требует реализации этих объектов VSPackage `ISupportErrorInfo` , всегда рекомендуется.  
  
 Интегрированная среда разработки отвечает за создание отчетов об ошибках и отображение их пользователю [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] при каждом `HRESULT` распространении в интегрированную среду разработки. Интегрированная среда разработки также является механизмом для создания `ErrorInfo` объектов.  
  
## <a name="general-guidelines"></a>Общие рекомендации  
 Можно использовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> методы и для установки и сообщения об ошибках, которые являются внутренними для реализации VSPackage. Однако в качестве общего правила следуйте приведенным ниже рекомендациям по обработке сообщений об ошибках в VSPackage.  
  
- Реализуйте `ISupportErrorInfo` в COM-объектах VSPackage.  
  
- Создайте механизм создания отчетов об ошибках, который вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод в объектах, реализующих <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
- Позвольте интегрированной среде разработки отображать ошибки пользователям с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> метода.  
  
## <a name="error-information-in-the-ide"></a>Сведения об ошибке в интегрированной среде разработки  
 Следующие правила указывают, как выполнять обработку сведений об ошибках в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной среде разработки:  
  
- В качестве защитной стратегии, гарантирующей, что устаревшие сведения об ошибках не передаются пользователям, функции, вызывающие <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> метод, должны сначала вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод. `null`Перед вызовом любого, который может задать новые сведения об ошибке, передайте в него четкие кэшированные сообщения об ошибках.  
  
- Функции, которые не сообщают сообщения об ошибках напрямую, могут вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод только в том случае, если они возвращают ошибку `HRESULT` . Допускается очистка `ErrorInfo` записи в функции или при возврате <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Единственным исключением из этого правила является то, что вызов возвращает ошибку `HRESULT` , из которой принимающая сторона может явно восстановить или спокойно проигнорировать.  
  
- Любая сторона, которая явно игнорирует ошибку, `HRESULT` должна вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод с <xref:Microsoft.VisualStudio.VSConstants.S_OK> . В противном случае `ErrorInfo` объект может быть случайно использован, когда другая сторона создает ошибку, не предоставляя собственной `ErrorInfo` .  
  
- Всем методам, которые поступили к ошибке `HRESULT` , рекомендуется вызывать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод для предоставления подробных сведений об ошибках. Если возвращаемое значение `HRESULT` является особой `FACILITY_ITF` ошибкой, метод необходим для предоставления соответствующего `ErrorInfo` объекта. Если возвращенная ошибка является стандартной системной ошибкой (например,,, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> , <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> и т. д.), допустимо возвращать код ошибки без явного вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метода. В качестве стратегии защитного кода при возникновении ошибки `HRESULT` (включая системные ошибки) всегда вызывайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> метод с `ErrorInfo` описанием ошибки более подробно или `null` .  
  
- Все функции, которые возвращают ошибку, вызванную другим вызовом, должны передавать сведения, полученные от неудачного вызова, в `HRESULT` без изменения `ErrorInfo` объекта.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [Сетерроринфо (Автоматизация компонентов)](https://msdn.microsoft.com/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [жетерроринфо](https://msdn.microsoft.com/03317526-8c4f-4173-bc10-110c8112676a)   
 [Интерфейс ISupportErrorInfo](https://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32)
