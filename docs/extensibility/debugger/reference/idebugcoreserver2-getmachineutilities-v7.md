---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80733153"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Этот метод получает служебные программы компьютера для сервера.

> [!NOTE]
> Этот метод является устаревшим: не используйте ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] всегда возвращает `E_NOTIMPL` , если вызывается этот метод). Он хранится по историческим причинам.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Параметры
`ppUtil`\
заполняет Возвращает `IDebugMDMUtil2_V7` интерфейс, представляющий сведения о служебных программах компьютера.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL` , указывающее, что метод не реализован.

## <a name="remarks"></a>Remarks
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] всегда возвращает `E_NOTIMPL` , если вызывается этот метод.

## <a name="see-also"></a>См. также раздел
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
