---
title: Сохранение данных с помощью методов DBDirect адаптера таблицы | Документация Майкрософт
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce987f5ef90448c41da45a39c62710b968e11199
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655424"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>Сохранение данных с помощью методов DBDirect адаптера таблицы TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве содержатся подробные инструкции по выполнению инструкций SQL непосредственно в базе данных с помощью методов DBDirect адаптера таблицы. Методы DBDirect адаптера таблицы обеспечивают точный контроль над обновлениями базы данных. Их можно использовать для выполнения определенных инструкций SQL и хранимых процедур, вызывая отдельные `Insert` `Update` методы, и в `Delete` соответствии с требованиями приложения (в отличие от перегруженного `Update` метода, который ВЫПОЛНЯЕТ инструкции UPDATE, INSERT и DELETE в одном вызове).

 В этом пошаговом руководстве описаны следующие процедуры.

- Создайте новое **приложение Windows**.

- Создание и настройка набора данных с помощью [мастера настройки источника данных](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Выбор элемента управления, создаваемого на форме при перетаскивании элементов из окна **Источники данных**. Дополнительные сведения см. в разделе [Установка элемента управления, создаваемого при перетаскивании из окна Источники данных](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Создание формы с привязкой к данным посредством перетаскивания элементов из окна **Источники данных** на форму.

- Добавьте методы для прямого доступа к базе данных и выполнения операций вставки, обновления и удаления.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения данного пошагового руководства требуется:

- Доступ к примеру базы данных "Борей".

## <a name="create-a-windows-application"></a>Создание приложения Windows
 Первым шагом является создание **приложения Windows**.

#### <a name="to-create-the-new-windows-project"></a>Порядок создания нового проекта Windows

1. В Visual Studio в меню **файл** создайте новый **проект**.

2. Назовите проект **таблеадаптердбдиректмесодсвалксраугх**.

3. Выберите **приложение Windows**и нажмите кнопку **ОК**. Дополнительные сведения см. в разделе [Client Applications](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Создается проект **TableAdapterDbDirectMethodsWalkthrough**, который добавляется в **Обозреватель решений**.

## <a name="create-a-data-source-from-your-database"></a>Создание источника данных из базы данных
 В этом шаге **Мастер настройки источника данных** используется для создания источника данных на основе таблицы `Region` в учебной базе данных "Борей". Для создания подключения необходимо иметь доступ к учебной базе данных "Борей".

#### <a name="to-create-the-data-source"></a>Создание источника данных

1. В меню **данные** выберите команду **отобразить источники данных**.

2. В окне **Источники данных** выберите **Добавить новый источник данных** , чтобы запустить **Мастер настройки источника данных**.

3. На экране **Выбор типа источника данных** выберите **база данных**, а затем нажмите кнопку **Далее**.

4. На экране **Выбор подключения к данным** выполните одно из следующих действий.

    - Если подключение к учебной базе данных Northwind доступно в раскрывающемся списке, то выберите его.

         -или-

    - Выберите **Новое подключение** для открытия диалогового окна **Добавить/изменить подключение**.

5. Если базе данных требуется пароль, выберите параметр, чтобы включить конфиденциальные данные, а затем нажмите кнопку **Далее**.

6. На экране **сохранить строку подключения в файле конфигурации приложения** нажмите кнопку **Далее**.

7. На экране **Выбор объектов базы данных** разверните узел **таблицы** .

8. Выберите `Region` таблицу и нажмите кнопку **Готово**.

     Объект **NorthwindDataSet** добавляется в проект, и таблица `Region` отображается в окне **Источники данных**.

## <a name="addcontrols-to-the-form-to-display-the-data"></a>Аддконтролс в форму для вывода данных
 Создайте элементы управления с привязкой к данным с помощью перетаскивания элементов из окна **Источники данных** на форму.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Создание элементов управления с привязкой к данным в форме Windows Forms

- Перетащите узел главного **региона** из окна **Источники данных** на форму.

     На форме появляется элемент <xref:System.Windows.Forms.DataGridView> и панель инструментов (<xref:System.Windows.Forms.BindingNavigator>) для перемещения по записям. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md) <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> В области компонентов появятся NorthwindDataSet, регионтаблеадаптер, и.

#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>Порядок добавления кнопок, вызывающих отдельные методы DbDirect адаптера таблицы

1. Перетащите три элемента управления <xref:System.Windows.Forms.Button> из **области элементов** на **Form1** (под **RegionDataGridView**).

2. Задайте следующие свойства **Имя** и **Текст** для каждой из кнопок.

    |Имя|Текст|
    |----------|----------|
    |`InsertButton`|**Insert**|
    |`UpdateButton`|**Update**|
    |`DeleteButton`|**Удаление**|

#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>Добавление кода для вставки новых записей в базу данных

1. Выберите **инсертбуттон** , чтобы создать обработчик событий для события Click и открыть форму в редакторе кода.

2. Замените обработчик событий `InsertButton_Click` следующим кодом:

     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]

#### <a name="to-add-code-to-update-records-in-the-database"></a>Добавление кода для обновления записей в базе данных

1. Дважды щелкните **UpdateButton**, чтобы создать обработчик событий для события щелчка кнопкой мыши и открыть форму в редакторе кода.

2. Замените обработчик событий `UpdateButton_Click` следующим кодом:

     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]

#### <a name="to-add-code-to-delete-records-from-the-database"></a>Добавление кода для удаления записей из базы данных

1. Выберите **делетебуттон** , чтобы создать обработчик событий для события Click и открыть форму в редакторе кода.

2. Замените обработчик событий `DeleteButton_Click` следующим кодом:

     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]

## <a name="run-the-application"></a>Запуск приложения

#### <a name="to-run-the-application"></a>Запуск приложения

- Нажмите **клавишу F5** , чтобы запустить приложение.

- Нажмите кнопку **Вставить** и убедитесь, что новая запись появилась в сетке.

- Нажмите кнопку **Обновить** и убедитесь, что запись обновлена в сетке.

- Нажмите кнопку **Удалить** и убедитесь, что запись удалена из сетки.

## <a name="next-steps"></a>Next Steps
 В зависимости от требований приложения существует несколько шагов, которые, возможно, потребуется выполнить после создания формы с привязкой к данным. Ниже приводится перечень рекомендаций, позволяющих улучшить полученный результат.

- Добавление функциональности поиска в форму. Дополнительные сведения см. в разделе [инструкции. Добавление параметризованного запроса в приложение Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Добавление дополнительных таблиц в набор данных посредством выбора элемента **Настроить набор данных с помощью мастера** в окне **Источники данных**. Вы можете добавить элементы управления, отображающие связанные данные, перетащив связанные узлы на форму.

## <a name="see-also"></a>См. также:
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
