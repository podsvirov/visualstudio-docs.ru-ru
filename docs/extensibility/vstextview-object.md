---
title: Объект Встекствиев | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06e1ba7c10912f23fedc09892e03e2105ff2bab4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583610"
---
# <a name="vstextview-object"></a>Объект Встекствиев

Текстовое представление — это окно, которое позволяет пользователям просматривать и изменять текст в Юникоде для текстового буфера. По сути, представление — это то, что большинство пользователей ссылается на редактор. Так как представление отделяется от буфера различными текстовыми слоями (перенос по словам, структурирование текста и т. д.), представление не обязательно должно быть точным представлением текста в буфере. Дополнительные сведения о представлении текста см. в разделе [доступ к представлению сетекст с помощью API прежних версий](../vs-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api.md?view=vs-2015&preserve-view=true).

В следующей таблице показаны интерфейсы в <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> объекте.

|Интерфейс|Описание|
|---------------|-----------------|
|[идропсаурце](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Стандартный OLE-интерфейс.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Позволяет создавать составные действия (то есть действия, сгруппированные в одну единицу отмены или возврата).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Предоставляет базовые методы для управления представлением и доступа к ним. `IVsTextView` не является потокобезопасным.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Создает и управляет областью окна.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Взаимодействует с текстовыми слоями.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Выполняет операции с представлением из другого потока.|

## <a name="see-also"></a>См. также

- [Изменение фигур](https://www.microsoft.com/download/details.aspx?id=55984)
- [Объект Встекстбуффер](../extensibility/vstextbuffer-object.md)