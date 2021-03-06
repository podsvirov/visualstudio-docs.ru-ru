---
title: Интерфейсы оценки выражений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8a710019390120768b665cf3b27174831a67f0cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842544"
---
# <a name="expression-evaluation-interfaces"></a>Интерфейсы вычисления выражений
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Ниже приведены интерфейсы вычисления выражений для [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] пакета SDK для отладки.  
  
## <a name="discussion"></a>Разговор  
 Эти интерфейсы используются для вычисления выражений в стеке вызовов в режиме приостановки выполнения. Они реализуются только для вычислителей выражений среды CLR (EE).  
  
 Каждый интерфейс в таблице показывает компонент, который может реализовать его из следующего списка:  
  
- Модуль отладки (DE)  
  
- Средство оценки выражений (EE)  
  
- Visual Studio (VS)  
  
|Интерфейс|Реализовано|Description|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|Представляет числовой псевдоним для переменной.|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|Представляет числовой псевдоним для переменной и позволяет средству оценки выражений (EE) получить домен приложения для псевдонима.|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|Представляет объект массива.|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|Представляет объект управляемого массива и позволяет средству оценки выражений (EE) определить базовый индекс (нижние границы) для массива.|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|Представляет связыватель, связывающий отладочные символы с фактическими адресами в памяти.|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|То же, что и интерфейс [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md) , но предоставляет доступ к типам, псевдонимам и пользовательским визуализаторам.|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|Представляет средство оценки выражений.|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|Представляет улучшенную версию средства оценки выражений (EE).|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|Представляет средство оценки выражений (EE) с расширенным деревом синтаксического анализа.|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|Представляет функцию.|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|Представляет функцию и расширяет интерфейс [идебугфунктионобжект](../../../extensibility/debugger/reference/idebugfunctionobject.md) .|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|Позволяет Вычислителю выражений (EE) отображать сообщение в окне вывода отладчика.|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|Представляет объект управляемого кода.|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|Базовый интерфейс, представляющий любой символ, привязанный к адресу памяти.|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|То же, что и интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , но предоставляет доступ к дополнительным сведениям.|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|Представляет проанализированное выражение, готовое для оценки.|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|Представляет указатель.|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|Представляет указатель в дереве синтаксического анализа и расширяет интерфейс **идебугпоинтеробжект** .|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|Предоставляет возможность изменять значение типа с помощью визуализатора типов.|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|Предоставляет доступ к пользовательским средствам просмотра и визуализаторам типов.|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|Предоставляет возможность создания объекта [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md) .|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|Представляет коллекцию объектов [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) .|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [Написание вычислителя выражений CLR](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
