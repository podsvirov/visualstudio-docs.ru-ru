---
title: Создание схем слоев из кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eea557035ef4e5f1ffa2585e620a331fb6b5cce2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852078"
---
# <a name="create-layer-diagrams-from-your-code"></a>Создание схем слоев на основе кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для визуализации высокоуровневой логической архитектуры программной системы Создайте *схему слоев* в Visual Studio. Чтобы убедиться в том, что код соответствует этой структуре, проверьте его с помощью схемы слоев. Можно создать схемы слоев для проектов Visual C# .NET и Visual Basic .NET. Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. статью [Поддержка версий для инструментов архитектуры и моделирования](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) .

 ![Создание схемы слоев](../modeling/media/layerdiagramvisualizecode.png "лайердиаграмвисуализекоде")

 Схема слоев позволяет организовывать элементы решений Visual Studio в логические, абстрактные группы, называемые *слоями*. Слои можно использовать для описания основных задач, выполняемых этими артефактами, или основных компонентов системы. Каждый слой может содержать другие слои, описывающие более подробные задачи. Можно также указать предполагаемые или существующие *зависимости* между слоями. Эти зависимости, представленные в виде стрелок, указывают, какие слои могут использовать или в настоящее время используют функциональные возможности, представленные другими слоями. Для поддержки архитектурного контроля кода добавьте предполагаемые зависимости в схему, а затем проверьте код по схеме.

