---
title: Общие сведения о доменных языках | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 29e5b6f2-ece4-4f3b-ab08-5f957418702f
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b76142dfbc2dca860591bf3c3cb73c2971f56b22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655371"
---
# <a name="about-domain-specific-languages"></a>О доменных языках
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В отличие от универсального языка, такого как C# или UML, доменный язык (DSL) предназначен для выражения инструкций в определенном пространстве или домене.

 Хорошо известный домен DSL включает регулярные выражения и SQL. Каждый домен DSL гораздо лучше, чем универсальный язык для описания операций с текстовыми строками или базами данных, но гораздо хуже для описания идей, находящихся за пределами собственной области. Для отдельных отраслей также предусмотрен собственный домен. Например, в телекоммуникационной отрасли языки описания вызовов широко используются для указания последовательности Штатов в телефонном звонке, а в индустрии авиаперелетов Стандартный DSL используется для описания полетом.

 Ваш бизнес и ваш проект также имеют дело с особыми наборами концепций, которые можно описать с помощью DSL. Например, можно определить DSL для одного из следующих приложений:

- Планирование путей перехода на веб-сайте.

- Схемы подключения для электронных компонентов.

- Сети конвейера конвейерных и багажа, обрабатывающие оборудование для аэропорта.

  При проектировании DSL необходимо определить *доменный класс* для каждого из важных концепций в домене, таких как веб-страница, лампа или Рабочий стол для возврата аэропорта. Для связывания концепций необходимо определить *доменные отношения* , такие как гиперссылка, канал или лента конвейера.

  Пользователи вашего DSL создают *модели.* Модели являются *экземплярами* DSL. Например, они описывают конкретный веб-сайт или подключение определенного устройства или систему обработки багажа в определенном аэропорту.

  Пользователи могут просматривать модель как схему или как форму Windows Forms. Модели также можно просматривать в виде XML, то есть как они хранятся. При определении DSL вы определяете, как экземпляры каждого доменного класса и отношения отображаются на экране пользователя. Обычный DSL отображается как коллекция значков или прямоугольников, Соединенных стрелками.

  На следующем рисунке показана небольшая модель в схематическое DSL:

  ![Модель1 семейного древа Тюдор](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")

## <a name="what-you-can-do-with-dsls"></a>Возможности DSL
 Типичное приложение DSL заключается в создании программного кода или других артефактов. При определении DSL можно определить *текстовые шаблоны* , которые СЧИТЫВАЮТ модель DSL и создают текстовые файлы.

 Например, можно написать шаблоны, которые принимают план аэропорта и создают часть программного обеспечения для обработки багажа, а также некоторые пользовательские документы, описывающие этот план.

 После определения DSL его можно распространить другим пользователям, которые могут установить его на своих компьютерах. Пользователи DSL могут создавать и изменять модели в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

 Можно также определить команды меню и другие средства, помогающие пользователям редактировать DSL, ограничения проверки, чтобы обеспечить правильное использование DSL, а также шаблоны элементов, помогающие пользователям создавать новые экземпляры. Можно заключить один или несколько языков DSL с помощью средств и других [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширений в виде интегрированного пакета.

 Как правило, доменный язык создается, когда группа разработчиков должна написать подобный код для нескольких продуктов. Например, компания, специализирующаяся на системах обработки багажа, может определить DSL Track, с помощью которого можно создать некоторый код для каждой установки. Преимущество DSL заключается в том, что они могут быть понятны своим клиентам, что код, созданный из него, надежен и что система может быть быстро обновлена при изменении требований клиентов.

 [!INCLUDE[dsl](../includes/dsl-md.md)] позволяет создать доменный язык с собственным графическим конструктором и собственной нотацией схемы, а затем использовать этот язык для создания соответствующего исходного кода для каждого проекта.

## <a name="domain-specific-development"></a>Разработка для конкретного домена
 Разработка для конкретного домена — это процесс определения частей приложений, которые можно моделировать с помощью доменного языка, а затем создание языка и его развертывание разработчикам приложений. Разработчики используют доменный язык для создания моделей, характерных для их приложений, используют модели для создания исходного кода, а затем используют исходный код для разработки приложений.

## <a name="aspects-of-graphical-domain-specific-development"></a>Характеристики графической разработки для конкретного домена
 Графический язык, относящийся к домену, должен включать следующие функции:

- Notation

- Модель предметной области

- Создание артефактов

- Сериализация

- Интеграция с Visual Studio

### <a name="notation"></a>Notation
 Доменный язык должен иметь достаточно небольшой набор элементов, который можно легко определить и расширить, чтобы представить специфические для домена конструкции. Нотация состоит из фигур, представляющих элементы, и соединителей, которые представляют связи между элементами на графической поверхности диаграммы. В [!INCLUDE[dsl](../includes/dsl-md.md)] формы можно расширять и уточнять, чтобы представить элементы доменного языка.

### <a name="domain-model"></a>Модель предметной области
 Доменный язык должен объединять набор элементов и связи между ними с согласованной грамматикой. Он также должен определять, являются ли сочетания элементов и связей допустимыми. Например, языки программирования обычно предотвращают циклическое наследование, при котором один класс является производным от второго класса, а второй класс является производным от первого класса. Ограничения также можно использовать для выражения бизнес-логики, например, один человек не может быть зависимым от самого себя. [!INCLUDE[dsl](../includes/dsl-md.md)] использует ограничения для выражения типов ограничений, требуемых для большинства языков, зависящих от домена.

### <a name="artifact-generation"></a>Создание артефактов
 Одной из основных целей доменного языка является создание артефакта, например исходного кода, XML-файла или других полезных данных. Как правило, изменение в модели означает изменение в артефакте. Можно использовать [!INCLUDE[dsl](../includes/dsl-md.md)] для создания артефактов и их повторного создания при изменении модели.

### <a name="serialization"></a>Сериализация
 Доменный язык должен быть сохранен в определенной форме, которая может быть изменена, сохранена, закрыта и перезагружена. [!INCLUDE[dsl](../includes/dsl-md.md)] использует формат XML, который позволяет определить и настроить сериализацию или сохранение доменного языка.

### <a name="integration-with-visual-studio"></a>Интеграция с Visual Studio
 Поскольку [!INCLUDE[dsl](../includes/dsl-md.md)] размещается в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , он расширяет многие [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] окна и элементы управления. Он также позволяет настраивать поведение команд меню, элементов панели элементов и других элементов пользовательского интерфейса.

 Вы также можете создать адаптер шины модели для конкретного доменного языка. Этот адаптер позволяет ссылаться на модель и элементы в модели и позволяет писать код, который может получать доступ к экземпляру DSL и обновлять его. Используя мощный механизм шины модели, можно писать [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] расширения, работающие с несколькими моделями. Кроме того, можно создавать автономные приложения, работающие с моделями. Дополнительные сведения см. в разделе [Интеграция моделей с помощью Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Преимущества разработки для конкретного домена
 Доменный язык может предоставить следующие преимущества:

- Содержит конструкции, точно соответствующие области проблемы.

     В отличие от языков общего назначения, доменный язык состоит из элементов и связей, которые непосредственно представляют логику пространства проблем. Например, приложение страхового полиса должно включать элементы для политик и утверждений. Доменный язык упрощает проектирование приложения и поиск и исправление ошибок логики.

- Позволяет неразработчикам и людям, не знающим домен, понять общую структуру.

     С помощью графического доменного языка можно создать визуальное представление домена, чтобы разработчики, не являющиеся разработчиками, могли легко понять структуру приложения.

- Упрощает создание прототипа окончательного приложения.

     Разработчики могут использовать код, создаваемый их моделью, для создания приложения-прототипа, которое они могут отображать клиентам.

## <a name="the-process-of-domain-specific-development"></a>Процесс разработки для конкретного домена
 Большинство команд разработки программного обеспечения, использующих доменные языки, выполняют следующие шаги для создания и использования их моделей:

- Команда различает переменные части домена из частей, которые никогда не изменяются.

- Разработчики пишут код для фиксированных частей и оставляют точки расширения для переменных частей.

- Ведущий разработчик программного обеспечения или архитектор создает доменный язык, включающий шаблоны разработки фиксированных частей домена и точки расширения для переменных частей.

- Ведущий разработчик программного обеспечения или архитектор развертывает доменный язык для разработчиков различных приложений, создаваемых группой.

- Каждый разработчик создает модель, которая применяется к конкретному приложению.
