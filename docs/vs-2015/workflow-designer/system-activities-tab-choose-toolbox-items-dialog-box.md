---
title: Вкладка System. Activitys, диалоговое окно «элементы панели элементов» | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS
- VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95b2aa636b63523e06e3c931381e4506a0a03bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655168"
---
# <a name="systemactivities-tab-choose-toolbox-items-dialog-box"></a>Вкладка «System.Activities», диалоговое окно «Выбор элементов области элементов»
На этой вкладке диалогового окна **Выбор элементов панели элементов** отображается список [!INCLUDE[wf](../includes/wf-md.md)] доступных действий, шаблонов и элементов. Чтобы отобразить этот список, выберите пункт **Выбор элементов панели элементов** в меню **Сервис** или щелкните правой кнопкой мыши **панель элементов** и выберите **пункт Выбрать элементы** для открытия диалогового окна **Выбор элементов панели элементов** , а затем перейдите на вкладку **System. activitys** . В списке содержатся действия рабочего процесса из сборок System. Activitys, System. ServiceModel. Activity и System. Activitys. Core. Presentation. Однако по умолчанию проверяются только предоставляемые системой действия и действия, добавленные через другие сборки, отображаемые на **панели элементов** . Недавно добавленные действия автоматически проверяются и появляются на **панели элементов** при нажатии кнопки **ОК** в диалоговом окне. Кроме того, эти элементы отображаются на **панели элементов** в новой категории, которая соответствует пространству имен, в котором находится действие, элемент или шаблон.

> [!WARNING]
> При попытке добавить сборку, которая не содержит ни одного действия рабочего процесса, будет выдано сообщение об ошибке.

 Это диалоговое окно не зависит от проекта, поэтому вкладка **System. activitys** будет отображаться в АВТОНОМНОМ коде XAML или в типе проекта без рабочего процесса.

 Фильтрация выполняется на каждой вкладке. Это означает, что невозможно добавить действия рабочего процесса на вкладке **компонент .NET** . Их необходимо добавить на вкладке **System. activitys** .

 Вы можете снять флажки для всех элементов, которые не должны отображаться на **панели элементов** , на этой вкладке диалогового окна. Кроме того, это можно сделать с помощью пункта контекстного меню **Удалить** в **панели элементов** и отмены ссылок на сборку не удаляет элемент из **панели элементов**.

 При создании экземпляра действия перетаскиванием его на конструктор в список сборок автоматически будет добавлена сборка, содержащая этот элемент. Кроме того, если действие ссылается на сборку C, то она не будет добавлена в список ссылок. Сборка C должна находиться в глобальном кэше сборок или в том же каталоге, что и действие б. В изолированном случае сборка должна находиться в глобальном кэше сборок или в пути пробы VS. Только после этого действие можно перетаскивать в рабочей области конструктора рабочих процессов.

 Параметры **панели элементов** сохраняются по умолчанию в качестве параметров пользователя, поэтому при следующем открытии **панели элементов**отображается настроенный список действий рабочего процесса. Один из побочных эффектов этого заключается в том, что если вы добавили определенные элементы домена на **панель элементов** при помощи диалогового окна **Выбор элементов панели элементов** , эти элементы по-прежнему будут отображаться при работе в консольном приложении рабочего процесса. Если вы не хотите видеть их, удалите их с помощью контекстного меню или снимите флажки в диалоговом окне **Выбор элементов панели элементов** , как отмечалось ранее.

 Столбцы в этом диалоговом окне содержат следующую информацию.

 Название перечисляет имена действий рабочего процесса, зарегистрированных в настоящее время на локальном компьютере.

 Пространство имен отображает иерархию пространства имен .NET Framework библиотеки классов, которая определяет структуру действия.

 Имя сборки отображает имя и версию сборки .NET Framework, содержащей действие.

 Каталог отображает расположение сборки .NET Framework, содержащей действия рабочего процесса. По умолчанию все сборки находятся в глобальном кэше сборок.

 Для сортировки списка компонентов следует щелкнуть заголовок любого столбца.