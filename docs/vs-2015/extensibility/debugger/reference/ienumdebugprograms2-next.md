---
title: 'IEnumDebugPrograms2:: Next | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 356f1086c4490c45672c5f71e761bdfc6cbe762d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199588"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает следующий набор из перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next(  
   ULONG            celt,  
   IDebugProgram2** rgelt,  
   ULONG*           pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint             celt,  
   IDebugProgram2[] rgelt,  
   ref uint         pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество получаемых элементов. Также указывает максимальный размер `rgelt` массива.  
  
 `rgelt`  
 [вход, выход] Массив элементов [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , которые должны быть заполнены.  
  
 `pceltFetched`  
 заполняет Возвращает количество элементов, фактически возвращаемых в `rgelt` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если может быть возвращено меньше запрошенного числа элементов; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
