---
title: 'IDebugProcess2:: Attach | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4664f164675c445510d8976f33577684dbd1d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188097"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Присоединяет диспетчер отладки сеансов (SDM) к процессу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCallback`  
 окне Объект [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , используемый для уведомления о событии отладки.  
  
 `rgguidSpecificEngines`  
 окне Массив идентификаторов GUID модулей отладки, которые будут использоваться для отладки программ, выполняющихся в процессе. Этот параметр может иметь значение null. Дополнительные сведения см. в разделе "Примечания".  
  
 `celtSpecificEngines`  
 окне Количество модулей отладки в `rgguidSpecificEngines` массиве и размер `rghrEngineAttach` массива.  
  
 `rghrEngineAttach`  
 [вход, выход] Массив кодов HRESULT, возвращаемых отладчиками. Размер этого массива указывается в `celtSpecificEngines` параметре. Каждый код обычно имеет значение `S_OK` или `S_ATTACH_DEFERRED` . Последнее означает, что в настоящее время в программе «DE» прикрепляется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны другие возможные значения.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Указанный процесс уже присоединен к отладчику.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Во время процедуры подключения возникло нарушение безопасности.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Рабочий процесс не может быть присоединен к отладчику.|  
  
## <a name="remarks"></a>Remarks  
 Присоединение к процессу прикрепляет SDM ко всем программам, выполняемым в этом процессе, которые могут быть отлажены модулями отладки (DE), указанными в `rgguidSpecificEngines` массиве. Задайте `rgguidSpecificEngines` для параметра значение null или включите `GUID_NULL` в массив, чтобы присоединить его ко всем программам в процессе.  
  
 Все события отладки, происходящие в процессе, отправляются в указанный объект [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) . Этот `IDebugEventCallback2` объект предоставляется, когда SDM вызывает этот метод.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
