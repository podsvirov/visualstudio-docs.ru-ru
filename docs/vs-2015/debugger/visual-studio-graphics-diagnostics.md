---
title: диагностика графики Visual Studio | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca0a1613f46f8542a3ede4ce2053b3584824590e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847830"
---
# <a name="visual-studio-graphics-diagnostics"></a>Диагностика графики в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Диагностика графики* в Visual Studio — это набор инструментов для записи и анализа проблем с производительностью и отрисовкой в приложениях Direct3D. Диагностику графики можно использовать для приложений, которые выполняются локально на компьютере под управлением Windows, в эмуляторе устройства Windows либо на удаленном компьютере или устройстве.  
  
 Рабочий процесс диагностики графики начинается с регистрации того, как приложение использует Direct3D — в оперативном режиме непосредственно во время выполнения. Это позволяет сразу проанализировать поведение приложения, предоставить соответствующие сведения для общего доступа либо сохранить их для использования в дальнейшем. Сеансы записи можно инициировать и контролировать вручную с помощью Visual Studio или программы командной строки для захвата **dxcap.exe**. Сеансы записи также можно инициировать и контролировать программными средствами с помощью API-интерфейсов захвата в компоненте диагностики графики.  
  
 После записи сеанса регистрации его содержимое можно в любое время воспроизвести с помощью *анализатора графики* Visual Studio, воссоздавая записанные кадры с применением точно таких же ресурсов и команд отрисовки, которые использовались в приложении. Затем с помощью инструментов, предоставляемых в окне анализатора графики, любые записанные кадры можно проанализировать в деталях. С помощью этих инструментов можно проверить любой вызов Direct3D API, ресурс, объект состояния конвейера, этап конвейера или даже полный журнал всех пикселей в записанном кадре. Благодаря совместному использованию этих инструментов проблемы с отрисовкой можно анализировать интуитивно, начиная с ее проявления на записанном кадре и выполняя детализацию до первопричины в исходном коде приложения, шейдерах или графических ресурсах.  
  
 Для диагностики проблем с производительностью записанный кадр можно проанализировать с помощью инструмента *Анализ кадров*. Этот инструмент анализирует потенциальные оптимизации производительности, автоматически изменяя способ использования Direct3D приложением и оценивая все отклонения. Возможно, раньше вам приходилось вручную вносить и оценивать такие изменения просто для того, чтобы подобрать нужное. Благодаря анализу кадров вы можете вносить только те изменения, вы обязательно дадут результат.  
  
 Диагностика графики помогает обогатить графическую составляющую приложения Direct3D и оптимизировать его выполнение.  
  
 См. сведения о [возможностях диагностики графики в Visual Studio](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Обзор](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Содержит вводные сведения о рабочем процессе и средствах диагностики графики.  
  
 [Начало работы](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 В этом разделе вы узнаете, как установить компонент диагностики графики Visual Studio и начать использовать его для приложения Direct3D.  
  
 [Capturing Graphics Information](../debugger/capturing-graphics-information.md)  
 Для использования диагностики графики при изучении проблемы отрисовки в приложении сначала необходимо записать информацию о том, как приложение использует DirectX. Во время сеанса записи приложение работает в обычном режиме, а вы *захватываете* (т. е. выбираете) интересующие вас кадры. Захваченные данные содержат подробные сведения о том, как отрисовываются кадры. Собранные данные можно сохранить в виде документа журнала графики, чтобы просмотреть его позже или показать другим членам команды.  
  
 [Использование GPU](../debugger/gpu-usage.md)  
 Чтобы использовать диагностику графики для профилирования приложения, используйте инструмент «Использование GPU». Этот инструмент можно использовать в сочетании с другими инструментами профилирования, такими как «Загрузка ЦП», для сопоставления активности ЦП и GPU, которая может вызывать появление проблем с производительностью в приложении.  
  
 [Документ журнала графики](../debugger/graphics-log-document.md)  
 Чтобы начать исследование записанного журнала графики, используйте окно документа журнала графики для выбора захваченного кадра или даже определенного пикселя. Таким образом, можно подробно рассмотреть *события* (т. е. вызовы API DirectX), которые влияют на него.  
  
 [Анализ кадров](../debugger/graphics-frame-analysis.md)  
 После выбора кадра используйте анализ кадров графики для изучения и настройки производительности отрисовки.  
  
 [Список событий](../debugger/graphics-event-list.md)  
 После выбора кадра используйте **список событий графики** для просмотра его событий и определения их связи с проблемой отрисовки.  
  
 [Состояние](../debugger/graphics-state.md)  
 Окно состояния помогает понять состояние графики на момент возникновения текущего события.  
  
 [Этапы конвейера](../debugger/graphics-pipeline-stages.md)  
 В окне **Этапы графического конвейера** можно изучить, как выбранное событие обрабатывается каждым этапом графического конвейера, чтобы найти место, где проблема отрисовки появляется впервые. Анализ этапов конвейера особенно полезен, когда объект не отображается из-за неверного преобразования или когда один из этапов выдает результат, не соответствующий ожиданиям следующего этапа.  
  
 [Стек вызовов событий](../debugger/graphics-event-call-stack.md)  
 **Стек вызовов событий графики** используется для просмотра стека вызовов выбранного события и перехода к коду приложения, связанному с проблемой отрисовки.  
  
 [Журнал пикселей](../debugger/graphics-pixel-history.md)  
 С помощью окна **Журнал пикселей графики** можно проанализировать, как на текущий выбранный пиксель влияют события, и определить событие или сочетание событий, которое вызывает определенные типы проблем отрисовки. Журнал пикселей особенно полезен, когда объект обрабатывается неправильно из-за того, что выходные данные пиксельного шейдера неверны или были неправильно объединены с буфером кадров, или когда объект даже не появляется, поскольку его пиксели были удалены до попадания в буфер кадров.  
  
 [Таблица объектов](../debugger/graphics-object-table.md)  
 **Таблица графических объектов** используется для просмотра свойств и содержимого конкретных объектов и ресурсов Direct3D, влияющих на выбранное событие. Таблица объектов может помочь определить контекст графического устройства, который активен во время события, и изучить содержимое графических ресурсов, например буферов констант, буферов вершин и текстур.  
  
 [Отладчик HLSL](../debugger/hlsl-shader-debugger.md)  
 Чтобы изучить поведение кода шейдера для выбранного события и этапа конвейера графики, воспользуйтесь **отладчиком HLSL**, который позволяет выполнять код пошагово, проверять содержимое переменных и выполнять другие стандартные задачи отладки. Отладчик HLSL можно также использовать для проверки кода вычислительного шейдера независимо от того, обрабатываются ли его результаты далее конвейером графики или просто считываются приложением.  
  
 [Программа командной строки для захвата](../debugger/command-line-capture-tool.md)  
 Используйте программу командной строки для быстрого захвата и воспроизведения графических данных, не прибегая к Visual Studio или программному захвату. В частности, программу командной строки можно использовать в целях автоматизации или в тестовой среде.  
  
 [Примеры](../debugger/graphics-diagnostics-examples.md)  
 Несколько примеров, демонстрирующих использование средств диагностики графики вместе для выявления различных типов проблем отрисовки.  
  
## <a name="related-sections"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)|Содержит вводные сведения о функциональных возможностях отладки в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Графика и игры DirectX](https://msdn.microsoft.com/library/ee663274(v=vs.85).aspx)|Содержит ссылки на статьи, посвященные технологиям графики DirectX.|
