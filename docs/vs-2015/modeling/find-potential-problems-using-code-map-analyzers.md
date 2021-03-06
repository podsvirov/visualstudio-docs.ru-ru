---
title: Поиск потенциальных проблем с помощью анализаторов карт кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc5d185640c9623a2213aaf7ad50fa68a088b15c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669619"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Поиск потенциальных проблем с помощью анализаторов карт кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Запустите анализаторы для карт кода, чтобы выявить код, который может быть слишком сложным или может требовать улучшений. Например, можно использовать следующие анализаторы:

|**Чтобы найти код, который**|**Изучите эти области в следующих целях**|
|-------------------------------|--------------------------------------------|
|Содержит циклы или циклические зависимости|Определите, можете ли вы упростить их, и рассмотрите возможность прерывания этих циклов.|
|Содержит слишком много зависимостей|Выясните, не выполняют ли они слишком много функций, или определите влияние изменения этих областей. Правильно сформированная карта кода имеет минимальное количество зависимостей. Чтобы сделать код проще для поддержки, изменения, проверки и повторного использования, рассмотрите возможность рефакторинга этих областей, чтобы они были определены более четко, или возможность слияния кода, выполняющего аналогичные функции.|
|Не содержит зависимостей|Определите, необходимы ли они или этот код можно удалить.|

## <a name="analyze-code-maps"></a>Анализ карт кода

1. На панели инструментов карты выберите **Макет**, **Анализаторы**, а затем анализатор, который вы хотите запустить:

   |**Analyzer**|**Для выявления следующих узлов**|
   |------------------|--------------------------------|
   |**Анализатор циклических ссылок**|Узлы, которые содержат циклические зависимости друг от друга. **Примечание.**  Циклические зависимости, которые находятся в группе **универсальных шаблонов** , не отображаются на карте при развертывании группы.|
   |**Анализатор "Найти концентраторы"**|Узлы, входящие в 25 % узлов, имеющих больше всего соединений.<br /><br /> **Скрытие всех узлов на карте**<br /><br /> — Откройте контекстное меню для схемы, выберите **Дополнительно**, **выберите**, **Скрыть невыбранные**.<br />     Невыбранные узлы карты скрываются, и анализатор определяет новые узлы как концентраторы.|
   |**Анализатор узлов, на которые нет ссылок**|Узлы, на которые не ссылаются другие узлы. **Внимание!**  Прежде чем предположить, что код не используется, проверьте каждый из этих вариантов. Некоторые зависимости, такие как зависимости XAML и зависимости времени выполнения, нельзя найти в коде статически.|

   Анализаторы карт кода продолжают работу после их применения. Если изменить карту, все примененные анализаторы автоматически обрабатывают обновленную карту повторно. Чтобы остановить работу анализатора, на панели инструментов карты выберите **Макет**, **Анализаторы**. Отключите выбранный анализатор.

> [!TIP]
> В случае с очень большой картой запуск анализатора может привести к возникновению исключения "Недостаточно памяти". В этом случае измените карту, чтобы сузить ее область действия, или создайте карту меньшего размера, а затем запустите анализатор.

## <a name="see-also"></a>См. также:
 [Сопоставление зависимостей в решениях](../modeling/map-dependencies-across-your-solutions.md) [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md) [в стеке вызовов во время отладки](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
