---
title: Иенумдебугфиелдс | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields
helpviewer_keywords:
- IEnumDebugFields interface
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d577ff2f5848f2cb348bcaccf57875507018634b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80716781"
---
# <a name="ienumdebugfields"></a>IEnumDebugFields
Этот интерфейс представляет коллекцию объектов, реализующих интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Синтаксис

```
IEnumDebugFields : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется поставщиком символов для предоставления наборов объектов, реализующих интерфейс [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) . Обратите внимание, что это не стандартное перечисление COM из-за наличия метода [NOCOUNT](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md) .

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Этот интерфейс возвращается [жетмесодфиелдсбинаме](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) и [жетнамеспацесуседатаддресс](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md).

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Этот интерфейс реализует следующие методы.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Извлекает из перечисления следующий набор объектов [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .|
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Пропускает указанное число записей.|
|[Сброс](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Сбрасывает перечисление до первой записи.|
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Извлекает копию текущего перечисления.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Возвращает количество записей в перечислении.|

## <a name="remarks"></a>Remarks

## <a name="requirements"></a>Требования
 Заголовок: sh. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)
- [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)
