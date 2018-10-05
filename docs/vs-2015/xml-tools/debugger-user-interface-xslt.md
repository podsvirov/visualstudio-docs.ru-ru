---
title: Пользовательский интерфейс отладчика (XSLT) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac2a1afdd9ccd36843ecce6c2536e2b477cdf5a5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571370"
---
# <a name="debugger-user-interface-xslt"></a>Пользовательский интерфейс отладчика (XSLT)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описаны окна отладчика и диалоговые окна отладчика. Описаны только те элементы пользовательского интерфейса, которым свойственно характерное для XSLT поведение при отладке.  
  
 Дополнительные сведения см. в разделе [отладки Справочник по пользовательскому интерфейсу](../debugger/debugging-user-interface-reference.md).  
  
## <a name="locals-window"></a>Окно локальных значений  
 Окно локальных значений отображает сведения обо всех переменных, определенных в таблице стилей. Окно локальных значений содержит три столбца сведений.  
  
 **Name**  
 В этом столбце содержатся имена всех локальных переменных текущей области. Наборы узлов имеют дерево объектов, в котором можно перейти на уровень ниже, чтобы увидеть вложенные папки.  
  
 **Значение**  
 Этот столбец показывает значение, содержащееся в каждой переменной. Узлы атрибутов, инструкций по обработке, комментариев, текста и CDATA отображают текстовое значение узла. Узлы пространства имен отображают URI-код пространства имен.  
  
 **Type**  
 Этот столбец определяет тип данных каждой переменной, перечисленной в **имя** столбца.  
  
 Окно локальных значений также отображает стандартные переменные контекста, которые отслеживают контекст XSLT-преобразования. Следующая таблица описывает стандартные переменные контекста, используемые XSLT-отладчиком.  
  
|Имя|Описание|  
|----------|-----------------|  
|`last()`|Размер контекста.|  
|`position()`|Положение или индексное число узла контекста относительно размера контекста.|  
|`self::node()`|Значение узла контекста.|  
  
 Дополнительные сведения см. в разделе [как: изменение контекста отладчика](http://msdn.microsoft.com/library/8a69ea63-2ef0-4b4f-9521-cf8ad2e3ec5e).  
  
## <a name="output-window"></a>Окно выходных данных  
 Окно «Вывод» показывает все сообщения об ошибках или исключения безопасности, происходящие во время отладки.  
  
 Отладчик XSLT использует для отображения вывода отладки отдельное окно. Это окно используется для отображения вывода из **Show XSL Output** команды.  
  
## <a name="task-list"></a>список задач  
 Список задач перечисляет все ошибки компиляции в таблице стилей. Двойной щелчок ошибки перемещает курсор к строке с ошибкой.  
  
 Список задач включает все ошибки, которые происходят в блоках скрипта в файле XSLT.  
  
> [!NOTE]
>  Отладчик XSLT не выдает предупреждений, поэтому они никогда не появляются в списке задач.  
  
## <a name="breakpoints-window"></a>Окно точек останова  
 Окно точек останова показывает все точки останова, заданные в текущем проекте. Если точка останова добавляется, пока окно просматривается, окно автоматически обновляется, чтобы отображать новую точку останова.  
  
 Окно точек останова должно вести себя таким же образом, что и другие отладчики среды Visual Studio.  
  
## <a name="command-windowimmediate-window"></a>Окно команд/промежуточное окно  
 Не реализовано в этой версии XSLT-отладчика.  
  
## <a name="watch-window"></a>Окно “Контрольное значение”  
 Окно просмотра значений используется для вычисления переменных. Можно также изменить значения переменных.  
  
 Переменные, отображаемые в окне просмотра значений, относятся к текущему контексту (самый верхний элемент в стеке вызовов). Если изменить контекст, окно просмотра значений обновляет и отображает переменные, заданные для этого контекста.  
  
## <a name="call-stack-window"></a>Окно стека вызовов  
 Окно стека вызовов используется для просмотра имен функций в стеке вызовов, типов параметров и значений параметров. Сведения стека вызовов отображаются, только если отлаживаемая программа находится в состоянии останова.  
  
 Стек вызовов представляет различные контексты, через которые проходит выполнение XSLT. Например, если шаблон «а» вызывает шаблон «б», то шаблон «а» и шаблон «б» появляются в стеке вызовов с текущим контекстом на самой вершине списка. Пользователь может видеть запрос, который выполняется в текущий момент.  
  
 Если у шаблона отсутствует имя в XSLT-файле, то используются имена, формируемые XSLT-обработчиком.  
  
 Щелкнув элемент, отличный от находящегося вверху списка, пользователь может узнать, где находится ветвь выполнения, с помощью стандартного зеленого выделения и зеленых стрелок.  
  
## <a name="quickwatch-dialog-box"></a>Диалоговое окно QuickWatch  
 **"Быстрая проверка"** диалоговое окно используется для оценки выражений XPath 1.0. Узел контекста (узел `self::node()` в окне локальных значений) предоставляет контекст для выполнения выражения XPath. Результат выполнения выражения XPath отображается в окне просмотра значений.  
  
 В следующем списке описываются некоторые ограничения на оценку выражения XPath.  
  
-   Разрешаются только встроенные функции XPath.  
  
-   Встроенные функции XSLT, такие как `document()`, `key()` и т. д., не допускаются.  
  
-   Определяемые пользователем функции не допускаются.  
  
 Дополнительные сведения см. в разделе [как: Оценка выражения XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).  
  
## <a name="disassembly-window"></a>Окно дизассемблирования  
 Окно дизассемблирования показывает код сборки, формируемый XSLT-компилятором. Это окно можно использовать так же, как и все остальные окна дизассемблирования среды Visual Studio.  
  
 Дополнительные сведения [как: использование окна дизассемблирования](../debugger/how-to-use-the-disassembly-window.md).  
  
## <a name="see-also"></a>См. также  
 [Отладка XSLT](../xml-tools/debugging-xslt.md)   
 [Основы отладки](../debugger/debugger-basics.md)   
 [Переменной Windows](http://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
