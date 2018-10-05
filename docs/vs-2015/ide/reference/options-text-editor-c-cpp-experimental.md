---
title: Параметры, текстовый редактор, C / C++, экспериментальный | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f6ab69c9b777fc28d1abc02267d9d94a1dca70c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559649"
---
# <a name="options-text-editor-cc-experimental"></a>"Параметры", "Текстовый редактор", C/C++, "Экспериментальный"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [параметры "," Текстовый редактор "," C/C++ "," экспериментальный](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-c-cpp-experimental).  
  
  
Изменяя эти параметры, можно настроить поведение, связанное с IntelliSense и базой данных просмотра, при программировании на языке C или C++.  
  
 Чтобы открыть эту страницу, в диалоговом окне **Параметры** в левой области разверните **Текстовый редактор**, разверните **C/C++** и щелкните **Экспериментальный**.  
  
 Эти функции доступны в версии-кандидате Visual Studio 2015 с обновлением 1.  
  
> [!NOTE]
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. См. раздел [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Обзор и навигация  
 **Включить новое ядро СУБД**  
 Это должно автоматически ускорить заполнение базы данных и все операции с базой данных (без снижения точности), такие как **Перейти к определению** и **Найти все ссылки**. (Чтобы применить изменения, просто закройте и повторно откройте решение. Перезапускать Visual Studio не нужно.)  
  
## <a name="intellisense"></a>IntelliSense  
 **Преобразовать точки в стрелки в списке членов**  
 Заменяет "." на "->" в списке членов, если это применимо.  
  
## <a name="refactoring"></a>Рефакторинг  
 **Включить извлечение функции**  
 Позволяет извлечь выделенный код в отдельную функцию и заменить код на вызов этой новой функции. Чтобы получить доступ к этой возможности, щелкните выделенный код правой кнопкой мыши и выберите пункт **Быстрые действия**или просто нажмите клавиши CTRL+точка [CTRL+.].  
  
 **Включить изменение сигнатуры**  
 Позволяет добавлять, переупорядочивать и удалять параметры функции и применять изменения ко всем местам вызова. Чтобы получить доступ к этой возможности, щелкните правой кнопкой мыши в любом месте, где используется функция, и выберите пункт **Быстрые действия**или просто нажмите клавиши CTRL+точка [CTRL+.].  
  
## <a name="text-editor"></a>Текстовый редактор  
 **Включить развертывание областей**  
 Если этот параметр включен, вы можете заключить выделенный текст в фигурные скобки, введя символ "{" в текстовом редакторе.  
  
 **Включить приоритет развертывания**  
 Если этот параметр включен, вы можете заключить выделенный текст в круглые скобки, введя символ "(" в текстовом редакторе.  
  
 Список дополнительных функций текстового редактора в галерее Visual Studio можно найти [здесь](http://go.microsoft.com/fwlink/?LinkId=692016). Примером может служить расширение [C++ Quick Fixes](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), которое поддерживает перечисленные ниже возможности.  
  
-   **Добавление недостающих операторов #include** — для неизвестных символов в коде предлагаются подходящие операторы #include.  
  
-   **Добавление пространства имен using и полное определение символа** — аналогично предыдущему пункту, но относится к пространствам имен.  
  
-   **Добавление недостающих точек с запятой.**  
  
-   **Справка MSDN** — поиск информации о сообщении об ошибке на сайте MSDN.  
  
 Вы можете либо навести указатель на волнистую линию, чтобы появилась лампочка, либо нажать клавиши CTRL+точка (CTRL+.). Имейте в виду, что при использовании сочетания клавиш курсор не обязательно должен находиться в элементе с ошибкой или в токене. Для получения предложений по любым элементам в строке достаточно, чтобы курсор находился в этой строке.  
  
## <a name="see-also"></a>См. также  
 [Настройка параметров языка редактора](../../ide/reference/setting-language-specific-editor-options.md)   
 [Рефакторинг в C++ (блог по VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)


