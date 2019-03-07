---
title: Отладка службы Kubernetes Azure live ASP.NET
description: Узнайте, как настроить snappoints и просмотреть моментальные снимки с помощью отладчика моментальных снимков.
ms.custom: ''
ms.date: 02/11/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- aspnet
- azure
ms.openlocfilehash: 21142ada9b8a922e5a66a673eae1059a845f6231
ms.sourcegitcommit: 62149c96de0811415e99bb1e0194e76c320e1a1e
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2019
ms.locfileid: "57007297"
---
# <a name="debug-live-aspnet-azure-kubernetes-services-using-the-snapshot-debugger"></a>Отладка службы Azure Kubernetes live ASP.NET, с помощью отладчика моментальных снимков

Отладчик моментальных снимков создает моментальный снимок в рабочих приложениях, когда выполняется код, который вас интересует. Чтобы указать отладчику на необходимость создать моментальный снимок, следует установить точки прикрепления и точки ведения в коде. Отладчик позволяет увидеть источник ошибки, не затрагивая трафик рабочего приложения. Средство Snapshot Debugger позволяет значительно сократить затраты времени на устранение проблем, возникающих в рабочих средах.

Snappoints и logpoints похожи на точки останова, но в отличие от точки останова, snappoints не приостанавливает работу приложения при попадании. Как правило создается моментальный снимок в точка прикрепления занимает 10 – 20 миллисекунд.

В этом руководстве рассмотрены следующие задачи:

> [!div class="checklist"]
> * Запуск отладчика моментальных снимков
> * Задайте точки прикрепления и Просмотр моментального снимка
> * Задать точка ведения журнала

## <a name="prerequisites"></a>Предварительные требования

