---
title: Средства тестирования
ms.date: 03/16/2018
ms.topic: conceptual
helpviewer_keywords:
- testing tools [Visual Studio]
- unit tests [Visual Studio]
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 5d61ab4ec7647921a928841d2a9c89fb84becdf9
ms.sourcegitcommit: 754133c68ad841f7d7962e0b7a575e133289d8a8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/09/2020
ms.locfileid: "91928073"
---
# <a name="first-look-at-testing-tools-in-visual-studio"></a>Первое знакомство со средствами тестирования в Visual Studio

Средства тестирования Visual Studio могут помочь вам и вашей команде в разработке и поддержке высоких стандартов качества кода.

> [!NOTE]
> Модульное тестирование доступно во всех выпусках Visual Studio. Другие средства тестирования, такие как Live Unit Testing, IntelliTest и закодированные тесты пользовательского интерфейса, доступны только в выпуске Visual Studio Enterprise. Дополнительные сведения о выпусках см. в статье [Сравнение интегрированных сред разработки Visual Studio](https://visualstudio.microsoft.com/vs/compare/).

## <a name="test-explorer"></a>Обозреватель тестов

Окно **Обозреватель тестов** помогает разработчикам создавать и запускать модульные тесты, а также управлять ими. Можно использовать платформу для выполнения модульных тестов Microsoft или одну из нескольких сторонних платформ, в том числе платформы с открытым исходным кодом.

::: moniker range="vs-2017"
![Обозреватель тестов Visual Studio](media/devtest-testexplorer.png)
::: moniker-end

::: moniker range="vs-2019"
![Обозреватель тестов Visual Studio 16.2](media/vs-2019/test-explorer-16-2.PNG)
::: moniker-end

* [Приступая к работе с модульным тестированием](unit-test-your-code.md)
* [Выполнение модульных тестов с помощью обозревателя тестов](run-unit-tests-with-test-explorer.md)
* [Вопросы и ответы по обозревателю тестов](test-explorer-faq.md)
* [Установка платформ модульного тестирования сторонних поставщиков](install-third-party-unit-test-frameworks.md)

Visual Studio является расширяемой системой и позволяет использовать сторонние адаптеры модульного тестирования, такие как NUnit и xUnit.net. Кроме того, функция клонов кода обеспечивает высокое качество программного обеспечения, помогая определить блоки семантически сходного кода, которые являются кандидатами для совместного исправления ошибок или рефакторинга.

![Интеграция тестов сторонних разработчиков](media/devtest-thirdparty.png)

## <a name="live-unit-testing"></a>Live Unit Testing

Функция [Live Unit Testing](../test/live-unit-testing.md) автоматически выполняет модульные тесты в фоновом режиме и графически отображает объем протестированного кода и результаты тестирования в редакторе кода Visual Studio.

## <a name="intellitest"></a>IntelliTest

IntelliTest автоматически создает модульные тесты и тестовые данные для управляемого кода. IntelliTest улучшает покрытие и значительно сокращает усилия, необходимые для создания и обслуживания модульных тестов для нового и существующего кода.

![IntelliTest в действии](media/devtest-intellitest.png)

* [Создание модульных тестов для кода с помощью IntelliTest](generate-unit-tests-for-your-code-with-intellitest.md)
* [IntelliTest — один тест на любой случай](https://devblogs.microsoft.com/devops/intellitest-one-test-to-rule-them-all/)
* [Справочное руководство по IntelliTest](intellitest-manual/index.md)

## <a name="code-coverage"></a>Покрытие кода

[Объем протестированного кода](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md) позволяет определить, какая часть кода проекта в действительности тестируется закодированными тестами, такими как модульные тесты. Для обеспечения эффективной защиты от ошибок тесты должны выполнять ("покрывать") большую часть кода.

Анализ объема протестированного кода может применяться и к управляемому, и к неуправляемому (машинному) коду.

Покрытие кода возможно при выполнении методов тестов с помощью обозревателя тестов. В таблице результатов отображается процент кода, который был выполнен в каждой сборке, классе и методе. Кроме того, редактор исходного кода показывает, какой код был протестирован.

* [Использование параметра объема протестированного кода для определения объема протестированного кода](using-code-coverage-to-determine-how-much-code-is-being-tested.md)
* [Модульное тестирование, объем протестированного кода и анализ клонов кода с помощью Visual Studio (лаборатория)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)
* [Настройка анализа объема протестированного кода](customizing-code-coverage-analysis.md)

## <a name="microsoft-fakes"></a>Microsoft Fakes

[Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md) помогает изолировать тестируемый код, заменяя другие части приложения заглушками или оболочками.

## <a name="user-interface-testing-with-coded-ui-and-selenium"></a>Тестирование пользовательского интерфейса с помощью закодированного теста и Selenium

Закодированные тесты пользовательского интерфейса позволяют создать полностью автоматические тесты для проверки функциональности и поведения пользовательского интерфейса приложения. Они автоматизируют тестирование пользовательского интерфейса в разных технологиях, включая приложения универсальной платформы Windows на основе XAML, приложения браузера и приложения SharePoint.

Если вам нужны лучшие в своем роде закодированные тесты пользовательского интерфейса или универсальные тесты на основе браузера с использованием Selenium, Visual Studio предоставляет все необходимые для этого инструменты.

![Тестирование пользовательского интерфейса с помощью закодированных тестов](media/devtest-codeduitest.png)

* [Использование автоматизации пользовательского интерфейса для тестирования кода](use-ui-automation-to-test-your-code.md)
* [Руководство по созданию, изменению и обслуживанию закодированного теста пользовательского интерфейса](walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)
* [Тестирование приложений UWP с помощью закодированных тестов пользовательского интерфейса](test-uwp-app-with-coded-ui-test.md)
* [Введение в использование закодированных тестов пользовательского интерфейса с помощью Visual Studio Enterprise (лаборатория)](https://www.boost.org/doc/libs/1_71_0/libs/test/doc/html/index.html)

## <a name="load-testing"></a>Нагрузочное тестирование

[Нагрузочное тестирование](../test/quickstart-create-a-load-test-project.md) позволяет моделировать нагрузку на серверное приложение посредством выполнения модульных тестов и веб-тестов производительности.

## <a name="related-scenarios"></a>Связанные сценарии

* [Произвольное и ручное тестирование (Azure Test Plans)](/azure/devops/test/index?view=vsts&preserve-view=true)
* [Нагрузочное тестирование (Azure Test Plans)](/azure/devops/test/load-test/index?view=vsts&preserve-view=true)
* [Непрерывное тестирование (Azure Test Plans)](/azure/devops/pipelines/test/getting-started-with-continuous-testing?view=vsts&preserve-view=true)
* [Средства анализа кода](../code-quality/code-analysis-for-managed-code-overview.md)
