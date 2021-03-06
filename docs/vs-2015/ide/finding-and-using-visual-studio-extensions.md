---
title: Поиск и использование расширений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
caps.latest.revision: 47
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: df6219a66b0f6c85e197b209741706abc7ce3d06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655878"
---
# <a name="finding-and-using-visual-studio-extensions"></a>Поиск и использование расширений Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Расширения Visual Studio — это пакеты кода, которые выполняются в Visual Studio и предоставляют новые или улучшенные функции Visual Studio. Дополнительные сведения о расширениях Visual Studio см. здесь: [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

 С помощью диалогового окна **Расширения и обновления** можно установить расширения и примеры Visual Studio с веб-сайтов и из других источников, а затем включить, отключить, обновить или удалить их. (**Сервис/расширения и обновления**, или введите **Расширения** в окне **Быстрый запуск** ). В диалоговом окне также показаны обновления для установленных образцов и расширений. Можно также загрузить расширения с веб-сайтов или получить их у других разработчиков.

> [!NOTE]
> Начиная с Visual Studio 2015, расширения, размещенные в коллекции Visual Studio, будут обновляться автоматически.  Этот параметр можно изменить с помощью диалогового окна **Расширения и обновления** .  Дополнительные сведения см. в разделе **Автоматическое обновление расширений** .

