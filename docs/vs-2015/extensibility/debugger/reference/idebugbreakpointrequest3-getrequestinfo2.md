---
title: 'IDebugBreakpointRequest3:: GetRequestInfo2 | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d01d1b5e3aef83d948f058dfbf5dbdbb4c7cb782
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158785"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод получает сведения о запросе точки останова, описывающие этот запрос на точку останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```csharp  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 окне Сочетание флагов из перечисления [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) , определяющих поля, которые должны `pBPRequestInfo` быть заполнены.  
  
 `bBPRequestInfo`  
 заполняет Структура [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) , которую необходимо заполнить.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 В этом запросе больше сведений, чем возвращается методом [жетрекуестинфо](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [жетрекуестинфо](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