## <a name="create-a-layer-diagram"></a><a name="CreateDiagram"></a> Создание схемы слоев
 Перед созданием схемы слоев решение должно иметь проект моделирования. См. статью [Создание UML-проектов моделирования и схем](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> Не следует добавлять, перетаскивать или копировать существующую схему слоев из одного проекта моделирования в другой проект моделирования или в другое местоположение в решении. Это позволит сохранить ссылки из исходной схемы при изменении схемы. Кроме того, это может привести к тому, что проверка схемы будет работать неправильно, и к другим потенциальным проблемам, таким как отсутствующие элементы или другие ошибки при попытке открыть схему.
>
> Вместо этого добавьте новую схему слоев в проект моделирования. Скопируйте элементы из исходной схемы в новую схему. Сохраните оба проекта моделирования и новую схему слоев.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Добавление новой схемы слоев в проект моделирования

1. В меню **архитектура** выберите пункт **создать UML или схему слоев**.

2. В разделе **шаблоны**выберите **Схема слоев**.

3. Назовите схему.

4. В окне **Добавить в проект моделирования**найдите и выберите существующий проект моделирования в решении.

     -или-

     Выберите **создать новый проект моделирования** , чтобы добавить в решение новый проект моделирования.

    > [!NOTE]
    > Схема слоя должна существовать внутри проекта моделирования. Однако ее можно связать с элементами в любом месте решения.

5. Убедитесь, что сохранены оба проекта моделирования и схема слоев.

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a> Создание слоев на основе артефактов
 Слои можно создать из элементов решения Visual Studio, таких как проекты, файлы кода, пространства имен, классы и методы. При этом автоматически создаются связи между слоями и элементами, которые включаются в процесс проверки слоев.

 Слои также можно связывать с элементами, которые не поддерживают проверку, такими как документы Word или презентации PowerPoint, чтобы можно было связать слой со спецификациями или планами. Кроме того, слои можно связать с файлами в проектах, которые являются общими для нескольких приложений, но в процесс проверки не войдут слои, которые отображаются с универсальными именами, например "Уровень 1" и "Уровень 2".

 Чтобы проверить, поддерживает ли связанный элемент проверку, откройте **Обозреватель слоев** и просмотрите свойство **Поддержка проверки** элемента. См. раздел [Управление связями с артефактами](#Managing).

|**Чтобы**|**Выполните следующие действия**|
|------------|----------------------------|
|Создать слой для одного артефакта|<ol><li>Перетащите элемент на схему слоев из указанных ниже источников.<br /><br /> <ul><li>**Обозреватель решений**<br /><br />         Например, можно перетаскивать файлы или проекты.</li><li>Карты кода<br /><br />         См. раздел [сопоставление зависимостей в решениях](../modeling/map-dependencies-across-your-solutions.md) и [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Представление классов** или **Обозреватель объектов**</li></ul><br />     Слой отображается на схеме и связан с артефактом.</li><li>Переименуйте слой, чтобы отразить обязанности связанного кода или артефактов.</li></ol> **Важно.**  При перетаскивании двоичных файлов на схему слоев их ссылки на проект моделирования не добавляются автоматически. Необходимо вручную добавить двоичные файлы, которые нужно проверить, в проект моделирования. **Добавление двоичных файлов в проект моделирования** <ol><li>В **Обозреватель решений**откройте контекстное меню проекта моделирования и выберите команду **Добавить существующий элемент**.</li><li>В диалоговом окне **Добавление существующего элемента** перейдите к двоичным файлам, выберите их и нажмите кнопку **ОК**.     Двоичные файлы отображаются в проекте моделирования.</li><li>В **Обозреватель решений**выберите добавленный двоичный файл и нажмите клавишу **F4** , чтобы открыть окно « **Свойства** ».</li><li>Для каждого двоичного файла задайте для свойства **действие сборки** значение **Проверка**.</li></ol>|
|Создание единственного слоя для всех выбранных артефактов|Одновременно перетащите на схему слоев все артефакты.<br /><br /> Слой отображается в схеме и связан со всеми артефактами.|
|Создание слоя для каждого выбранного артефакта|При одновременном перетаскивании всех артефактов в схему слоев нажмите и удерживайте клавишу **SHIFT** . **Примечание.**  Если для выбора диапазона элементов используется клавиша **SHIFT** , отпустите клавишу после выбора артефактов. Нажмите и удерживайте ее снова при перетаскивании артефактов в схему. <br /><br /> Слой для каждого артефакта отображается в схеме и связан с каждым артефактом.|
|Добавление артефакта в слой|Перетащите артефакт в слой.|
|Создание нового несвязанного слоя|На **панели элементов**разверните раздел **Схема слоев** , а затем перетащите **слой** на схему слоев.<br /><br /> Чтобы добавить несколько слоев, дважды щелкните средство. По завершении выберите инструмент **указатель** или нажмите клавишу **ESC** .<br /><br /> — или —<br /><br /> Откройте контекстное меню схемы слоев, выберите **Добавить**, а затем выберите **слой**.|
|Создание вложенных слоев|Перетащите существующий слой в другой слой.<br /><br /> — или —<br /><br /> Откройте контекстное меню слоя, выберите **Добавить**, а затем выберите **слой**.|
|Создание нового слоя, который содержит два или более существующих слоев|Выберите слои, откройте контекстное меню для выбранного элемента и выберите **Группа**.|
|Изменение цвета слоя|Задайте для свойства **Цвет** значение нужного цвета.|
|Указание, что артефакт, связанный со слоем, не должен более принадлежать указанному пространству имен|Введите пространства имен в свойстве **Запрещенные пространства имен** слоя. Для разделения пространств имен используйте точку с запятой (**;**).|
|Указание, что артефакт, связанный со слоем, не может зависеть от указанного пространства имен|Введите пространства имен в свойстве " **Запрещенные зависимости пространства имен** слоя". Для разделения пространств имен используйте точку с запятой (**;**).|
|Указание, что артефакт, связанный со слоем, должен принадлежать одному из указанных пространств имен|Введите пространство имен в свойстве **обязательные пространства имен** слоя. Для разделения пространств имен используйте точку с запятой (**;**).|

 Число на слое обозначает количество артефактов, связанных со слоем. Однако при считывании этого числа учитывайте следующее.

- Если слой связан с артефактом, содержащим другие артефакты, но слой не связан с другими артефактами напрямую, то число включает только связанный артефакт. Однако для анализа в ходе проверки слоя включаются другие артефакты.

     Например, если слой связан с одним пространством имен, то число связанных артефактов равно 1, даже если пространство имен содержит классы. Если слой также связан с каждым классом в пространстве имен, то число будет включать эти связанные классы.

- Если слой содержит другие слои, связанные с артефактами, то слой-контейнер также связан с этими артефактами, даже если число в слое-контейнере не включает эти артефакты.

## <a name="manage-links-between-layers-and-artifacts"></a><a name="Managing"></a> Управление связями между слоями и артефактами

1. На схеме слоев откройте контекстное меню слоя и выберите **Просмотреть ссылки**.

     **Обозреватель слоев** отображает ссылки артефактов для выбранного слоя.

2. Для управления этими ссылками можно использовать следующие задачи:

|**Чтобы**|**В обозревателе слоев**|
|------------|---------------------------|
|Удалить ссылку между слоем и артефактом|Откройте контекстное меню для ссылки артефакт и выберите команду **Удалить**.|
|Переместить ссылку из одного слоя в другой|Перетащите ссылку артефакта в существующий слой на схеме.<br /><br /> — или —<br /><br /> 1. Откройте контекстное меню для ссылки артефакт, а затем выберите **Вырезать**.<br />2. на схеме слоев откройте контекстное меню слоя и выберите команду **Вставить**.|
|Скопировать ссылку из одного слоя в другой|1. Откройте контекстное меню для ссылки артефакта и выберите команду **Копировать**.<br />2. на схеме слоев откройте контекстное меню слоя и выберите команду **Вставить**.|
|Создать новый слой из существующей ссылки артефакта|Перетащите ссылку артефакта в пустую область на схеме.|
|Убедитесь, что связанный артефакт поддерживает проверку относительно схемы слоев.|Просмотрите столбец **Поддержка проверки** для ссылки артефакт.|

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a> Реконструировать существующие зависимости
 Зависимости существуют там, где артефакт, связанный с одним слоем, ссылается на артефакт, связанный с другим слоем. Например, класс в одном слое объявляет переменную, которая имеет класс в другом слое. Реконструировать существующие зависимости можно для артефактов, связанных со слоями в схеме.

> [!NOTE]
> Для определенных видов артефактов реконструировать зависимости невозможно. Например, зависимости не могут быть реконструированы из или в слой, связанный с текстовым файлом. Чтобы узнать, какие артефакты имеют зависимости, которые можно реконструировать, откройте контекстное меню для одного или нескольких слоев, а затем выберите **Просмотреть ссылки**. В **обозревателе слоев**изучите столбец **поддерживает проверку** . Зависимости не будут реконструированы для артефактов, для которых в этом столбце указано **значение false**.

- Выберите один или несколько слоев, откройте контекстное меню для выбранного слоя, а затем выберите **создать зависимости**.

  Как правило, на этом этапе можно увидеть некоторые зависимости, которых быть не должно. Эти зависимости можно изменить для соответствия предполагаемой структуре.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a> Изменение слоев и зависимостей для отображения предполагаемого дизайна
 Чтобы описать изменения, которые планируется внести в систему или предполагаемую архитектуру, измените схему слоев.

|**Чтобы**|**Выполните следующие действия**|
|------------|-----------------------------|
|Изменить или ограничить направление зависимости|Задайте свойство **Direction** .|
|Создать новые зависимости|Используйте средства **зависимости** и **двунаправленной зависимости** .<br /><br /> Чтобы нарисовать несколько зависимостей, дважды щелкните средство. По завершении выберите инструмент **указатель** или нажмите клавишу **ESC** .|
|Указание, что артефакт, связанный со слоем, не может зависеть от указанного пространства имен|Введите пространства имен в свойстве " **Запрещенные зависимости пространства имен** слоя". Для разделения пространств имен используйте точку с запятой (**;**).|
|Указание, что артефакт, связанный со слоем, не должен более принадлежать указанному пространству имен|Введите пространства имен в свойстве **Запрещенные пространства имен** слоя. Для разделения пространств имен используйте точку с запятой (**;**).|
|Указание, что артефакт, связанный со слоем, должен принадлежать одному из указанных пространств имен|Введите пространство имен в свойстве **обязательные пространства имен** слоя. Для разделения пространств имен используйте точку с запятой (**;**).|

## <a name="change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a> Изменение отображения элементов на схеме
 Можно изменить размер, фигуру, цвет, положение слоев или цвет зависимостей, изменив их свойства.

## <a name="discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a> Обнаружение шаблонов и зависимостей на карте кода
 При создании схем слоев вы также можете создавать **карты кода**. Они помогают обнаружить закономерности и зависимости при анализе кода. Воспользуйтесь обозревателем решений, представлением классов или обозревателем объектов, чтобы изучить сборки, пространства имен и классы, которые часто находятся в точном соответствии с существующими слоями. Подробнее о картах кода читайте в следующих разделах:

- [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)

- [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)

- [Поиск потенциальных проблем с помощью анализаторов карт кода](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>См. также:
 [Видео на канале 9. Разработка и проверка архитектуры с помощью](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture) схем слоев схемы слоев [: эталонные](../modeling/layer-diagrams-reference.md) [схемы слоев: рекомендации](../modeling/layer-diagrams-guidelines.md) [Проверка кода с помощью схем слоев](../modeling/validate-code-with-layer-diagrams.md) [Визуализация кода](../modeling/visualize-code.md)
