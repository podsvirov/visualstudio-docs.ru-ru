---
title: Архитектура средства оценки выражений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8e0aa8f5cc45e0f6e012ecb3f0a27a22725a259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842777"
---
# <a name="expression-evaluator-architecture"></a>Архитектура вычислителя выражений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Интеграция собственного языка в пакет отладки Visual Studio означает реализацию требуемых интерфейсов оценщика выражений (EE) и вызов интерфейсов CLR и BINDER для общеязыковой среды выполнения. Объекты SP и BINDER вместе с текущим адресом выполнения — это контекст, в котором оцениваются выражения. Информация, которую эти интерфейсы создают и потребляют, представляет ключевые понятия архитектуры EE.  
  
## <a name="overview"></a>Overview  
  
### <a name="parsing-the-expression"></a>Анализ выражения  
 При отладке программы выражения оцениваются по ряду причин, но всегда при остановке отлаживаемой программы в точке останова (точки останова, размещенной пользователем или вызванной исключением). В данный момент это происходит, когда Visual Studio получает кадр стека, представленный интерфейсом [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) , из модуля отладки (de). Затем Visual Studio вызывает [жетекспрессионконтекст](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) для получения интерфейса [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . Этот интерфейс представляет контекст, в котором можно вычислить выражения. [Парсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) — это точка входа для процесса оценки. До этого момента все интерфейсы реализуются методом DE.  
  
 При `IDebugExpressionContext2::ParseText` вызове метод de создает экземпляр ee, связанный с языком исходного файла, в котором произошла точка останова (в этом случае на de также создается экземпляр SH). EE представляется интерфейсом [идебужекспрессионевалуатор](../../extensibility/debugger/reference/idebugexpressionevaluator.md) . Затем метод DE вызывает [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) для преобразования выражения (в текстовой форме) в проанализированное выражение, готовое к оценке. Это проанализированное выражение представлено интерфейсом [идебугпарседекспрессион](../../extensibility/debugger/reference/idebugparsedexpression.md) . Обратите внимание, что в этой точке выражение обычно анализируется и не вычисляется.  
  
 Метод DE создает объект, реализующий интерфейс [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , помещает `IDebugParsedExpression` объект в `IDebugExpression2` объект и возвращает `IDebugExpression2` объект из `IDebugExpressionContext2::ParseText` .  
  
### <a name="evaluating-the-expression"></a>Вычисление выражения  
 Visual Studio вызывает либо [евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) , либо [евалуатеасинк](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) для вычисления проанализированного выражения. Оба эти метода вызывают [евалуатесинк](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) ( `IDebugExpression2::EvaluateSync` вызывает метод немедленно, в то время как `IDebugExpression2::EvaluateAsync` вызывает метод через фоновый поток) для вычисления проанализированного выражения и возврата интерфейса [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , представляющего значение и тип проанализированного выражения. `IDebugParsedExpression::EvaluateSync` использует предоставленную SH, Address и BINDER для преобразования проанализированного выражения в фактическое значение, представленное `IDebugProperty2` интерфейсом.  
  
### <a name="for-example"></a>Например  
 После попадания точки останова в работающую программу пользователь выбирает просмотр переменной в диалоговом окне **Быстрая проверка** . В этом диалоговом окне отображается имя переменной, ее значение и тип. Пользователь обычно может изменить значение.  
  
 При отображении диалогового окна **Быстрая проверка** имя проверяемой переменной отправляется в виде текста в [парсетекст](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Он возвращает объект [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , представляющий проанализированное выражение, в данном случае — переменную. Затем вызывается [евалуатесинк](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) для создания `IDebugProperty2` объекта, представляющего значение и тип переменной, а также ее имя. Эти сведения отображаются.  
  
 Если пользователь изменяет значение переменной, [сетвалуеасстринг](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) вызывается с новым значением, которое изменяет значение переменной в памяти и будет использоваться при возобновлении работы программы.  
  
 Дополнительные сведения об этом процессе отображения значений переменных см. в разделе [отображение локальных переменных](../../extensibility/debugger/displaying-locals.md) . Дополнительные сведения об изменении значения переменной см. в разделе [изменение значения локального объекта](../../extensibility/debugger/changing-the-value-of-a-local.md) .  
  
## <a name="in-this-section"></a>в этом разделе  
 [Контекст вычислений](../../extensibility/debugger/evaluation-context.md)  
 Предоставляет аргументы, которые передаются, когда метод DE вызывает EE.  
  
 [Интерфейсы вычислителя ключевых выражений](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Описывает ключевые интерфейсы, необходимые при записи EE, а также контекст оценки.  
  
## <a name="see-also"></a>См. также:  
 [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Отображение локальных переменных](../../extensibility/debugger/displaying-locals.md)   
 [Изменение значения локальной переменной](../../extensibility/debugger/changing-the-value-of-a-local.md)
