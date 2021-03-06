---
title: Повышение производительности надстройки VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7529c69270b5f33cde32e8a7907f1b80589c43b7
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "92298513"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Повышение производительности надстройки VSTO
  Для повышения удобства работы пользователей можно оптимизировать надстройки VSTO, создаваемые для приложений Office, что позволит быстрее выполнять запуск, завершать работу, открывать элементы и выполнять другие задачи. Если ваша надстройка VSTO предназначена для Outlook, можно уменьшить вероятность ее отключения из-за низкой производительности. Для повышения производительности надстройки VSTO можно реализовать следующие стратегии:

- [Загрузка надстроек VSTO по требованию](#Load).

- [Публикация решений Office с помощью установщика Windows](#Publish).

- [Обход отражения ленты](#Bypass).

- [Выполнение ресурсоемких операций в отдельном потоке](#Perform).

  Дополнительные сведения о том, как оптимизировать надстройку VSTO для Outlook, см. [в разделе критерии производительности для сохранения включенных надстроек VSTO](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a> Загрузка надстроек VSTO по требованию
 Вы можете настроить надстройку VSTO так, чтобы она загружалась только при следующих обстоятельствах:

- когда пользователь запускает приложение в первый раз после установки надстройки VSTO;

- когда пользователь взаимодействует с надстройкой VSTO в первый раз после запуска приложения в любое другое последующее время.

  Например, Надстройка VSTO может заполнить лист данными, когда пользователь нажмет пользовательскую кнопку, помеченную **«получение моих данных**». Приложение должно загрузить надстройку VSTO по крайней мере один раз, чтобы кнопка **получить мои данные** появилась на ленте. Однако Надстройка VSTO не загружается повторно, когда пользователь запускает приложение в следующий раз. Надстройка VSTO загружается только в том случае, когда пользователь нажмет кнопку **Получить мои данные** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Настройка решения ClickOnce для загрузки надстроек VSTO по требованию

1. В области **Обозреватель решений**выберите узел проекта.

2. В строке меню выберите **Вид** > **Страницы свойств**.

3. На вкладке **Публикация** нажмите кнопку **Параметры** .

4. В диалоговом окне **Параметры публикации** выберите элемент списка **Параметры Office** , выберите параметр **Загружать по требованию** , а затем нажмите кнопку **ОК** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Настройка решения установщика Windows для загрузки надстроек VSTO по требованию

1. В реестре задайте для параметра `LoadBehavior` ** _Root_ \\ \\ _ID надстройки_ \софтваре\микрософт\оффице_applicationName_\аддинс** значение **0x10**.

     Дополнительные сведения см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Настройка решения для загрузки надстроек VSTO по требованию при отладке решения

1. Создайте скрипт, который устанавливает `LoadBehavior` для ключа ** _Root_ \\ \\ _идентификатора надстройки_ root \софтваре\микрософт\оффице_applicationName_\аддинс** значение **0x10**.

     В следующем коде показан пример такого скрипта.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Создайте событие после сборки, которое обновляет реестр с помощью скрипта.

     Ниже приведен пример командной строки, который можно добавить в событие после сборки.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Сведения о создании события после сборки в проекте C# см. [в разделе инструкции. Указание событий сборки &#40;&#35;&#41;](../ide/how-to-specify-build-events-csharp.md)в.

     Сведения о создании события после сборки в Visual Basic проекте см. в разделе [как указать события сборки &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a> Публикация решений Office с помощью установщик Windows
 Если вы публикуете решение с помощью установщик Windows, среда выполнения средств Visual Studio 2010 Tools для Office обходит следующие шаги при загрузке надстройки VSTO.

- Проверка схемы манифеста.

- Автоматическая проверка наличия обновлений.

- Проверка цифровых подписей манифестов развертывания.

  > [!NOTE]
  > Этот подход не нужен, если надстройка VSTO развертывается в безопасном месте на компьютерах пользователей.

  Дополнительные сведения см. в статье [развертывание решения Office с помощью установщик Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> Обход отражения ленты
 Если вы создаете решение с помощью [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] , убедитесь, что пользователи установили последнюю версию среды выполнения Visual Studio 2010 Tools для Office при развертывании решения. Более старые версии среды выполнения VSTO отражены в сборках решений для выявления настроек ленты. Этот процесс может привести к замедлению загрузки надстройки VSTO.

 В качестве альтернативы можно запретить любой версии среды выполнения средств Visual Studio 2010 для Office использовать отражение для задания настроек ленты. Чтобы выполнить эту стратегию, переопределите `CreateRibbonExtensibility` метод и явно возвратите объекты Ribbon. Если надстройка VSTO не содержит настроек ленты, вернитесь в `null` метод.

 В следующем примере возвращается объект Ribbon на основе значения поля.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> Выполнение ресурсоемких операций в отдельном потоке выполнения
 Рассмотрите возможность выполнения длительных задач (например, соединений с базой данных или других видов сетевых вызовов) в отдельном потоке. Дополнительные сведения см. [в разделе Поддержка потоков в Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Весь код, вызывающий объектную модель Office, должен выполняться в основном потоке.

## <a name="see-also"></a>См. также раздел

- [Загрузка надстроек VSTO по требованию](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [Отложенная загрузка среды CLR в надстройках Office](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [Создание надстроек VSTO для Office с помощью Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)