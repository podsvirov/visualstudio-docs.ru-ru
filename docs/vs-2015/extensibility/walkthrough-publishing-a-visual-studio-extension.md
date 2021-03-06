---
title: Опубликовать расширение | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5238274d66296a21e15b47d1a090ab01c1a1299d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201969"
---
# <a name="walkthrough-publishing-a-visual-studio-extension"></a>Пошаговое руководство. Публикация расширения Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Примечание**. коллекция Visual Studio заменяется Visual Studio Marketplace. Дополнительные сведения см. в последней версии этого раздела.

В этом пошаговом руководстве показано, как опубликовать расширение Visual Studio в коллекции Visual Studio. При добавлении расширения в коллекцию разработчики могут использовать **расширения и обновления** для просмотра новых и обновленных расширений.

## <a name="prerequisites"></a>Предварительные требования
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Создание расширения Visual Studio
 В этом случае мы будем использовать расширение VSPackage по умолчанию, но те же действия допустимы для каждого типа расширения.

1. Создайте пакет VSPackage в C# с именем `TestPublishing` , который содержит команду меню. Дополнительные сведения см. в разделе [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="test-the-extension"></a>Тестирование расширения
 Перед распространением расширения выполните сборку и тестирование, чтобы убедиться, что оно правильно установлено в экспериментальном экземпляре Visual Studio.

1. В Visual Studio запустите отладку. , чтобы открыть экспериментальный экземпляр Visual Studio.

2. В экспериментальном экземпляре перейдите в меню **Сервис** и выберите **Диспетчер расширений**. Расширение Тестпублишинг должно отображаться в центральной области и быть включено.

3. В меню **Сервис** убедитесь, что вы видите команду test.

## <a name="publish-the-extension-to-the-visual-studio-gallery"></a>Публикация расширения в коллекции Visual Studio
 Теперь вы можете опубликовать расширение в галерее Visual Studio.

1. Убедитесь, что вы создали окончательную версию расширения и что она актуальна.

2. В веб-браузере откройте веб-сайт [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

3. В правом верхнем углу щелкните **Вход**.

4. Войдите с помощью своей учетной записи Майкрософт. Если у вас нет учетная запись Майкрософт, вы можете создать его на этом этапе.

5. Щелкните **Отправить**.

6. На **шаге 1: тип расширения**выберите **инструмент** , а затем нажмите кнопку **Далее**.

7. На **шаге 2: upload**можно отправить его непосредственно в коллекцию Visual Studio или просто добавить ссылку на свой веб-сайт. В этом случае выберите **я хочу отправить мой инструмент**. Появится окно **Выбор элемента управления** . Нажмите кнопку **Обзор** , а затем выберите тестпублиш. VSIX в папке \bin\Release проекта. Нажмите кнопку **Далее**.

8. На **шаге 3: основные сведения**отображаются поля из файла Source. extension. vsixmanifest. Выберите соответствующую **категорию** и добавьте **теги** , чтобы помочь пользователям найти ваше расширение. Может потребоваться добавить более подробную сводку и описание (описание должно содержать не менее 280 символов). Оставьте **тип расширения** **не как расширение Майкрософт** и **Категория затрат** в качестве **пробной версии**.

9. Прочтите соглашение об участии в нижней части страницы и установите флажок **я принимаю**.

10. Щелкните **создать публикацию**. Отобразится страница расширения в коллекции Visual Studio с сообщением о том, что страница еще не опубликована.

11. Щелкните **Опубликовать**.

12. Выполните поиск расширения в коллекции Visual Studio. Должно отобразиться список расширения Тестпублиш.

## <a name="install-the-extension-from-the-visual-studio-gallery"></a>Установка расширения из коллекции Visual Studio
 Теперь, когда расширение Опубликовано, установите его в Visual Studio и протестируйте его.

1. В Visual Studio в меню **Сервис** выберите **расширения и обновления**.

2. Щелкните в **сети** и выполните поиск по запросу тестпублиш. Должно отобразиться список расширения Тестпублиш.

3. Щелкните элемент **Загрузить**. После скачивания расширения нажмите кнопку **Установить**.

4. Чтобы завершить установку, перезапустите Visual Studio.

## <a name="removing-the-extension"></a>Удаление расширения
 Расширение можно удалить из коллекции Visual Studio и с компьютера.

#### <a name="to-remove-the-extension-from-the-visual-studio-gallery"></a>Удаление расширения из коллекции Visual Studio

1. Откройте веб-сайт [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

2. В правом верхнем углу щелкните **Мой екстенионс**. Отобразится список для Тестпублиш.

3. Щелкните **Удалить**.

#### <a name="to-remove-the-extension-from-your-computer"></a>Удаление расширения с компьютера

1. В меню **Сервис** Visual Studio выберите пункт **Диспетчер расширений**.

2. Выберите Тестпублиш и нажмите кнопку **Удалить**.

3. Чтобы завершить удаление, перезапустите Visual Studio.
