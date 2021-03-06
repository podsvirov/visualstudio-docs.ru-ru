---
title: Создание таблиц подстановок в приложениях WPF | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6816b7465b8a3271ec6ebc0db5046d76e60ec5b3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657424"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Создание таблиц подстановки в приложениях WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Таблица уточняющих запросов* термина (иногда называемая *привязкой уточняющего запроса*) описывает элемент управления, отображающий сведения из одной таблицы данных на основе значения поля внешнего ключа в другой таблице. Таблицу подстановки можно создать, перетащив главный узел родительской таблицы или объекта в окне **Источники данных** на элемент управления, который уже привязан к столбцу или свойству в связанной дочерней таблице.

 Например, рассмотрим таблицу `Orders` в базе данных Sales. Каждая запись в `Orders` таблице включает объект `CustomerID` , указывающий, какой клиент поместил заказ. `CustomerID`— Это внешний ключ, указывающий на запись клиента в `Customers` таблице. При отображении списка заказов из `Orders` таблицы может потребоваться отобразить фактическое имя клиента вместо `CustomerID` . Поскольку имя клиента находится в `Customers` таблице, необходимо создать таблицу подстановки для вывода имени клиента. Таблица подстановки использует `CustomerID` значение в `Orders` записи для перехода по связи и возврата имени клиента.

## <a name="to-create-a-lookup-table"></a>Создание таблицы подстановок

1. Добавьте в проект один из следующих типов источников данных с взаимосвязанными данными:

    - Набор данных или EDM.

    - Служба данных WCF, служба WCF или веб-служба. Дополнительные сведения см. в разделе [как подключиться к данным в службе](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Объекты. Дополнительные сведения см. в разделе [как подключиться к данным в объектах](https://msdn.microsoft.com/library/862fd351-0f4d-4220-9743-6103b87dc24b).

    > [!NOTE]
    > Прежде чем можно будет создать таблицу подстановки, в качестве источника данных для проекта должны существовать две связанные таблицы или объекты.

2. Откройте**конструктор WPF**и убедитесь, что конструктор содержит контейнер, который является допустимым целевым объектом перетаскивания для элементов в окне **Источники данных** .

     Дополнительные сведения о допустимых целевых объектах перетаскивания см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

3. Чтобы открыть окно **Источники данных**, щелкните пункт **Показать источники данных** в меню **Данные**.

4. Разверните узлы в окне **Источники данных** , пока не появится родительская таблица или объект и связанная дочерняя таблица или объект.

    > [!NOTE]
    > Связанная дочерняя таблица или объект — это узел, который отображается как расширяемый дочерний узел в родительской таблице или объекте.

5. Щелкните раскрывающееся меню дочернего узла и выберите **сведения**.

6. Разверните дочерний узел.

7. В дочернем узле щелкните раскрывающееся меню для элемента, связывающего дочерние и родительские данные. (В предыдущем примере это узел **CustomerID** .) Выберите один из следующих типов элементов управления, поддерживающих привязку подстановки:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Если элемент управления **ListBox** или **ListView** не отображается в списке, можно добавить эти элементы управления в список. Дополнительные сведения см. в разделе [Установка элемента управления, создаваемого при перетаскивании из окна Источники данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Любой пользовательский элемент управления, производный от <xref:System.Windows.Controls.Primitives.Selector> .

        > [!NOTE]
        > Сведения о добавлении пользовательских элементов управления в список элементов управления, которые можно выбрать для элементов в окне **Источники данных** , см. в разделе [Добавление пользовательских элементов управления в окно Источники данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Перетащите дочерний узел из окна **Источники данных** на контейнер в конструкторе WPF. (В предыдущем примере дочерний узел является узлом **Orders** .)

     Visual Studio создает код XAML, который создает новые элементы управления с привязкой к данным для каждого перетаскиваемого элемента. XAML также добавляет новый <xref:System.Windows.Data.CollectionViewSource> объект для дочерней таблицы или объекта в ресурсы целевого объекта перетаскивания. Для некоторых источников данных Visual Studio также создает код для загрузки данных в таблицу или объект. Дополнительные сведения см. [в разделе Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

9. Перетащите родительский узел из окна **Источники данных** на созданный ранее элемент управления привязки подстановки. (В предыдущем примере родительским узлом является узел **Customers** ).

     Visual Studio задает некоторые свойства элемента управления для настройки привязки подстановки. В следующей таблице перечислены свойства, изменяемые Visual Studio. При необходимости эти свойства можно изменить в XAML или в окне " **Свойства** ".

    |Свойство|Пояснение к параметру|
    |--------------|----------------------------|
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Это свойство задает коллекцию или привязку, используемые для получения данных, отображаемых в элементе управления. Visual Studio присваивает этому свойству значение <xref:System.Windows.Data.CollectionViewSource> для родительских данных, которые были перенесены в элемент управления.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Это свойство задает путь к элементу данных, отображаемому в элементе управления. Visual Studio устанавливает это свойство в первый столбец или свойство в родительских данных после первичного ключа, имеющего строковый тип данных.<br /><br /> Если необходимо отобразить другой столбец или свойство в родительских данных, измените это свойство на путь другого свойства.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio привязывает это свойство к столбцу или свойству дочерних данных, которые были перенесены в конструктор. Это внешний ключ к родительским данным.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio задает этому свойству путь к столбцу или свойству дочерних данных, которые являются внешним ключом для родительских данных.|

## <a name="see-also"></a>См. также:
 [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) пошаговое руководство по отображению связанных данных в [приложениях WPF](../data-tools/display-related-data-in-wpf-applications.md) [. Отображение связанных данных в приложении WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
