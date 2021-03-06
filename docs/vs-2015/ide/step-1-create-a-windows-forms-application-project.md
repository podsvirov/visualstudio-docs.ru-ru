---
title: Шаг 1. Создание проекта приложения Windows Forms | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cdba2105c6b8af42d51669e0d1fc8ce49085d513
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851614"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Шаг 1. Создание проекта приложения Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Первый шаг в создании программы для просмотра изображений — это создание проекта приложения Windows Forms.

 ![ссылка на видео](../data-tools/media/playvideo.gif "PlayVideo") Для получения видео-версии этой статьи см. [руководство 1. Создание средства просмотра изображений в Visual Basic-Video 1](https://msdn.microsoft.com/vbasic/gg315352.aspx) или [учебном курсе 1. Создание средства просмотра изображений на C# — видео 1](https://msdn.microsoft.com/vcsharp/gg278409.aspx). Эти видеоролики сняты с использованием более ранней версии Visual Studio, поэтому существуют небольшие различия в некоторых командах меню и других элементах пользовательского интерфейса. Однако концепции и процедуры аналогичны текущей версии Visual Studio.

### <a name="to-create-a-windows-forms-application-project"></a>Создание проекта приложения Windows Forms

1. В строке меню выберите **Файл**, **Создать**, **Проект**. Диалоговое окно должно выглядеть следующим образом.

     ![Диалоговое окно создания проекта](../ide/media/newprojectdialogcallouts.png "невпрожектдиалогкаллаутс") Диалоговое окно «Создание проекта»

2. В списке **Установленные шаблоны** выберите **Visual C#** или **Visual Basic**.

3. В списке шаблонов выберите значок **Приложение Windows Forms**. Назовите новую форму **PictureViewer** и нажмите кнопку **ОК**.

     Visual Studio создает решение для программы. Решение играет роль контейнера для всех проектов и файлов, необходимых программе. Более подробно эти термины поясняются далее в этом учебнике.

4. На следующем рисунке показано, как теперь должен выглядеть интерфейс Visual Studio.

    > [!NOTE]
    > В вашем случае макет окна может отличаться от показанного. Точный макет окна зависит от версии Visual Studio, используемого языка программирования и других факторов. Однако необходимо убедиться, что отображаются все три окна.

     ![Окно интегрированной среды разработки](../ide/media/express-ideoverview-visio.png "Express_IDEOverview_Visio") Окно интегрированной среды разработки

     Интерфейс содержит три окна: главное окно, **Обозреватель решений** и окно **Свойства**.

     Если какое-либо из этих окон отсутствует, восстановите макет окон по умолчанию, выбрав в строке меню **Окно**, **Сбросить макет окна**. Можно также отобразить окна с помощью команд меню. В строке меню выберите **Вид**, **Окно "Свойства"** или **Обозреватель решений**. Если открыты какие-либо другие окна, закройте их с помощью кнопки **Закрыть** (x) в верхнем правом углу.

5. На рисунке показаны следующие окна (по часовой стрелке от левого верхнего угла):

    - **Главное окно**. В этом окне выполняется основная часть работы, например работа с формами и редактирование кода. На рисунке в окне показана форма в редакторе форм. В верхней части окна находятся две вкладки — вкладка **Начальная страница** и вкладка **Form1.cs [Design]**. (В Visual Basic имя вкладки заканчивается на .vb, а не на .cs.)

    - **Окно Обозреватель решений** В этом окне можно просматривать все элементы решения и переходить по ним. Если выбрать файл, содержимое в окне **Свойства** изменится. Если открыть файл кода (с расширением .cs в Visual C# и .vb в Visual Basic), откроется файл кода или конструктор для файла кода. Конструктор — это визуальная поверхность, на которую можно добавлять элементы управления, такие как кнопки и списки. При работе с формами Visual Studio он называется конструктор Windows Forms.

    - **Окно свойств** В этом окне можно изменить свойства элементов, выбранных в других окнах. Например, выбрав форму Form1, можно изменить ее название путем задания свойства **Text**, а также изменить цвет фона путем задания свойства **Backcolor**.

    > [!NOTE]
    > В верхней строке в **обозревателе решений** отображается текст **Решение "PictureViewer" (1 проект)**. Это означает, что Visual Studio автоматически создала для вас решение. Решение может содержать несколько проектов, но пока что вы будете работать с решениями, которые содержат только один проект.

6. В строке меню выберите **Файл**, **Сохранить все**.

     Другой вариант — нажать кнопку **Сохранить все** на панели инструментов, показанной на следующем рисунке.

     ![Кнопка "сохранить все" на панели инструментов](../ide/media/express-iconsaveall.png "Express_IconSaveAll") Кнопка "сохранить все" на панели инструментов

     Visual Studio автоматически заполняет имя папки и имя проекта, а затем сохраняет проект в папке проектов.

### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал

- Чтобы перейти к следующему шагу руководства, см. [Шаг 2. Запуск программы](../ide/step-2-run-your-program.md).

- Чтобы вернуться к обзорному разделу, ознакомьтесь с [руководством 1. Создание средства просмотра изображений](../ide/tutorial-1-create-a-picture-viewer.md).
