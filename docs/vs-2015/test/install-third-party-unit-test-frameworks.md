---
title: Установка платформ модульного тестирования сторонних поставщиков | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bd087dc0b06cbf8ffe4c08f84d819e8ef1c2f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660515"
---
# <a name="install-third-party-unit-test-frameworks"></a>Установка платформ модульного тестирования сторонних поставщиков
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обозреватель тестов Visual Studio может запускать любую платформу модульного тестирования, разработавшую интерфейс адаптера для обозревателя. Программа установки платформы устанавливает двоичные файлы и добавляет шаблоны проекта Visual Studio для поддерживаемых языков. При создании проекта с шаблоном платформа регистрируется с помощью обозревателя тестов. Решение Visual Studio может содержать проекты модульного тестирования, которые используют разные платформы, предназначенные для разных языков. Обозреватель тестов выполняет их все.

 **Требования**

- Visual Studio Enterprise, Visual Studio Professional

## <a name="acquiring-third-party-frameworks"></a>Приобретение сторонних платформ
 Вы можете скачать и установить множество сторонних платформ модульного тестирования, используя диспетчер расширений Visual Studio, или сделать это в коллекции Visual Studio на веб-сайте MSDN. Платформы можно также скачать с других сайтов, например с веб-сайта платформы.

### <a name="installing-from-visual-studio"></a>Установка из Visual Studio

1. Выберите **Сервис** в стандартном меню, а затем **Расширения и обновления**.

2. Разверните узел **В сети**, **Галерея Visual Studio**, **Сервис**. Выберите **Тестирование**.

3. Откройте список, чтобы найти платформу.

4. Выберите платформу и нажмите кнопку **Скачать**.

   Дополнительные сведения см. в разделе [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Установка из Интернета
 Если вы знаете интересующую вас платформу:

1. Откройте [Visual Studio Marketplace](https://marketplace.visualstudio.com).

2. Введите имя платформы в поле **Найти**.

3. Выберите платформу в списке результатов, чтобы перейти на страницу "Коллекция Visual Studio" инструмента.

   Чтобы открыть список платформ с другими средствами тестирования:

4. Откройте [Visual Studio Marketplace](https://marketplace.visualstudio.com).

5. Нажмите кнопку **Обзор**.

6. В списке **Категория** разверните узел **Сервис** и выберите **Тестирование**.

7. Выберите платформу в списке результатов, чтобы перейти на страницу "Коллекция Visual Studio" инструмента.

## <a name="see-also"></a>См. также:
 [Модульное тестирование кода](../test/unit-test-your-code.md)
