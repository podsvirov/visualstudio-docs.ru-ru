---
title: Идебугбиндер | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder
helpviewer_keywords:
- IDebugBinder interface
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc00c50e3c340ab0685ab1010c6e924e77a18a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842408"
---
# <a name="idebugbinder"></a>IDebugBinder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс Привязывает поле символа, обычно возвращаемое поставщиком символов, к контексту памяти или объекту, который содержит текущее значение символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugBinder : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс поддерживает вычисление выражений и должен быть реализован модулем отладки (DE).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Этот интерфейс используется в процессе оценки выражений и обычно используется в реализации [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) и [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugBinder` .  
  
|Метод|Description|  
|------------|-----------------|  
|[Выполняется](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Возвращает контекст памяти или объект, который содержит текущее значение символа.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Определяет тип времени выполнения объекта.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Преобразует расположение объекта или адрес памяти в контекст памяти.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Возвращает объект [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) , используемый для создания параметров функции.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Возвращает точный тип для переменной.|  
  
## <a name="remarks"></a>Remarks  
 Этот интерфейс возвращает объекты, используемые средством оценки выражений в деревьях синтаксического анализа. Средство оценки выражений анализирует выражение с помощью поставщика символов для преобразования символов в выражении в экземпляры [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md), которые описывают каждый символ в терминах его типа и расположения в исходном коде. Метод [BIND](../../../extensibility/debugger/reference/idebugbinder-bind.md) преобразует `IDebugField` объекты в объекты [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , которые соединяют или привязывают тип символа к фактическому значению в памяти. `IDebugObject`Затем эти объекты сохраняются в дереве синтаксического анализа для последующей оценки.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы оценки выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [евалуатесинк](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [евалуатеасинк](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
