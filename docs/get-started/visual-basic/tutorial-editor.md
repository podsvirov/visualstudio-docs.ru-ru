---
title: Введение в редактирование для разработчиков Visual Basic
description: В этом десятиминутном вводном руководстве по редактору кода Visual Studio мы продемонстрируем несколько методов, которые упрощают написание, понимание кода Visual Basic и навигацию по нему в Visual Studio.
ms.custom: seodec18, get-started
ms.date: 11/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: tutorial
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1ccb218781294cf464ce1c7532de078220bedefb
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740092"
---
# <a name="learn-to-use-the-code-editor"></a>Узнайте, как использовать редактор кода

В этом 10-минутном введении, посвященном редактору кода в Visual Studio, мы добавим код в файл, чтобы рассмотреть некоторые способы, упрощающие написание, понимание кода и навигацию по нему в Visual Studio.

> [!TIP]
> Установите Visual Studio бесплатно со страницы [скачиваемых материалов Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017), если еще не сделали этого.

В этой статье предполагается, что вы уже знакомы с Visual Basic. Если это не так, мы рекомендуем сначала изучить руководство по [началу работы с Visual Basic в Visual Studio](../../get-started/visual-basic/tutorial-console.md).

> [!TIP]
> Чтобы выполнять действия, описанные в этой статье, выберите нужные параметры Visual Basic для Visual Studio. Сведения о настройке параметров для интегрированной среды разработки (IDE) вы найдете в [этой статье](visual-studio-ide.md#select-environment-settings).

## <a name="create-a-new-code-file"></a>Создание файла кода

Для начала создайте файл и добавьте в него код.

1. Откройте Visual Studio, а затем в меню **Файл** в строке меню выберите пункт **Создать файл**.

1. В диалоговом окне **Новый файл** в разделе **Общие** выберите **Класс Visual Basic** и щелкните **Открыть**.

   Новый файл открывается в редакторе с каркасом класса Visual Basic. (Возможно, вы уже заметили, что нам не нужно создавать полный проект Visual Studio, чтобы использовать такие преимущества редактора кода, как выделение синтаксиса. Нам нужен только файл кода.)

   ![Файл кода Visual Basic в Visual Studio](media/tutorial-editor.png)

## <a name="use-code-snippets"></a>Использование фрагментов кода

Visual Studio предоставляет удобные *фрагменты кода*, позволяющие быстро и легко создавать часто используемые блоки кода. [Фрагменты кода](../../ide/code-snippets.md) доступны для различных языков программирования, включая Visual Basic, C# и C++. Давайте добавим в созданный файл фрагмент кода **Sub** на Visual Basic.

1. Поместите курсор над линией с текстом `End Class` и введите слово **sub**.

   Появится всплывающее диалоговое окно с информацией о ключевом слове `Sub` и подсказками для вставки фрагмента кода **Sub**.

   ![IntelliSense для фрагмента кода в Visual Studio](media/tutorial-intellisense-snippet.png)

1. Два раза нажмите клавишу **TAB**, чтобы вставить фрагмент кода.

   В файл будет добавлена структура процедуры Sub `MySub()`.

Для разных языков программирования доступны различные фрагменты кода. Вы можете просмотреть фрагменты кода, доступные для Visual Basic, выбрав пункты меню **Изменить** > **IntelliSense** > **Вставить фрагмент** или нажав сочетание клавиш  **CTRL**+**K**, **Ctrl**+**X**. Для Visual Basic предлагаются фрагменты кода следующих категорий:

![Список фрагментов кода для Visual Basic](media/tutorial-code-snippet-list.png)

Эти фрагменты кода позволяют определить, существует ли на компьютере определенный файл, записать данные в текстовый файл, считать значение реестра, выполнить SQL-запрос, создать [инструкцию For Each...Next](/dotnet/visual-basic/language-reference/statements/for-each-next-statement) и многое другое.

## <a name="comment-out-code"></a>Закомментирование кода

Панель инструментов, которая находится в строке кнопок под строкой меню в Visual Studio, поможет повысить продуктивность написания кода. Например, вы можете переключить режим завершения IntelliSense, увеличить или уменьшить отступ строк или закомментировать фрагмент кода, который не нужно компилировать. (Средство [IntelliSense](../../ide/using-intellisense.md) помогает создавать код, предоставляя списки подходящих методов и выполняя другие действия.) В этом разделе мы закомментируем код.

![Кнопки панели инструментов редактора](media/tutorial-editor-toolbar.png)

1. Вставьте следующий код в тело процедуры `MySub()`.

   ```vb
   ' _words is a string array that we'll sort alphabetically
   Dim _words = New String() {
   "the",
   "quick",
   "brown",
   "fox",
   "jumps"
   }

   Dim morewords = New String() {
   "over",
   "the",
   "lazy",
   "dog"
   }

   Dim query = From word In _words
               Order By word.Length
               Select word
   ```

1. Мы не используем массив `morewords`, но он может нам потребоваться позднее, поэтому удалять этот фрагмент мы пока не будем. Вместо этого давайте закомментируем эти строки. Выберите все определение формы `morewords` до закрывающей скобки и нажмите кнопку **Закомментировать выделенные строки** на панели инструментов. Если вы предпочитаете использовать клавиатуру, нажмите **Ctrl**+**K**, **Ctrl**+**C**.

   ![Кнопка закомментирования](media/tutorial-comment-out.png)

   В начало каждой выбранной строки добавляются символы комментария Visual Basic `'`, чтобы закомментировать код.

## <a name="collapse-code-blocks"></a>Свертывание блоков кода

Вы можете свернуть разделы кода, чтобы полностью сосредоточиться на тех частях, над которыми вы сейчас работаете. Давайте потренируемся, свернув массив `_words` в одну строку кода. Выберите небольшое серое поле со знаком "минус" внутри в поле строки с текстом `Dim _words = New String() {`. Если вы предпочитаете использовать клавиатуру, поместите курсор в любое место определения массива и нажмите сочетание клавиш **CTRL**+**M**, **CTRL**+**M**.

![Кнопка свертывания структурирования](media/tutorial-collapse.png)

Блок кода сворачивается до первой строки, после которой идет многоточие (`...`). Чтобы развернуть блок кода, щелкните то же серое поле, в котором теперь находится знак "плюс", или нажмите клавиши **CTRL**+**M**, **CTRL**+**M** еще раз. Эта функция называется [структурированием](../../ide/outlining.md) и особенно полезна при свертывании длинных методов или целых классов.

## <a name="view-symbol-definitions"></a>Просмотр определений символов

В редакторе Visual Studio можно легко проверить определение типа, метода и т. д. Один из способов заключается в том, чтобы перейти к файлу, который содержит определение, например, выбрав **Перейти к определению** в любом месте, где указана ссылка на этот символ. Сделать это еще быстрее и даже без перемещения фокуса с рабочего файла можно с помощью команды [Показать определение](../../ide/go-to-and-peek-definition.md#peek-definition). Давайте посмотрим определение типа `String`.

1. Щелкните слово `String` правой кнопкой мыши и выберите пункт **Показать определение** в контекстном меню. Или нажмите **Alt**+**F12**.

   Отображается всплывающее окно с определением класса `String`. Вы можете прокрутить его или даже показать определение другого типа из просматриваемого кода.

   ![Окно "Показать определение"](media/tutorial-peek-definition.png)

1. Закройте окно просматриваемого определения, щелкнув небольшое поле со знаком "x" в его правом верхнем углу.

## <a name="use-intellisense-to-complete-words"></a>Использование IntelliSense для завершения слов

Технология [IntelliSense](../../ide/using-intellisense.md) крайне полезна при написании кода. Она может отображать сведения о доступных членах типа или сведения о параметрах для различных перегрузок метода. Вы также можете использовать IntelliSense для завершения слова после того, как ввели достаточно знаков для однозначного его определения. Давайте добавим строку кода для вывода упорядоченных строк в окне консоли — это стандартное место для отображения выходных данных программы.

1. Начните набирать следующий код под переменной `query`.

   ```vb
   For Each str In qu
   ```

   Вы видите, как IntelliSense показывает **Краткие сведения** о символе `query`.

   ![Завершение слов IntelliSense в Visual Studio](media/tutorial-intellisense-completion-list.png)

1. Чтобы вставить оставшуюся часть слова `query` с помощью функции завершения слов IntelliSense, нажмите клавишу **Tab**.

1. Завершите блок кода, чтобы он выглядел аналогично приведенному ниже примеру кода.

   ```vb
   For Each str In query
       Console.WriteLine(str)
   Next
   ```

## <a name="refactor-a-name"></a>Рефакторинг имени

Никто не пишет код правильно с первого раза, и, среди прочего, вам может потребоваться изменить имя переменной или метода. Давайте попробуем использовать функциональность [рефакторинга](../../ide/refactoring-in-visual-studio.md) Visual Studio, чтобы переименовать переменную `_words` в `words`.

1. Поместите курсор над определением переменной `_words` и выберите пункт **Переименовать** в контекстном меню, которое открывается правой кнопкой мыши.

   В верхней правой части редактора отображается всплывающее диалоговое окно **Переименование**.

1. Не снимая выделение с переменной `_words`, введите желаемое имя **words** (слова). Обратите внимание, что ссылка на `words` в запросе также переименовывается автоматически. Прежде, чем нажимать клавишу **ВВОД** или щелкнуть действие **Применить**, установите флажок **Включить комментарии** во всплывающем окне **Переименовать**.

   ![Переименование - диалоговое окно](media/tutorial-rename.png)

1. Нажмите клавишу **ВВОД** или щелкните **Применить**.

   Это действие переименует оба экземпляра `words` и ссылку на `words` в комментариях к коду.

## <a name="next-steps"></a>Следующие шаги

> [!div class="nextstepaction"]
> [Сведения о проектах и решениях](tutorial-projects-solutions.md)

## <a name="see-also"></a>См. также

- [Фрагменты кода](../../ide/code-snippets.md)
- [Навигация по коду](../../ide/navigating-code.md)
- [Структура](../../ide/outlining.md)
- [Функции "Перейти к определению" и "Показать определение"](../../ide/go-to-and-peek-definition.md)
- [Рефакторинг](../../ide/refactoring-in-visual-studio.md)
- [Использование IntelliSense](../../ide/using-intellisense.md)