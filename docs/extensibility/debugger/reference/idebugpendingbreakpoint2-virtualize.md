---
title: 'IDebugPendingBreakpoint2:: виртуализировать | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Virtualize
helpviewer_keywords:
- Virtualize method
- IDebugPendingBreakpoint2::Virtualize method
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ad5aac997cf694a7cf8fa887ae63fbef54ca07f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725659"
---
# <a name="idebugpendingbreakpoint2virtualize"></a>IDebugPendingBreakpoint2::Virtualize
Переключает виртуализированное состояние этой ожидающей точки останова. Если ожидающая точка останова виртуализирована, модуль отладки попытается привязать его каждый раз, когда в программу будет загружен новый код.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Virtualize(
    BOOL fVirtualize
);
```

```cpp
int Virtualize(
    int fVirtualize
);
```

## <a name="parameters"></a>Параметры
`fVirtualize`\
окне Задайте для параметра значение ненулевой ( `TRUE` ), чтобы выполнить виртуализацию ожидающей точки останова, или нуль ( `FALSE` ), чтобы отключить виртуализацию.

## <a name="return-value"></a>Возвращаемое значение
Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. Возвращает значение `E_BP_DELETED` , если точка останова была удалена.

## <a name="remarks"></a>Remarks
Виртуальная точка останова привязывается каждый раз при загрузке кода.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CPendingBreakpoint` объекта, предоставляющего интерфейс [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

```cpp
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)
{
    HRESULT hr;

    // Verify that the pending breakpoint has not been deleted. If deleted,
    // then return hr = E_BP_DELETED.
    if (m_state.state != PBPS_DELETED)
    {
        if (fVirtualize)
        {
            // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS
            // structure.
            SetFlag(m_state.flags, PBPSF_VIRTUALIZED);
        }
        else
        {
            // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS
            // structure.
            ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);
        }
        hr = S_OK;
    }
    else
    {
        hr = E_BP_DELETED;
    }

    return hr;
}
```

## <a name="see-also"></a>См. также раздел
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
