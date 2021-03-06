---
title: Шаблоны элементов для проектов Python
description: Список ссылок на шаблоны элементов для проектов Python доступны при выборе пунктов Добавить > Новый элемент в Visual Studio.
ms.date: 12/06/2018
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 528606356c2d976de71ab2c0317a1a0236d2e63f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533397"
---
# <a name="python-item-templates"></a>Шаблоны элементов Python

Шаблоны элементов можно найти в проектах Python, последовательно выбрав **Проект** > **Добавить новый элемент** (в меню) или **Добавить** > **Новый элемент** (в контекстном меню) **обозревателя решений**.

![Диалоговое окно "Добавление нового элемента"](media/project-item-templates.png)

Используя имя, присвоенное элементу, шаблон обычно создает один или несколько файлов и папок в текущей выбранной папке проекта (щелкнув правой кнопкой мыши папку, можно открыть контекстное меню, и папка будет выбрана автоматически). Добавляемый элемент включается в проект Visual Studio и появляется в **обозревателе решений**.

В следующей таблице кратко описывается назначение каждого шаблона элемента в проекте Python:

| Шаблон | С помощью этого шаблона создается |
| --- | --- |
| **Пустой файл Python** | Пустой файл с расширением *.py*. |
| **Класс Python** | Файл *.py* с одним определением пустого класса Python. |
| **Пакет Python** | Папка, которая содержит файл *\_\_init\_\_.py*. |
| **Модульный тест Python** | Файл *.py* с одним модульным тестом на основе платформы `unittest` и вызовом `unittest.main()` для выполнения тестов в файле. |
| **Страница HTML** | Файл *.html* с простой структурой страницы, состоящей из элементов `<head>` и `<body>`. |
| **JavaScript** | Пустой файл *.js*. |
| **Таблица стилей** | Файл *.css* с пустым стилем для `body`. |
| **Текстовый файл** | Пустой файл *.txt*. |
| **Приложение Django 1.9**<br/>**Приложение Django 1.4** | Папка с именем приложения, которая содержит основные файлы приложения, как описано в [шаге 2.2 руководства по изучению Django в Visual Studio](learn-django-in-visual-studio-step-02-create-an-app.md#step-2-1-create-an-app-with-a-default-structure) (для Django 1.9). Для Django 1.4 не включаются папка *migration*, файлы *admin.py* и *apps.py*. |
| **Окно WPF IronPython** | Окно WPF содержит два расположенных рядом файла: *.xaml*, который определяет `<Window>` с пустым элементом `<Grid>`, и связанного с ним файла *.py*, который загружает файл XAML с помощью библиотеки `wpf`. Обычно используется в проекте, созданном с помощью одного из шаблонов проектов IronPython. См. статью [о шаблонах проектов](managing-python-projects-in-visual-studio.md#project-templates) в руководстве по управлению проектами Python. |
| **Вспомогательные файлы веб-роли** | Папка *bin* в корневом каталоге проекта (независимо от выбранной папки в проекте). Эта папка содержит скрипт развертывания по умолчанию и файл *web.config* для веб-ролей облачной службы Azure. Кроме того, шаблон включает файл *readme.html* с дополнительной информацией. |
| **Вспомогательные файлы рабочей роли** | Папка *bin* в корневом каталоге проекта (независимо от выбранной папки в проекте). Эта папка содержит скрипт развертывания и запуска по умолчанию, а также файл *web.config* для рабочих ролей облачной службы Azure. Кроме того, шаблон включает файл *readme.html* с дополнительной информацией. |
| **Файл web.config для Azure (FastCGI)** | Файл *web.config* с записями для приложений, использующих объект [WSGI](https://wsgi.readthedocs.io/en/latest/) для обработки входящих подключений. Этот файл обычно развертывается в корневом каталоге веб-сервера под управлением служб IIS. Дополнительные сведения см. в статье [Настройка веб-приложений Python для IIS](configure-web-apps-for-iis-windows.md). |
| **Файл web.config для Azure (HttpPlatformHandler)** | Файл *web.config* с записями для приложений, которые ожидают передачи данных по входящим подключениям в сокете. Этот файл обычно развертывается в корневом каталоге веб-сервера под управлением служб IIS, таких как служба приложений Azure. Дополнительные сведения см. в статье [Настройка веб-приложений Python для IIS](configure-web-apps-for-iis-windows.md). |
| **Файл web.config для статических файлов Azure** | Файл *web.config*, который обычно добавляется в папку *static* (или другую папку со статическими элементами) для отключения обработки этой папки в Python. Этот файл конфигурации используется совместно с одним из файлов конфигурации FastCGI или HttpPlatformHandle, указанных выше. Дополнительные сведения см. в статье [Настройка веб-приложений Python для IIS](configure-web-apps-for-iis-windows.md). |
| **Файл web.config для удаленной отладки Azure** | Нерекомендуемый (использовался для удаленной отладки в "Службе приложений Azure" для Windows, которая больше не поддерживается). |

## <a name="see-also"></a>См. также раздел

- [Руководство по управлению проектами Python. Шаблоны проектов](managing-python-projects-in-visual-studio.md#project-templates)
- [Шаблоны проекта веб-приложений Python](python-web-application-project-templates.md)
- [Публикация в службу приложений Azure](publishing-python-web-applications-to-azure-from-visual-studio.md)