* Отладчик моментальных снимков для службы Azure Kubernetes — только доступной в предварительной версии Visual Studio Enterprise 2019 г. или более поздней версии с **рабочую нагрузку разработки Azure**. (В разделе **отдельные компоненты** вкладке его найти в разделе **отладка и тестирование** > **Snapshot debugger**.)

    Если он еще не установлен, установите [предварительной версии Visual Studio 2019 Enterprise](https://visualstudio.microsoft.com/vs/preview/).

* Коллекция моментальных снимков доступна для следующих веб-приложений службы Azure Kubernetes:
  * Приложения ASP.NET Core, выполняющиеся на .NET Core 2.2 или более поздней на Debian 9.
  * Приложения ASP.NET Core, выполняющиеся на .NET Core 2.2 или более поздней на Alpine 3.8.
  * Приложения ASP.NET Core, выполняющиеся на .NET Core 2.2 или более поздней Ubuntu 18.04.

    > [!NOTE]
    > Чтобы обеспечить поддержку отладчика моментальных снимков в AKS, мы предоставили [репозитория с набором данных файлы Dockerfile, демонстрирующие установки в образах Docker](https://github.com/Microsoft/vssnapshotdebugger-docker).

## <a name="open-your-project-and-start-the-snapshot-debugger"></a>Откройте свой проект и запустить отладчик моментальных снимков

1. Откройте проект, который вы хотите отладки моментальных снимков.

    > [!IMPORTANT]
    > Отладка моментальных снимков, необходимо открыть *же версию исходного кода* , опубликованный в службе Azure Kubernetes.

1. Подключите Snapshot Debugger. Можно использовать один из нескольких способов:

    * Выберите **Отладка > подключить Snapshot Debugger...** . Выберите ресурсы AKS развертывается веб-приложения и учетная запись хранилища Azure и нажмите кнопку **Attach**.

      ![Отладчик моментальных снимков, из меню "Отладка"](../debugger/media/snapshot-debug-menu-attach.png)

    * Щелкнуть правой кнопкой мыши проект и выберите **публикации**, а затем на странице публикации щелкните **подключить отладчик моментальных снимков**. Выберите ресурсы AKS развертывается веб-приложения и учетная запись хранилища Azure и нажмите кнопку **Attach**.
    ![Запустить отладчик моментальных снимков на странице публикация](../debugger/media/snapshot-publish-attach.png)

    * В отладочной ориентироваться в раскрывающемся меню выберите **Snapshot Debugger**, нажатия **F5** и при необходимости выберите ресурсы AKS развертывается веб-приложения и службы хранилища Azure учетной записи и нажмите кнопку  **Присоединение**.
    ![Отладчик моментальных снимков, в раскрывающемся меню F5](../debugger/media/snapshot-F5-dropdown-attach.png)

    * С помощью Cloud Explorer (**представление > Cloud Explorer**), щелкните правой кнопкой мыши ресурс AKS развертывается веб-приложения и учетная запись хранилища Azure и нажмите кнопку **подключить отладчик моментальных снимков**.

      ![Запустить отладчик моментальных снимков из Cloud Explorer](../debugger/media/snapshot-launch.png)

    > [!NOTE]
    > Расширение сайта Application Insights также поддерживает отладка моментальных снимков. Если возникнет сообщение об ошибке «узла расширения, которые устарели», см. в разделе [Устранение неполадок, советов и известные проблемы для отладки моментальных снимков](../debugger/debug-live-azure-apps-troubleshooting.md) для обновления сведений.

   ![Режим отладки моментальных снимков](../debugger/media/snapshot-message.png)

   **Модули** окне отображается, когда все модули, загруженные для службы приложений Azure (выберите **Отладка > Windows > модули** чтобы открыть это окно).

   ![Проверьте окно "Модули"](../debugger/media/snapshot-modules.png)

## <a name="set-a-snappoint"></a>Задайте точки прикрепления

1. В редакторе кода выберите левом поле рядом со строкой кода, которые вас интересуют задать точка прикрепления. Убедитесь, что это код, который вы знаете, будет выполняться.

   ![Задайте точки прикрепления](../debugger/media/snapshot-set-snappoint.png)

1. Нажмите кнопку **начать сбор** Включение точки прикрепления.

   ![Включите точки прикрепления](../debugger/media/snapshot-start-collection.png)

    > [!TIP]
    > Не удается шаг при просмотре моментального снимка, но можно разместить несколько точек прикрепления в коде для выполнения в строках кода. При наличии нескольких точек прикрепления в коде, отладчик моментальных снимков обеспечивает доступность соответствующих моментальных снимков из одного сеанса конечного пользователя. Отладчик моментальных снимков делает это, даже при наличии многих пользователей щелкают ссылку на приложение.

## <a name="take-a-snapshot"></a>Сделайте моментальный снимок

При включении точка прикрепления соберет моментальный снимок, при каждом выполнении строку кода, где размещается точка прикрепления. Выполнение может быть вызвана реального запроса на сервере. Для принудительного вашей точки прикрепления для сбора, перейдите в представление браузера веб-узла и выполнять любые действия обязательные, привести к вашей точки прикрепления для проверки касания.

## <a name="inspect-snapshot-data"></a>Проверьте данные моментального снимка

1. При достижении snappoint моментальный снимок отображается в окне средств диагностики. Чтобы открыть это окно, выберите **Отладка > Windows > Показать средства диагностики**.

   ![Откройте точка прикрепления](../debugger/media/snapshot-diagsession-window.png)

1. Дважды щелкните точки прикрепления для открытия моментального снимка в редакторе кода.

   ![Проверьте данные моментального снимка](../debugger/media/snapshot-inspect-data.png)

   В этом представлении наводите указатель мыши на переменные, чтобы просмотреть подсказки данных, используйте **"Локальные"**, **Watches**, и **стек вызовов** windows, а также оценивать выражения.

    На веб-узел по-прежнему активно и не влияет на конечных пользователей. Только один моментальный снимок фиксируется на точки прикрепления по умолчанию: отключает после захвата моментальный снимок точки прикрепления. Если вы хотите собирать другой снимок в точка прикрепления, можно включить точки прикрепления обратно на, щелкнув **обновить коллекцию**.

Можно также добавить дополнительные точки прикрепления для приложения и включить их с **обновить коллекцию** кнопки.

**Нужна помощь?** См. в разделе [Устранение неполадок и известные проблемы](../debugger/debug-live-azure-apps-troubleshooting.md) и [вопросы и ответы по отладке моментальных снимков](../debugger/debug-live-azure-apps-faq.md) страниц.

## <a name="set-a-conditional-snappoint"></a>Задайте условный точка прикрепления

Если сложно воссоздать определенном состоянии в приложении, следует ли помочь использование условной точки прикрепления. Условные точки прикрепления позволяет избежать создания моментального снимка, пока приложение входит в требуемое состояние, например, если переменная имеет определенное значение, которое требуется проверить. Можно задать с помощью выражений, фильтров, условий или числа попаданий.

#### <a name="to-create-a-conditional-snappoint"></a>Создание условной точки прикрепления

1. Щелкните правой кнопкой мыши значок в виде точка прикрепления (пустой шар) и выберите **параметры**.

   ![Выберите параметры](../debugger/media/snapshot-snappoint-settings.png)

1. В окне параметров точки прикрепления введите выражение.

   ![Введите выражение](../debugger/media/snapshot-snappoint-conditions.png)

   В предыдущем примере, создается моментальный снимок только для точки прикрепления при `visitor.FirstName == "Dan"`.

## <a name="set-a-logpoint"></a>Задать точка ведения журнала

Кроме создания моментального снимка, при достижении snappoint, можно также настроить точки прикрепления для регистрации сообщения (то есть создать точка ведения журнала). Точек ведения журнала можно задать без повторного развертывания приложения. Точек ведения журнала, выполняются практически в результате чего не влияние или побочные эффекты для запущенного приложения.

#### <a name="to-create-a-logpoint"></a>Чтобы создать точка ведения журнала

1. Щелкните правой кнопкой мыши значок в виде точка прикрепления (синий шестиугольник) и выберите **параметры**.

1. В окне параметров точки прикрепления выберите **действия**.

    ![Создание точка ведения журнала](../debugger/media/snapshot-logpoint.png)

1. В **сообщение** , можно ввести новое сообщение журнала, которые будут использоваться для входа. Также можно оценить переменные в сообщении журнала, поместив их в фигурных скобках.

    Если вы выберете **отправить в окно вывода**, когда достигнута точка ведения журнала, сообщение будет отображаться в окне средств диагностики.

    ![Точка ведения журнала данных в окне сеансу diagsession](../debugger/media/snapshot-logpoint-output.png)

    Если вы выберете **отправить в журнал приложений**, когда будет достигнута точка ведения журнала, сообщение будет отображаться в любом месте, вы можете просмотреть сообщения из `System.Diagnostics.Trace` (или `ILogger` в .NET Core), такие как [App Insights](/azure/application-insights/app-insights-asp-net-trace-logs).

## <a name="next-steps"></a>Следующие шаги

В этом руководстве вы узнали, как использовать отладчик моментальных снимков для Kubernetes в Azure. Вы можете прочитать дополнительные сведения об этой функции.

> [!div class="nextstepaction"]
> [Ответы на часто задаваемые вопросы по отладке моментальных снимков](../debugger/debug-live-azure-apps-faq.md)