---
title: Система управления версиями TF
description: Подключение к Team Foundation Server или Visual Studio Team Services с использованием системы управления версиями Team Foundation.
author: asb3993
ms.author: amburns
ms.date: 05/03/2018
ms.topic: article
ms.technology: vs-ide-general
ms.assetid: 52D3D26A-4D01-4FD1-AAA1-AE7D7BD39746
ms.openlocfilehash: 58d0fc5c31b02574661f8b86a4ae8bcaf393be3a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693777"
---
# <a name="connecting-to-team-foundation-version-control"></a>Подключение к системе управления версиями Team Foundation 

> [!NOTE]
> **Примечание**. Поддержка управления версиями Team Foundation находится в предварительной стадии, и некоторые функции еще не поддерживаются полностью. Мы будем рады ответить на ваши вопросы на сайте [сообщества разработчиков](https://developercommunity.visualstudio.com/spaces/41/index.html). Планируются дальнейшие обновления.

Visual Studio Team Services (VSTS) и Team Foundation Server (TFS) предоставляют две модели системы управления версиями: Git, которая является распределенной системой управления версиями, и система управления версиями Team Foundation (TFVC), которая является централизованной системой управления версиями. В этой статье представлены общие сведения и отправная точка для использования системы управления версиями Team Foundation в Visual Studio для Mac.

## <a name="requirements"></a>Требования

* Visual Studio для Mac 7.5 или более поздней версии.
* Visual Studio Team Services или Team Foundation Server 2013 и более поздние версии
* Проект в Visual Studio Team Services или Team Foundation Server, настроенный на использование системы управления версиями Team Foundation.

## <a name="installation"></a>Установка

В Visual Studio для Mac выберите в меню **Visual Studio > Расширения...**. На вкладке **Коллекция** выберите **Управление версиями > Управление версиями Team Foundation для TFS и VSTS** и нажмите кнопку **Установить...**:

  ![Диспетчер расширений](media/tfvc-install.png) 

Следуйте инструкциям для установки расширения. После установки перезапустите интегрированную среду разработки.

## <a name="using-the-add-in"></a>Использование надстройки

После установки расширения выберите в меню **Управление версиями > TFS и VSTS > Соединение с системой управления версиями Team Foundation...**. Нажмите кнопку **Добавить** для добавления новой учетной записи: 

![Добавление сервера TFVC](media/tfvc-add-remove-server.png)

Вначале выберите Visual Studio Team Services или Team Foundation Server:

![Соединения с сервером TFVC](media/tfvc-choose-server-type.png)

Введите свои учетные данные и нажмите кнопку **Войти**: 

![Войдите на сервер TFVC](media/tfvc-login.png)

После успешного входа в систему выберите проекты, к которым требуется получить доступ, и нажмите клавишу **ОК**: 

![Выбор проектов](media/tfvc-choose-projects.png)

Выберите пункт меню **Управление версиями > TFS и VSTS > Обозреватель управления исходным кодом**, чтобы открыть обозреватель управления исходным кодом, который позволяет просмотреть исходный код.

> [!IMPORTANT]
> **Известная проблема**. В этом предварительном выпуске при первом открытии обозревателя управления исходным кодом вам потребуется [создать новую рабочую область](#creating-a-new-workspace).

![Проводник источников данных](media/tfvc-source-explorer.png)

Из обозревателя исходного кода можно просмотреть исходный код на сервере и выполнять следующие действия:

- Управлять рабочими областями (создавать, изменять и удалять).
- Перемещаться по структуре проекта.
- Сопоставлять проекты.
- Получать проекты.
- Блокировать и разблокировать файлы.
- Переименовывать файлы.
- Удалять файлы.
- Добавлять новые файлы.
- Извлекать для изменения.
- Возвращать после изменения.
- Просматривать журнал изменений.
- Сравнивать изменения.

## <a name="creating-a-new-workspace"></a>Создание новой рабочей области

В обозревателе управления исходным кодом нажмите кнопку **Управление рабочими областями**. 

![Управление рабочими областями](media/tfvc-manage-workspaces.png)

Для создания рабочей области нажмите кнопку **Добавить**.

![Создание рабочей области](media/tfvc-create-workspace.png)

Укажите имя рабочей области и нажмите кнопку **Добавить рабочую папку**, чтобы привязать к проекту локальную папку на компьютере.

По завершении нажмите кнопку **ОК**, затем закройте диалоговое окно "Управление рабочими областями". Теперь все готово для того, чтобы получить файлы в обозревателе исходного кода и приступить к работе.

## <a name="troubleshooting"></a>Устранение неполадок

### <a name="problems-using-basic-authentication"></a>Проблемы при использовании обычной проверки подлинности

Существует несколько вариантов выполнения проверки подлинности на сервере.

- Oauth
- Basic
- Ntlm

Для использования обычной проверки подлинности необходимо включить **альтернативные учетные данные** в VSTS, выполнив следующие действия.

1. Войдите как владелец учетной записи VSTS (https://{ваша_учетная_запись}.visualstudio.com).
2. В панели инструментов учетной записи выберите значок шестеренки и пункт **Политика**: ![выбран вариант "Параметры политики"](media/tfvc-auth2.png) 
3. Проверьте параметры подключения для приложения. Измените эти параметры в зависимости от политик безопасности: ![выбран вариант "Параметры политики"](media/tfvc-auth.png)  

### <a name="i-do-not-see-anything-in-tfvc"></a>В TFVC ничего не отображается

Для настройки системы управления версиями Team Foundation (TFVC) на компьютере разработки **необходимо** создать рабочую область, как описано в разделе [Создание рабочей области](#creating-a-new-workspace).

В обозревателе управления исходным кодом нажмите кнопку **Управление рабочими областями**. Выполните процедуру по сопоставлению командного проекта с папкой на компьютере разработки.

### <a name="i-do-not-see-any--all-of-my-projects"></a>Я не вижу свои проекты (все или некоторые)

После проверки подлинности вы должны увидеть список проектов. По умолчанию отображаются только проекты TFS. Для просмотра других типов проектов установите флажок "Показать все проекты".

Имейте в виду, что проекты, которые находятся на сервере, не будут отображаться, если у вас нет нужных привилегий.

#### <a name="i-am-getting-the-error-cannot-create-the-workspace-please-try-again"></a>Выводится ошибка "Не удается создать рабочую область. Повторите попытку"

При попытке [создать рабочую область](#creating-a-new-workspace) необходимо убедиться в том, что выполняются следующие условия:

- в имени рабочей области не используются недопустимые символы;
- максимальная длина имени — 64 символа;
- локальный путь не может использоваться другими рабочими областями.