## <a name="finding-visual-studio-extensions"></a>Поиск расширений Visual Studio
 Расширения можно установить из [Visual Studio Marketplace](https://marketplace.visualstudio.com/) или из [коллекции примеров](https://code.msdn.microsoft.com/vstudio) на веб-сайте Майкрософт. К числу расширений относятся элементы управления, примеры, шаблоны, инструменты или другие компоненты, расширяющие возможности Visual Studio. Visual Studio поддерживает расширения в формате VSIX: шаблоны проектов, шаблоны элементов, элементы для **панели элементов** , компоненты MEF и пакеты VSPackage. Кроме того, можно загрузить и установить расширения на основе MSI, однако их будет невозможно включить или отключить в диалоговом окне **Расширения и обновления** . Коллекция Visual Studio содержит расширения VSIX и MSI.

## <a name="installing-or-uninstalling-visual-studio-extensions"></a>Установка и удаление расширений Visual Studio
 В разделе **Расширения и обновления**найдите нужное расширение для установки. (Если известно имя или часть имени расширения, можно выполнить поиск в окне **Поиск в галерее Visual Studio** .) Нажмите кнопку **скачать**, а затем — **установить**. Для загрузки расширения необходимо перезапустить Visual Studio.

 При попытке установить расширение, имеющее зависимости, то установщик проверяет, установлены ли эти зависимости. Если они не установлены, то диалоговое окно **Расширения и обновления** отображает список зависимостей, которые требуется установить перед установкой данного расширения.

 Если требуется прекратить использование расширения, его можно отключить или удалить. Отключенное расширение сохранится, но не будет загружаться. Можно отключить только расширения VSIX; расширения, которые были установлены с помощью MSI, можно только удалить. Найдите расширение и щелкните **Удалить** или **Отключить**. Чтобы выгрузить отключенное расширение, необходимо перезапустить Visual Studio.

## <a name="per-user-and-administrative-extensions"></a>Расширения на уровне пользователя и администратора
 Большинство расширений подлежат установке на уровне пользователя и устанавливаются в папку **%LocalAppData%\Microsoft\VisualStudio\\<версия_Visual_Studio\>\Extensions\\**. Несколько расширений являются административными расширениями и устанавливаются в папку ** \<Visual Studio installation folder> \Common7\IDE\Extensions \\ **

 Чтобы защитить систему от расширений, которые могут содержать ошибки или вредоносный код, можно ограничить расширения на уровне пользователя, чтобы они загружались только при запуске Visual Studio под учетной записью пользователя со стандартными правами. Это означает, что расширения на уровне пользователя отключаются при запуске Visual Studio с правами администратора. Для этого перейдите на страницу параметров **Расширения и обновления** (выберите**Сервис/параметры**, **Среда**, **Расширения и обновления**или просто введите **Расширение** в окне **Быстрый запуск** ). Снимите флажок **Загрузить расширения для пользователей при запуске с правами администратора** и перезапустите Visual Studio.

## <a name="automatic-extension-updates"></a>Автоматическое обновление расширений
 Пользовательские расширения обновляются автоматически при появлении новой версии в коллекции Visual Studio.  Новая версия расширения обнаруживается и устанавливается в фоновом режиме и при следующей перезагрузке Visual Studio будет выполняться новая версия расширения.

 Автоматическое обновление поддерживается только для пользовательских расширений.  Административные расширения, которые устанавливаются для всех пользователей, не будут обновляться, и вам потребуется вручную установить новые версии с помощью диалогового окна **Расширения и обновления** узла **Обновления** . Вы можете увидеть, какие расширения будут автоматически обновляться в области сведений о расширении диалогового окна **расширения и обновления** .

 Функцию автоматического обновления можно отключить для всех или только определенных расширений.

- Чтобы отключить автоматическое обновление для всех расширений, щелкните ссылку **Изменить параметры расширений и обновлений** в диалоговом окне **Расширения и обновления** и снимите флажок **Автоматически обновлять расширения**.

- Чтобы отключить автоматическое обновление для определенного расширения, снимите флажок **автоматически обновлять это расширение** в области сведений о расширении в правой части диалогового окна **расширения и обновления** .

> [!NOTE]
> Начиная с Visual Studio 2015 с обновлением 2, можно указать (**Инструменты / Параметры / Среда / Расширения и обновления**) необходимость автоматических обновлений для расширений на уровне пользователя, расширений для всех пользователей или и то, и другое (значение по умолчанию).

## <a name="sample-master-copies-and-working-copies"></a>Контрольные и рабочие экземпляры
 При установке примера из сети решение сохраняется в двух местоположениях:

- Рабочий экземпляр сохраняется в местоположении, которое вы укажете в диалоговом окне **Создать проект** .

- Отдельный контрольный экземпляр сохраняется на компьютере.

  С помощью диалогового окна **Расширения и обновления** можно выполнить следующие задачи, связанные с примерами.

- Отобразить список контрольных экземпляров установленных образцов.

- Отключить или удалить контрольный экземпляр образца.

- Установить пакеты примеров — коллекции примеров, связанных с определенной технологией или функцией.

- Установить отдельные примеры из сети. (Для этого также можно использовать диалоговое окно **Создать проект** .)

- Просмотреть уведомления об обновлениях, когда будут опубликованы изменения в исходном коде для установленных примеров.

- Обновить контрольный экземпляр установленного примера при получении уведомления об обновлении.

## <a name="installing-without-using-the-extensions-and-updates-dialog-box"></a>Установка без применения диалогового окна "Расширения и обновления"
 Расширения, упакованные в VSIX-файлы, могут быть доступны не только в коллекции Visual Studio. Несмотря на то что эти файлы не обнаруживаются в диалоговом окне **Расширения и обновления** , VSIX-файл можно установить, дважды щелкнув его или выбрав файл и нажав клавишу «ВВОД». После этого следуйте инструкциям. После установки данное расширение можно будет включить, отключить или удалить в диалоговом окне **Расширения и обновления** .

## <a name="extension-types-not-supported-by-the-extensions-and-updates-dialog-box"></a>Типы расширений, которые не поддерживаются в диалоговом окне «Расширения и обновления»
 Visual Studio продолжает поддерживать расширения, установленные с помощью установщика Microsoft (MSI), но не в диалоговом окне **Расширения и обновления** без модификаций.

> [!TIP]
> Если расширение MSI содержит файл extension.vsixmanifest, это расширение отобразится в диалоговом окне **Расширения и обновления** .
