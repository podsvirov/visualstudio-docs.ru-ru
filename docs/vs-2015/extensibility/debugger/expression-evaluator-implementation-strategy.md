---
title: Стратегия реализации средства оценки выражений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, implementation strategy
- debug engines, implementation strategies
ms.assetid: 1bccaeb3-8109-4128-ae79-16fd8fbbaaa2
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2ded111c371fc1a42c8f1ee08769f5b06aeda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843117"
---
# <a name="expression-evaluator-implementation-strategy"></a>Стратегия реализации вычислителя выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Один из подходов к быстрому созданию средства оценки выражений (EE) заключается в том, чтобы сначала реализовать минимальный код, необходимый для вывода локальных переменных в окне **локальные** . Полезно понимать, что каждая строка в окне **локальные** отображает имя, тип и значение локальной переменной, а все три представляются объектом [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) . Имя, тип и значение локальной переменной можно получить из `IDebugProperty2` объекта, вызвав его метод [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . Дополнительные сведения о том, как отображать локальные переменные в окне **локальные** , см. в разделе [отображение локальных](../../extensibility/debugger/displaying-locals.md)переменных.  
  
## <a name="discussion"></a>Разговор  
 Возможная последовательность реализации начинается с реализации [идебужекспрессионевалуатор](../../extensibility/debugger/reference/idebugexpressionevaluator.md). Для вывода локальных переменных необходимо реализовать методы [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) и [жетмесодпроперти](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) . Вызов `IDebugExpressionEvaluator::GetMethodProperty` возвращает `IDebugProperty2` объект, представляющий метод:, то есть объект [идебугмесодфиелд](../../extensibility/debugger/reference/idebugmethodfield.md) . Сами методы не отображаются в окне **локальные** .  
  
 Метод [енумчилдрен](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) должен быть реализован далее. Модуль отладки (DE) вызывает этот метод для получения списка локальных переменных и аргументов путем передачи `IDebugProperty2::EnumChildren` `guidFilter` аргумента `guidFilterLocalsPlusArgs` . `IDebugProperty2::EnumChildren` вызывает [енумаргументс](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) и [енумлокалс](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md), объединяя результаты в одно перечисление. Дополнительные сведения см. в разделе [отображение локальных переменных](../../extensibility/debugger/displaying-locals.md) .  
  
## <a name="see-also"></a>См. также:  
 [Реализация средства оценки выражений](../../extensibility/debugger/implementing-an-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)
