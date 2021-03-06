---
title: 'IDebugPortEvents2:: Event | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEvents2::Event
helpviewer_keywords:
- IDebugPortEvents2::Event
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28738b94ecc711833a4e16204b20f64d88687fe5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188556"
---
# <a name="idebugportevents2event"></a>IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод отправляет события, которые обозначают создание и уничтожение процессов и программ на порте.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```csharp  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pMachine`  
 окне Объект [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , представляющий сервер отладки (по одному для каждого экземпляра [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ), в котором произошло событие.  
  
 `pPort`  
 окне Объект [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) , представляющий порт, в котором произошло событие.  
  
 `pProcess`  
 окне Объект [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс, в котором произошло событие.  
  
 `pProgram`  
 окне Объект [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющий программу, в которой произошло событие.  
  
 `pEvent`  
 окне Объект [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , определяющий событие. Возможны следующие события.  
  
- [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
- [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
- [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
  `riidEvent`  
  окне Идентификатор GUID события. Так как событие приводится к [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) перед вызовом этого метода, этот идентификатор упрощает определение того, какое событие отправляется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
