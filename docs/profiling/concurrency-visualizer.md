---
title: Визуализатор параллелизма | Документы Майкрософт
ms.date: 07/11/2017
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a955304e1a0939bbe7398b48a5e9ff30461d8745
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037345"
---
# <a name="concurrency-visualizer"></a>Визуализатор параллелизма

> [!NOTE]
> Визуализатор параллелизма — это дополнительное расширение Visual Studio. Загрузите визуализатор параллелизма и средства сбора данных визуализатора параллелизма по следующим ссылкам:
>
> - Скачайте расширение [Визуализатор параллелизма для Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview).
> - Скачайте расширение [Визуализатор параллелизма для Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview).
> - Скачайте расширение [Визуализатор параллелизма для Visual Studio 2015](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015).
> - Скачайте [средства сбора данных визуализатора параллелизма для Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).
>
> С помощью [служебной программы командной строки "Визуализатор параллелизма" (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) можно собирать трассировки из командной строки, чтобы просматривать их в визуализаторе параллелизма для Visual Studio 2015. Это средство можно использовать на компьютерах без установленной среды Visual Studio.

Визуализатор параллелизма можно использовать для изучения работы многопоточного приложения. Представления в визуализаторе параллелизма предоставляют графические, табличные и текстовые данные, отражающие временные связи между потоками в программе и системе в целом. С помощью визуализатора параллелизма можно найти узкие места по производительности, случаи избыточного использования ЦП, конфликты потоков, межъядерную миграцию потоков, задержки синхронизации, действия DirectX, области перекрывающихся операций ввода-вывода и другие сведения. Эти представления предоставляют данные, действия с которыми можно выполнять путем связывания выводимой графической информации со стеками вызова и исходным кодом.

> [!NOTE]
> Визуализатор параллелизма не поддерживает веб-проекты.

Визуализатор параллелизма основывается на функции [Трассировка событий Windows](/windows/win32/etw/event-tracing-portal) .

## <a name="related-topics"></a>См. также

|Title|Description|
|-----------|-----------------|
|[Представление использования](../profiling/utilization-view.md)|Содержит описание процедуры просмотра и анализа системных действий для всех процессоров.|
|[Представление "Потоки"](../profiling/threads-view-parallel-performance.md)|Содержит описание процедуры анализа взаимодействия между потоками программы.|
|[Представление "Ядра"](../profiling/cores-view.md)|Содержит описание процедуры анализа миграции потоков между ядрами.|
|[Общие шаблоны для неправильно работающих многопоточных приложений](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Описывает несколько общих шаблонов и показывает, как они отображаются в визуализаторе параллелизма.|
|[Блог о параллельной разработке в Visual Studio](/archive/blogs/visualizeparallel/)|Содержит советы и рекомендации для визуализатора параллелизма.|
|[Представления отчетов о производительности](../profiling/performance-report-views.md)|Содержит справочные сведения по отчетам и представлениям средств профилирования Visual Studio.|
|[Пакет SDK визуализатора параллелизма](../profiling/concurrency-visualizer-sdk.md)|Описывает, как инструментировать исходный код для отображения дополнительных сведений в визуализаторе параллелизма.|
|[Служебная программа командной строки "Визуализатор параллелизма" (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Описывает, как использовать программу командной строки визуализатора параллелизма (CVCollectionCmd.exe) для сбора и обработки трассировки на компьютерах, на которых не установлена Visual Studio.|

## <a name="see-also"></a>См. также раздел

- [Профилирование в Visual Studio](../profiling/index.yml)
- [Первое знакомство со средствами профилирования](../profiling/profiling-feature-tour.md)