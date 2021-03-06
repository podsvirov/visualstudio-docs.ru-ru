---
title: Идебугпортпиккер | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 554ac24d7148f0d5de07779f35376b28b7ff7b07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724845"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
Представляет настраиваемый пользовательский интерфейс для выбора порта.

## <a name="syntax"></a>Синтаксис

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиками портов. Поставщик порта определяет его средство выбора портов, предоставляя его в качестве идентификатора CLSID и указывая `metricPortPickerCLSID` метрику на предоставленном CLSID.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugPortPicker` .

|Метод|Описание|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Отображает указанное диалоговое окно, позволяющее пользователю выбрать порт.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Задает поставщик служб.|

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
