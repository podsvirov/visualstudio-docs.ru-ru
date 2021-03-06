---
title: 'UML-схемы последовательностей: рекомендации | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cdd853307bdea28c48762a6a3f0416e698b577ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850123"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sequence Diagrams: Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно нарисовать *схему последовательностей* , чтобы отобразить взаимодействие. Взаимодействие — это последовательность сообщений между типичными экземплярами классов, компонентов, подсистем или субъектов.

 Схемы последовательностей UML являются частью модели UML и существуют только в проектах моделирования UML. Чтобы создать UML-схему последовательностей, в меню **архитектура** выберите пункт **создать UML или схему слоев**. Узнайте больше о [элементах схемы последовательностей UML](../modeling/uml-sequence-diagrams-reference.md) или [UML-схемах моделирования](../modeling/edit-uml-models-and-diagrams.md) в целом. Демонстрационные видеоролики см. в разделе [наброска взаимодействия с помощью схем последовательностей (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>В этом разделе
 [Использование схем последовательностей UML](#Using)

 [Основные этапы создания схем последовательностей](#BasicSteps)

 [Создание и использование простых схем последовательностей](#Simple)

 [Классы и линии жизни](#ClassesAndLifelines)

 [Создание последовательностей взаимодействия с возможностью повторного использования](#Multiple)

 [Сворачивание групп линий жизни](#Collapse)

 [Описание структур управления с помощью фрагментов](#Fragments)

## <a name="using-uml-sequence-diagrams"></a><a name="Using"></a> Использование UML-схем последовательностей
 Схемы последовательностей можно использовать в разных целях и на разных уровнях детализации программы. Как правило, схема последовательностей создается в указанных ниже случаях.

- Если есть схема вариантов использования, которая обобщает сведения о пользователях системы и их целях, можно создать схемы последовательностей, чтобы описать, как основные компоненты системы взаимодействуют для достижения цели каждого варианта использования. Дополнительные сведения см. в разделе [UML-схемы вариантов использования: рекомендации](../modeling/uml-use-case-diagrams-guidelines.md).

- Если определены сообщения, поступающие в интерфейс компонента, можно создать схемы последовательностей, чтобы описать, как внутренние части компонента взаимодействуют для достижения результата, требуемого для каждого входящего сообщения. Дополнительные сведения см. в разделе [UML-схемы компонентов: рекомендации](../modeling/uml-component-diagrams-guidelines.md).

  Создание схем последовательностей имеет несколько преимуществ.

- Можно легко увидеть, как задачи распределяются между компонентами.

- Можно определить шаблоны взаимодействия, затрудняющие обновление программы.

## <a name="relationship-to-other-diagrams"></a>Отношение к другим схемам
 Схемы последовательностей UML можно использовать с другими схемами несколькими способами.

#### <a name="lifelines-and-types"></a>Линии жизни и типы
 Линии жизни, создаваемые в схеме последовательностей, могут представлять типичные экземпляры компонентов или классов в системе. Можно создавать линии жизни из типов, а типы — из линий жизни, а также отображать типы на схемах классов и компонентов UML. Дополнительные сведения см. в разделе [классы и линии жизни](#ClassesAndLifelines).

#### <a name="parameter-types"></a>Типы параметров
 С помощью схемы классов UML можно также описать типы параметров и возвращаемые значения в сообщениях, обмен которыми ведется между линиями жизни.

#### <a name="use-case-details"></a>Подробности варианта использования
 Вариант использования представляет цель пользователя, а также последовательность шагов для достижения этой цели. Последовательность шагов можно описать несколькими способами. Во-первых, можно создать схему последовательностей, показывающую взаимодействия между пользователями и основными компонентами системы. Дополнительные сведения см. в разделе [UML-схемы вариантов использования: рекомендации](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="basic-steps-for-drawing-sequence-diagrams"></a><a name="BasicSteps"></a> Основные шаги для рисования схем последовательностей
 Полный список элементов на схемах последовательностей см. в разделе [UML-схемы последовательностей. Справочник](../modeling/uml-sequence-diagrams-reference.md).

> [!NOTE]
> Подробные инструкции по созданию схем моделирования см. в разделе [изменение моделей и схем UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>Создание схемы последовательностей

1. В меню **архитектура** выберите пункт **создать UML или схему слоев**.

2. В разделе **шаблоны**щелкните **схема последовательностей UML**.

3. Назовите схему.

4. В меню **Добавить в проект моделирования**выберите существующий проект моделирования в решении или **Создайте новый проект моделирования**и нажмите кнопку **ОК**.

    Откроется новая схема последовательностей с панелью элементов **схемы последовательностей** . Эта панель содержит требуемые элементы и соединители.

   ![Части схемы последовательностей](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>Создание схемы последовательностей

1. Перетащите **линии жизни** (1) из **области элементов** на схему, чтобы представить экземпляры классов, компонентов, субъектов или устройств.

    > [!NOTE]
    > Можно также создать линию жизни, перетащив существующий класс, интерфейс, субъект или компонент из **обозревателя моделей UML** на схему. Так создается линия жизни, представляющая экземпляр выбранного типа.

2. Создайте сообщения, чтобы показать, как линии жизни взаимодействуют для достижения конкретной цели.

     Чтобы создать сообщение (3, 4, 6, 7), щелкните инструмент создания сообщений. Затем щелкните отправляющую линию жизни в том месте, где необходимо начать сообщение, и щелкните получающую линию жизни.

     Вхождение выполнения (5) отображается на получающей линии жизни. Вхождение выполнения представляет период времени, в течение которого экземпляр выполняет метод. Можно создать другие сообщения, начинающиеся с вхождения выполнения.

3. Чтобы показать сообщение, поступающее из неизвестного источника события (9) или передающее данные неизвестным получателям (10), создайте асинхронное сообщение из пустого пространства на схеме или в него.  Эти сообщения называются *найденными сообщениями* (9) и *потерянными сообщениями* (10).

    > [!NOTE]
    > Чтобы переместить группу жизненных линий жизни, которые содержат потерянные или найденные сообщения, выполните следующие действия, чтобы выбрать линии жизни перед перемещением: Нарисуйте прямоугольник вокруг этих линий жизни или нажмите и удерживайте клавишу **CTRL** , щелкнув каждую линию жизни. Если **выбрать все** **CTRL** + **A** линии жизни, а затем переместить их, то все потерянные или найденные сообщения, прикрепленные к этим линиям жизни, не будут перемещены. В этом случае такие сообщения можно переместить отдельно.

4. Создайте схемы последовательностей для каждого основного сообщения одному и тому же компоненту или системе.

#### <a name="to-change-the-order-of-messages"></a>Изменение порядка сообщений

- Перетащите сообщение вверх или вниз по соответствующей линии жизни. Вы можете перетаскивать сообщения на другие сообщения, а также в блок выполнения или из него.

     \- или -

- Щелкните сообщение и используйте клавиши **стрелка вверх** и **стрелка вниз** для настройки положения сообщения. Чтобы изменить порядок сообщений, используйте **клавиши Shift + стрелка вверх** и **Shift + стрелка вниз** .

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Перемещение или копирование последовательностей сообщений на схеме последовательностей

1. Щелкните правой кнопкой мыши сообщение (3, 4) и выберите команду **Копировать**.

2. Щелкните правой кнопкой мыши вхождение выполнения (5) или линию жизни (1), из которой нужно отправить новое сообщение, и выберите команду **Вставить**. При необходимости нового отправителя можно изобразить на другой схеме.

     Копия сообщения и все его дочерние сообщения добавляются в конец вхождения выполнения или в конец линии жизни.

    > [!NOTE]
    > Вставленное сообщение всегда отображается в конце вхождения выполнения или линии жизни. Вставив сообщение, можно перетащить его на прежнее место.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Отображение и изменение текста подписи сообщения

- Для того чтобы текст подписи был видим, линия жизни целевого объекта должна быть связана или сопоставлена с каким-либо типом. Для выполнения этой задачи необходимо выполнить одно из указанных ниже действий.

  - Щелкните линию жизни правой кнопкой мыши и выберите команду **создать класс**.

     -или-

  - Выберите линию жизни, нажмите клавишу **F4**, а затем в окне **Свойства** задайте для свойства **тип** значение существующий тип или укажите имя для нового типа. Щелкните правой кнопкой мыши метку сообщения и выберите команду **Создать операцию**.

    Текст подписи отобразится под меткой сообщения. Теперь текст подписи можно изменять. Дополнительные сведения см. в разделе [классы и линии жизни](#ClassesAndLifelines).

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Оптимизация размещения элементов на схеме последовательностей

- Щелкните правой кнопкой мыши пустую часть диаграммы и выберите пункт **изменить макет**.

- Чтобы отменить операцию, нажмите кнопку **изменить**, а затем кнопку **отменить**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>Изменение пакета, которому принадлежит взаимодействие

1. В **обозревателе моделей UML**найдите взаимодействие, которое отображается на схеме последовательностей.

    > [!NOTE]
    > Взаимодействие не будет отображаться в **обозревателе моделей UML** , пока вы не добавите первую линию жизни в схему последовательностей.

2. Перетащите взаимодействие в пакет.

     \- или -

     Щелкните взаимодействие правой кнопкой мыши и выберите команду **Вырезать**. Щелкните пакет правой кнопкой мыши и выберите команду **Вставить**.

## <a name="creating-and-using-simple-sequence-diagrams"></a><a name="Simple"></a> Создание и использование простых схем последовательностей
 Наиболее простая и часто используемая форма схемы последовательностей содержит только линии жизни и сообщения. Схема этого вида позволяет ясно показать типичную последовательность взаимодействий между объектами в проектируемой системе или между системой и ее пользователями. Часто этого достаточно, чтобы обсуждать проектируемую систему и передавать сведения о ней.

 При создании простой схемы последовательностей не следует забывать об указанных ниже моментах.

### <a name="types-of-message"></a>Типы сообщений
 Для создания сообщений можно использовать три различных инструмента.

- Используйте **синхронное** средство для описания взаимодействия, в котором отправитель ждет, пока получатель возвратит ответ (3).

     **<\<return>>** В конце вхождения выполнения будет отображаться стрелка. Она обозначает, что контроль над взаимодействием возвращается отправителю.

- Используйте **асинхронное** средство для описания взаимодействия, в котором отправитель может продолжать работу немедленно, не дожидаясь получателя (4).

- Используйте средство **создать** для описания взаимодействия, в котором отправитель создает получателя (8).

     Сообщение о создании должно быть первым сообщением, которое получит получатель.

### <a name="annotating-the-interactions"></a>Создание заметок о взаимодействиях
 Чтобы описать последовательность более подробно, можно поместить **Комментарий** в любое место на схеме.

 С помощью **ссылок на комментарии**можно связать комментарий с жизненным циклом, выполнением, использованием взаимодействия и фрагментами.

> [!CAUTION]
> Если нужно прикрепить комментарий к определенной точке последовательности, свяжите его с вхождением выполнения, использованием взаимодействия или фрагментом. Не связывайте комментарий с линией жизни, потому что в этом случае он не будет прикреплен к правильной точке последовательности.

 Используйте комментарий в указанных ниже целях.

- Чтобы отметить, что было достигнуто в ключевых точках последовательности. Это позволяет другим пользователям видеть цели взаимодействий.

- Чтобы описать общую цель всей последовательности. Прикрепить комментарий к начальному вхождению выполнения или не прикреплять его ни к чему. Пример: "Клиент выбрал пункты из меню, и ему была предоставлена информация о стоимости этих пунктов".

- Чтобы описать обязанности каждой линии жизни. Прикрепите комментарий к линии жизни. Пример: "Менеджер по обработке заказов собирает сведения о выбранных клиентом пунктах меню".

- Чтобы создавать примечания об исключениях и других вариантах последовательностей, которые могут быть выполнены в качестве альтернативы показанной типичной последовательности. Пример: "Клиент может пропустить остальные элементы последовательности".

  - В качестве более формальной альтернативы этого вида примечаний можно использовать фрагменты. См. раздел [Описание структур управления с помощью фрагментов](#Fragments) .

## <a name="deciding-the-scope-of-the-diagram"></a>Определение области действия схемы
 Очень важно четко обозначить, что должно отображаться на схеме.

#### <a name="initiating-event"></a>Инициирующее событие
 На каждой схеме должна быть показана последовательность взаимодействий, порождаемых одним инициирующим событием. Это может быть, например, одно из следующих событий:

- инициация варианта использования пользователем (например, открытие веб-страницы для покупки продуктов питания);

- сообщение от одного системного компонента другому, например с запросом о доступности пунктов, которые желает приобрести клиент;

- событие, инициируемое изменением состояния, например если уровень запасов определенного товара падает ниже порогового значения.

#### <a name="level-of-detail"></a>Уровень детализации
 Схемы последовательностей могут иметь разные уровни детализации. Уровень детализации можно определять в двух разных измерениях практически независимо друг от друга.

 Линии жизни могут представлять один из следующих уровней детализации:

- объекты в существующем или разрабатываемом программном коде;

- компоненты или их подкомпоненты, как правило, без видов, посредников и других соединительных механизмов;

- система и внешние субъекты.

  Сообщения могут представлять один из следующих уровней детализации:

- программные сообщения в программном коде, в API или веб-интерфейсе;

- транзакции или подтранзакции, например между пользователями и системой или между кодом и базой данных;

- варианты использования — основные взаимодействия между пользователями и системой.

  При анализе существующего кода или описании новой проектируемой системы часто имеет смысл создавать и анализировать представления с меньшей детализацией.

## <a name="describing-variations"></a>Описание вариантов
 На схеме отображается одна типичная последовательность событий. Если нужно показать альтернативные возможности, такие как сценарии сбоев, можно воспользоваться одним из следующих методов:

- создать отдельные схемы последовательностей для описания этих сценариев;

- Используйте [Описание структур управления с фрагментами](#Fragments) для отображения циклов, альтернатив и т. д.

## <a name="assessing-the-design"></a>Оценка проекта
 Схему можно использовать для оценки распределения задач между ее объектами или компонентами. Необходимо провести реструктуризацию, если наблюдаются указанные ниже явления.

- Создается впечатление, что одна линия жизни выполняет все функции, вызывая все остальные элементы схемы, в то время как другие линии жизни лишь пассивно отвечают на эти вызовы.

- Многие сообщения пересекают линии жизни. Каждая линия жизни должна отправлять сообщения небольшому числу соседних элементов и не должна взаимодействовать с их соседями. Как правило, имеется возможность расположить линии жизни так, чтобы сообщения пересекали линии жизни всего в нескольких местах. В местах пересечения целевая линия жизни не должна обмениваться сообщениями, пересекающими какие-либо другие линии жизни.

- Некоторые линии жизни выполняют несколько разных видов задач.  Область ответственности каждой линии жизни должна описываться в одном кратком предложении. В нем должны обобщаться сведения о том, что линия жизни делает в ответ на каждое получаемое сообщение.

## <a name="classes-and-lifelines"></a><a name="ClassesAndLifelines"></a> Классы и линии жизни
 Линии жизни на схемах последовательностей показывают экземпляры классов или интерфейсов компонентов. Существует два способа именования линии жизни.

|**Способ именования**|**Используйте этот формат**|
|--------------------------|-------------------------|
|Анонимный экземпляр типа.<br /><br /> Используйте его, если для каждого типа имеется только одна линия жизни.|*Имени*|
|Именованный экземпляр типа.<br /><br /> Используйте его, если необходимо показать последовательность, включающую несколько экземпляров одного типа.|*имя_объекта*:*TypeName*|

### <a name="creating-lifelines-from-types"></a>Создание линий жизни на основе типов
 Линии жизни можно создавать из уже определенных классов (например, на схеме классов).

> [!NOTE]
> Прежде чем выполнять эту задачу, убедитесь в том, что имеется схема последовательностей.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Создание линии жизни на основе существующего типа

- Перетащите класс, компонент или интерфейс из обозревателя моделей UML на схему последовательностей.

   \- или -

  1. Щелкните правой кнопкой мыши класс, компонент или интерфейс на соответствующей схеме и выберите команду **создать линию жизни**.

  2. В диалоговом окне **Создание линии жизни** выберите схему последовательностей и нажмите кнопку **ОК**.

     Появится новая линия жизни с именованным экземпляром. Ее типом является тип, который вы перетащили.

  > [!NOTE]
  > Это действие можно повторять неограниченное число раз. При этом создаются линии жизни с разными именами экземпляров.

##### <a name="to-change-the-type-of-a-lifeline"></a>Изменение типа линии жизни

1. Щелкните линию жизни правой кнопкой мыши и выберите пункт **Свойства**.

2. В окне **Свойства** задайте свойство **Type** . Можно выбрать тип из раскрывающегося меню или указать новое имя.

### <a name="creating-classes-from-lifelines"></a>Создание классов на основе линий жизни
 Создав одну или несколько схем последовательностей, можно обобщить линии жизни, создав на их основе классы или интерфейсы.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Создание класса или интерфейса на основе линии жизни

1. Щелкните линию жизни правой кнопкой мыши и выберите команду **создать класс** или **создать интерфейс**.

     В обозревателе моделей UML появится новый класс или интерфейс.

2. Создайте в классе или интерфейсе операции для каждого получаемого линией жизни сообщения.

    1. Выделите все сообщения, которые нужно включить.

    2. Щелкните правой кнопкой мыши одно из сообщений и выберите команду **создать метод**.

         Новый класс или интерфейс имеет операции для каждого выделенного сообщения.

         Имя операции отображается под каждой стрелкой сообщения и в свойстве " **Операция** " сообщения.

         Если сообщение включает параметры в форме "(параметр : тип)", они отобразятся в списке параметров новой операции.

        > [!NOTE]
        > Если в схему последовательностей добавляются новые сообщения, этот шаг необходимо повторить.

3. Чтобы просмотреть подробные сведения о новом классе или интерфейсе, добавьте его в схему классов или компонентов.

    1. Откройте или создайте схему классов или компонентов.

    2. Перетащите новый класс или интерфейс из **обозревателя моделей UML** на схему классов.

         Класс или интерфейс появится на схеме классов.

         \- или -

    3. Перетащите новый интерфейс из **обозревателя моделей UML** на компонент или порт на схеме компонентов.

         Интерфейс отображается в компоненте в качестве обозначения без описания операций.

### <a name="creating-classes-for-parameters"></a>Создание классов параметров
 В сообщения на схеме последовательностей можно включить параметры. Схему классов UML можно использовать для описания типов параметров.

## <a name="creating-reusable-interaction-sequences"></a><a name="Multiple"></a> Создание повторно используемых последовательностей взаимодействия
 Для описания последовательности можно использовать отдельную схему, которая содержит подробные сведения, которые необходимо отделить от других, либо сведения, относящиеся к нескольким схемам.

 На одной схеме можно создать прямоугольник использования взаимодействия (12), указывающий на подробные сведения на другой схеме.

 Дважды щелкните использование взаимодействия, чтобы открыть связанную с ним схему последовательностей.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Создание последовательности взаимодействий с возможностью повторного использования на основе существующих линий жизни

1. На **панели элементов**щелкните **взаимодействие использование**.

2. Удерживая нажатой кнопку мыши, перетащите по схеме последовательностей линии жизни, которые нужно включить в последовательность с возможностью повторного использования. Начните с выбора положения по вертикали для вставки использования взаимодействия.

     Использование взаимодействия отображается напротив выбранных линий жизни на схеме последовательностей.

3. Дважды щелкните имя использования взаимодействия и переименуйте его, чтобы описать результат последовательности с возможностью повторного использования на этой схеме.

     \- или -

     Напишите имя в качестве вызова функции с параметрами.

4. Свяжите использование взаимодействия с другой схемой последовательностей. Щелкните использование взаимодействия правой кнопкой мыши и выполните одно из указанных ниже действий.

     Щелкните **создать новую последовательность** , чтобы создать новую схему последовательностей.

     \- или -

     Щелкните **связать с последовательностью** , чтобы связать существующую схему.

     Visual Studio создает связь между использованием взаимодействия и новой последовательностью взаимодействий.

     В решении появляется новая схема последовательностей. На ней отображаются линии жизни, с помощью которых было создано использование взаимодействия.

    > [!NOTE]
    > Отображаются только те линии жизни, с помощью которых было создано использование взаимодействия. На новой схеме не будут отображаться линии жизни, созданные после использования взаимодействия, даже если использование взаимодействия включает эти линии.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Создание последовательности с возможностью повторного использования на основе существующих сообщений

- Щелкните правой кнопкой мыши сообщение, которое необходимо переместить, и выберите пункт **переместить в диаграмму**.

  Visual Studio.

  - заменяет выделенное сообщение и любые дочерние сообщения использованием взаимодействия;

  - перемещает замещенные сообщения на новую схему последовательностей;

  - создает связь между использованием взаимодействия и новой схемой последовательностей.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Переход к последовательности, на которую ссылается использование взаимодействия

- Дважды щелкните использование взаимодействия.

     \- или -

     Щелкните правой кнопкой мыши использование взаимодействия и выберите команду **Переход к последовательности**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Создание заполнителя с использованием взаимодействия
 Вы можете создать использование взаимодействия, не связывая его с другой схемой. Его можно использовать в качестве заполнителя для части последовательности, сведения о которой еще должны быть обработаны. Используйте имя использования взаимодействия, чтобы указать нужный результат.

## <a name="collapsing-groups-of-lifelines"></a><a name="Collapse"></a> Сворачивание групп жизненных циклов жизни
 Вы можете свернуть несколько линий жизни, чтобы группа отображалась как одна линия. Так можно визуально представить группу объектов как один компонент. Сообщения и использования взаимодействий между линиями жизни свернутой группы скрыты. Сообщения и последовательности взаимодействий, включающие другие линии жизни, отображаются.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>Сворачивание группы линий жизни

1. Выберите две или более линий жизни.

2. Щелкните правой кнопкой мыши один из них и выберите **Свернуть**.

     Несколько линий жизни заменяются одной.

     Сообщения и использования взаимодействия, включающие только члены этой группы, скрыты.

3. Щелкните имя, чтобы переименовать группу.

    > [!NOTE]
    > Если развернуть группу, ее имя будет утеряно.

#### <a name="to-expand-a-collapsed-group"></a>Разворачивание свернутой группы

- Щелкните свернутую линию жизни правой кнопкой мыши и выберите **развернуть**.

    > [!NOTE]
    > Имя группы будет утеряно, равно как и любые ссылки из группы на комментарии или рабочие элементы.

## <a name="describing-control-structures-with-fragments"></a><a name="Fragments"></a> Описание структур элементов управления с помощью фрагментов
 Для определения циклов, ветвей и параллельной обработки на схеме последовательностей можно использовать объединенные фрагменты (13). Эти сведения можно отобразить и на схеме деятельности. Схема деятельности не позволяет показывать сообщения, которыми обмениваются субъекты, так же наглядно, но иногда с ее помощью можно более эффективно представить циклы, ветви и параллелизм.

 Полный список типов фрагментов см. в разделе [Описание потока управления с помощью фрагментов на UML-схемах последовательностей](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>Создание объединенного фрагмента

1. Выделите сообщение или последовательность сообщений, начинающихся в одном вхождении выполнения или на одной линии жизни.

    > [!NOTE]
    > Выделите стрелки сообщений, а не вхождения выполнения, на которые указывают сообщения.

2. Щелкните правой кнопкой мыши одно из сообщений, наведите указатель на пункт **окружить**, а затем выберите нужный тип фрагмента.

     Появится новый фрагмент. В нем содержатся выбранные сообщения.

     Если тип объединенного фрагмента допускает наличие нескольких фрагментов, отображается также пустой фрагмент.

3. Чтобы задать условие для фрагмента, щелкните правой кнопкой мыши границу фрагмента и выберите пункт **Свойства**. Задайте свойство **Guard** .

     Условие используется для определения требований к ветви или циклу.

4. Чтобы добавить новый фрагмент к виду, допускающему несколько фрагментов, щелкните правой кнопкой мыши границу фрагмента и наведите указатель на пункт **Добавить**. Щелкните **операнд взаимодействия до** или **операнда взаимодействия после**.

5. Чтобы добавить во фрагмент новые сообщения, используйте инструменты создания сообщений либо скопируйте и вставьте их во фрагмент.

## <a name="see-also"></a>См. также:
 [UML-схемы последовательностей. ссылки для](../modeling/uml-sequence-diagrams-reference.md) [изменения моделей и схем UML](../modeling/edit-uml-models-and-diagrams.md) [схемы вариантов использования UML: ссылки на](../modeling/uml-use-case-diagrams-reference.md) UML-схемы [классов:](../modeling/uml-class-diagrams-reference.md) ссылки на UML- [схемы компонентов:](../modeling/uml-component-diagrams-reference.md) Справочник по схемам [компонентов UML](../modeling/uml-component-diagrams-reference.md) : справочное [видео. изменение наброска взаимодействия с помощью схем последовательностей](https://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-2-Organizing-Features-Into-Use-Cases)
