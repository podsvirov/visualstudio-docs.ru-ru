---
title: IDebugBreakpointRequest2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 263b947fff45eafd2d2e5afc029572b69ea24b82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158782"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет сведения, необходимые для создания и привязки любого типа точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Диспетчер отладки сеансов (SDM) обычно реализует этот интерфейс.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Модуль отладки (DE) получает этот интерфейс через вызов [креатепендингбреакпоинт](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) для создания ожидающей точки останова. Вызов [жетбреакпоинтрекуест](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) может получить этот интерфейс из de.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBreakpointRequest2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Возвращает тип расположения точки останова для этого запроса точки останова.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Получает сведения о запросе точки останова, описывающие этот запрос на точку останова.|  
  
## <a name="remarks"></a>Remarks  
 После загрузки отлаживаемой программы вызов [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) привязывает отложенную точку останова к запрошенному расположению в программе.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [креатепендингбреакпоинт](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [жетбреакпоинтрекуест](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Выполняется](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
