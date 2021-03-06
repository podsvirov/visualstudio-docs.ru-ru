---
title: Создание простой службы WCF в Windows Forms
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7b0c874509622b34d7a9703a6b31481e0d88e586
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036799"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Пошаговое руководство. Создание простой службы WCF в Windows Forms

В этом пошаговом руководстве показано, как создать простую службу Windows Communication Foundation (WCF), проверить ее, а затем получить к ней доступ из Windows Forms приложения.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Создание службы

1. Запустите Visual Studio.

::: moniker range="vs-2017"

2. В меню **Файл** щелкните **Создать** > **Проект**.

3. В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C#** и выберите **WCF**, а затем — **библиотеку служб WCF**.

4. Чтобы создать проект, нажмите кнопку **ОК** .

   ![Проект библиотеки служб WCF](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. На начальном экране выберите **Создать проект**.

3. Введите **библиотеку служб WCF** в поле поиска на странице **Создание нового проекта** . Выберите шаблон C# или Visual Basic для **библиотеки службы WCF**, а затем нажмите кнопку **Далее**.

   ![Создание нового проекта библиотеки службы WCF в Visual Studio 2019](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Если шаблоны не отображаются, может потребоваться установить компонент **Windows Communication Foundation** Visual Studio. Выберите **установить дополнительные инструменты и компоненты** , чтобы открыть Visual Studio Installer. Перейдите на вкладку **отдельные компоненты** , прокрутите вниз до пункта **действия разработки**, а затем выберите **Windows Communication Foundation**. Нажмите кнопку **Изменить**.

4. На странице **Настройка нового проекта** нажмите кнопку **создать**.

::: moniker-end

   > [!NOTE]
   > Будет создана работающая служба, которую можно протестировать и использовать. Следующие два действия демонстрируют, как можно изменить метод по умолчанию для использования другого типа данных. В реальном приложении необходимо также добавить к службе ее специальные функции.

5. В **Обозреватель решений**дважды щелкните **IService1. vb** или **IService1.CS**.

   ![Файл IService1](../data-tools/media/wcf2.png)

   Найдите следующую строку:

   [!code-csharp[WCFWalkthrough#4](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.cs)]
   [!code-vb[WCFWalkthrough#4](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_1.vb)]

   Измените тип `value` параметра на String:

   [!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.cs)]
   [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_2.vb)]

   В приведенном выше коде обратите внимание на атрибуты `<OperationContract()>` или `[OperationContract]` . Эти атрибуты обязательны для любого метода, предоставляемого службой.

6. В **Обозреватель решений**дважды щелкните **Service1. vb** или **Service1.CS**.

   ![Файл Service1](../data-tools/media/wcf3.png)

   Найдите следующую строку:

   [!code-vb[WCFWalkthrough#5](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.vb)]
   [!code-csharp[WCFWalkthrough#5](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_3.cs)]

   Измените тип `value` параметра на String:

   [!code-csharp[WCFWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.cs)]
   [!code-vb[WCFWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_4.vb)]

## <a name="test-the-service"></a>Тестирование службы

1. Нажмите клавишу **F5**, чтобы запустить службу. Откроется форма **тестового клиента WCF** , которая загружает службу.

2. В форме **Тестовый клиент WCF** дважды щелкните метод **GetData()** в разделе **IService1**. Откроется вкладка **GetData** .

     ![Метод&#40;&#41; GetData](../data-tools/media/wcf4.png)

3. В диалоговом окне **Запрос** выберите поле **Значение** и введите `Hello`.

     ![Поле значения](../data-tools/media/wcf5.png)

4. Нажмите кнопку **Вызвать**. Если появится диалоговое окно " **предупреждение системы безопасности** ", нажмите кнопку **ОК**. Результат отобразится в поле **ответ** .

     ![Результат в поле "Ответ"](../data-tools/media/wcf6.png)

5. В меню **Файл** щелкните **Выход**, чтобы закрыть тестовую форму.

## <a name="access-the-service"></a>Доступ к службе

### <a name="reference-the-wcf-service"></a>Ссылка на службу WCF

1. В меню **файл** выберите команду **Добавить** , а затем — **Новый проект**.

2. В диалоговом окне **Новый проект** разверните узел **Visual Basic** или **Visual C#** , выберите пункт **Windows**, а затем выберите **Windows Forms приложение**. Нажмите кнопку **ОК**, чтобы открыть проект.

     ![Проект приложения Windows Forms](../data-tools/media/wcf7.png)

3. Щелкните правой кнопкой мыши **WindowsApplication1** и выберите команду **Добавить ссылку на службу**. Откроется диалоговое окно **Добавить ссылку на службу**.

4. В диалоговом окне **Добавление ссылки на службу** выберите **Найти**.

     ![Добавить ссылку на службу - диалоговое окно](../data-tools/media/wcf8.png)

     **Service1** отображается в области **службы** .

5. Нажмите кнопку **ОК**, чтобы добавить ссылку на службу.

### <a name="build-a-client-application"></a>Создайте клиентское приложение

1. В **Обозревателе решений** дважды щелкните **Form1.vb** или **Form1.cs**, чтобы открыть конструктор Windows Forms, если он еще не открыт.

2. Из **Панели элементов** перетащите на форму элемент управления `TextBox`, элемент управления`Label` и элемент управления `Button`.

     ![Добавление элементов управления на форму](../data-tools/media/wcf9.png)

3. Дважды щелкните `Button` и добавьте следующий код в обработчик событий `Click`:

     [!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.cs)]
     [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-simple-wcf-service-in-windows-forms_5.vb)]

4. В **Обозревателе решений** щелкните правой кнопкой мыши **WindowsApplication1** и выберите команду **Назначить запускаемым проектом**.

5. Нажмите клавишу **F5** , чтобы запустить проект. Введите любой текст и нажмите кнопку. На этой метке отображается введенный текст:.

     ![Форма с результатом](../data-tools/media/wcf10.png)

## <a name="see-also"></a>См. также раздел

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
