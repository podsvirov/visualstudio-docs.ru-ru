---
title: Одновременное использование нескольких профилировщиков | Документация Майкрософт
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, multiple tools
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f72757d46496c3990c0a0d4205753d185078eac7
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332036"
---
# <a name="using-multiple-profiler-tools-simultaneously"></a>Одновременное использование нескольких профилировщиков

Профилировщик производительности разрабатывался таким образом, чтобы в одном сеансе можно было использовать несколько инструментов для лучшего понимания проблем с производительностью. Большинство инструментов в Профилировщике производительности, такие как [Загрузка ЦП](../profiling/cpu-usage.md), [.NET Async](../profiling/analyze-async.md) и [База данных](../profiling/analyze-database.md), поддерживают работу в параллельном режиме. Для одновременного запуска инструментов в рамках одного диагностического сеанса установите флажки рядом с ними и запустите сеанс.

![Центр диагностики — выбраны все инструменты](../profiling/media/diaghuballtoolsselected.png "Центр диагностики — выбраны все инструменты")

>[!NOTE]
>Некоторые инструменты, такие как [Распределение объектов .NET](../profiling/dotnet-alloc-tool.md), нельзя запустить вместе с другими из-за высоких издержек или других технических ограничений.

## <a name="time-filtering"></a>Фильтрация по времени 

Во время анализа можно выполнять фильтрацию по времени в разных инструментах, что позволяет использовать данные одного инструмента для сужения временного диапазона и фильтрации данных в другом инструменте. Эта функция помогает сузить объем анализируемых данных до определенных моментов во времени, чтобы вы могли лучше понять состояние приложения.

![Центр диагностики — фильтрация по времени](../profiling/media/diaghubtimefiltering.png "Центр диагностики — фильтрация по времени")

## <a name="see-also"></a>См. также

- [Оптимизация параметров профилировщика](../profiling/optimize-profiler-settings.md)
- [Запуск средств профилирования с отладчиком или без него](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Общие сведения о методах сбора данных о производительности](../profiling/understanding-performance-collection-methods-perf-profiler.md)
