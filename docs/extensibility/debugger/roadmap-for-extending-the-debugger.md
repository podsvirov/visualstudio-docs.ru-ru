---
title: Стратегия расширения отладчика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d97a7edd62540d12a0a60d15b3179ca0a623c26
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011831"
---
# <a name="roadmap-for-extending-the-debugger"></a>Стратегия расширения отладчика
Эта документация содержит руководство и справочные сведения по расширению [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] отладчика с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Документация по отладке включает примеры, исчерпывающие ссылки и несколько репрезентативных сценариев, демонстрирующих типичные способы настройки отладчика.

 Компилятор и его выходные данные определяют, что необходимо для настройки отладки в вашем продукте. Если ваш компилятор:

- Предназначен для встроенной операционной системы Windows и записывает *. PDB* -файл позволяет отлаживать программы с помощью машинного модуля отладки кода (de), интегрированного в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Нет необходимости реализовывать средство оценки «DE» или «вычислителя выражений». Средство оценки выражений написано для синтаксиса языка программирования C++.

- Создает выходные данные промежуточного языка MSIL, можно выполнять отладку программ с помощью модуля отладки управляемого кода DE, который также интегрирован в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Поэтому требуется только реализовать средство оценки выражений. Для вас предоставляется пример средства оценки выражений. Дополнительные сведения см. в следующих разделах:

   [Вычисление выражений](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Вычисление выражений](../../extensibility/debugger/evaluating-expressions.md)

   [Контекст вычисления выражения](../../extensibility/debugger/expression-evaluation-context.md)

   [Вычисление выражений в режиме приостановки выполнения](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Написание средства оценки выражений среды CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Предназначен для собственной операционной системы или какой-либо другой среды выполнения, необходимо написать собственный DE. Предоставляется учебник, в котором создается простой протокол DE-using ATL COM. Дополнительные сведения см. в следующих разделах:

   [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Учебник. Создание модуля отладки с помощью ATL COM](/previous-versions/bb147024(v=vs.90))

   [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>См. также раздел
- [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)