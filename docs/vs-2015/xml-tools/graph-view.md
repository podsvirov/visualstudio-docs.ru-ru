---
title: Представление графа | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 5881afde-3f24-4eb9-bff8-6cb3fc8aade7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba58777700ba34de3dc3b7a842f26462daf08c89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656351"
---
# <a name="graph-view"></a>Представление диаграммы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представление графика обеспечивает графическое представление глобальных узлов схемы и связей между узлами. Заметьте, что представление графика не позволяет изменять расположение набора схем в области конструктора. Представление графика также содержит панель инструментов конструктора XML-схем и строка навигатора.

 На приведенном ниже рисунке показано представление графика с шестью глобальными узлами в области конструктора:

 ![Представление графа конструктора схемы XML](../xml-tools/media/xsddesigner-graphview.gif "XSDDesigner_GraphView")

## <a name="design-surface"></a>Область конструктора
 В области конструктора представления графика отображается содержимое [рабочей области Конструктор схем XML](../xml-tools/xml-schema-designer-workspace.md). Если рабочая область содержит глобальные узлы из набора схем, узлы будут показаны в области конструктора представления графика, а узлы, связанные друг с другом, будут соединены стрелочками.

 Двойное нажатие на узел в представлении графика открывает редактор XML.

 Чтобы удалить выбранные узлы в рабочей области, используйте панель инструментов конструктора XSD или клавишу DELETE.

 Если область конструктора пуста, редактор XML, обозреватель XML-схем и водяной знак не отображаются. *Подложка* содержит список ссылок на все представления конструктора XSD.

 ![Конструктор XSD; представление графа](../xml-tools/media/xsdgraphviewwatermark.gif "кссдграфвиевватермарк")

 Если набор схем содержит ошибки, в конце списка появится следующий текст: "Воспользуйтесь списком ошибок для просмотра и устранения ошибок в наборе".

## <a name="breadcrumb-bar"></a>Строка навигатора
 Строка навигатора внизу представления графика показывает месторасположение выбранного узла в наборе схем. Если выбрано несколько элементов, строка навигатора будет пустой.

## <a name="context-menu"></a>Контекстное меню
 В следующей таблице приведены параметры, доступные для всех узлов поверхности конструктора представления графика.

|Параметр|Описание|
|------------|-----------------|
|**Показать в обозревателе XML-схем**|Устанавливает фокус на обозревателе схем и выделяет узел набора схем.|
|**Показать в представлении графика**|Переключается в представление графика (отображается серым цветом).|
|**Создать пример XML**|Этот метод предусмотрен только для глобальных элементов. Создает образец XML-файла для глобального элемента.|
|**Очистить рабочую область**|Очищает рабочую область и область конструктора.|
|**Удалить из рабочей области**|Удаляет выбранные узлы из рабочей области и из области конструктора.|
|**Удалить все элементы, кроме выделенных в рабочей области**|Удаляет узлы, не выделенные в рабочей области и в области конструктора.|
|**Экспортировать схему как изображение...**|Сохраняет область конструктора в XPS-файле.|
|**Выделить все**|Выбирает все узлы в области конструктора.|
|**Просмотреть код**|Открывает в редакторе XML-файл, содержащий выбранный узел. Пункт, выбранный в обозревателе XML-схем, будет выбран и в редакторе XML.|
|**Окно "Свойства"**|Откроется окно **Свойства** (если оно не было открыто). В данном окне будут выведены сведения об узле.|

 Помимо описанных выше общих параметров контекстное меню для глобальных элементов также имеет следующие параметры:

|Параметр|Описание|
|------------|-----------------|
|**Добавить определение типа**|Добавляет базовый тип в схему.|
|**Добавить все ссылки**|Добавляет все узлы, связанные с элементом, и рисует стрелочки, обозначающие связи между ними.|
|**Добавить члены группы подстановки**|Добавляет все члены группы подстановки. Данный параметр появляется в представлении, если элемент является головным элементом или членом группы подстановки.|
|**Создать пример XML**|Создает образец XML-файла для глобального элемента.|

 Помимо описанных выше общих параметров контекстное меню для глобальных простых и глобальных сложных типов также имеет следующие параметры:

|Параметр|Описание|
|------------|-----------------|
|**Добавить базовый тип**|Если выбранный тип является производным от глобального типа, добавляет базовый тип выбранного типа.|
|**Добавить все ссылки**|Добавляет все ссылки выбранного типа. Это относится ко всем элементам и атрибутам выбранного типа и типов, производных от выбранного.|
|**Добавить все производные типы**|Добавляет все типы, прямо или косвенно являющиеся производными от выбранного типа.|
|**Добавить всех предков**|Добавляет все родительские (базовые) типы.|

 Помимо общих параметров, описанных выше, контекстное меню для глобальных групп и групп атрибутов также имеет следующие параметры:

|Параметр|Описание|
|------------|-----------------|
|**Добавить все ссылки**|Добавляет все узлы, связанные с группой, и рисует стрелочки, обозначающие связи между ними.|
|**Добавить все члены**|Добавляет все члены группы и рисует стрелочки, обозначающие связи между ними.|

 Помимо описанных выше общих параметров контекстное меню для глобальных атрибутов также имеет следующие параметры:

|Параметр|Описание|
|------------|-----------------|
|**Добавить все ссылки**|Добавляет все узлы, связанные с группой, и рисует стрелочки, обозначающие связи между ними.|

## <a name="properties-window"></a>Окно «Свойства»
 Используйте контекстное меню для первоначального открытия окна **Свойства** . По умолчанию окно **Свойства** открывается в правом нижнем углу Visual Studio. При нажатии на узел, отображающийся в представлении модели содержимого, свойства этого узла будут отображены в окне **Свойства**.

## <a name="xsd-toolbar"></a>Панель инструментов XSD
 Следующие кнопки панели инструментов XSD включены, если активно представление графика.

 ![Панель инструментов конструктора схемы XML.](../xml-tools/media/xsdgraphviewtoolbar.gif "кссдграфвиевтулбар")

|Параметр|Описание|
|------------|-----------------|
|**Показать начальное представление**|Переключается в [начальное представление](../xml-tools/start-view.md). Доступ к этому представлению можно получить с помощью сочетания клавиш: **CTRL + 1**.|
|**Показать представление модели содержимого**|Переключается на [представление модели содержимого](../xml-tools/content-model-view.md). Доступ к этому представлению можно получить с помощью сочетания клавиш: **CTRL + 2**.|
|**Показать представление графика**|Переключается в [представление графика](../xml-tools/graph-view.md). Доступ к этому представлению можно получить с помощью сочетания клавиш: **CTRL + 3**.|
|**Очистить рабочую область**|Очищает рабочую область и область конструктора.|
|**Удалить из рабочей области**|Удаляет выбранные узлы из рабочей области и из области конструктора.|
|**Удалить все элементы, кроме выделенных в рабочей области**|Удаляет узлы, не выделенные в рабочей области и в области конструктора. Данный параметр включен в представлении модели содержимого и в представлении графика.|
|**Слева направо**|Изменяет макет в представлении графика на иерархическое представление узлов слева направо. Доступ к этому параметру можно получить с помощью сочетания клавиш: **Alt + стрелка вправо**.|
|**Справа налево**|Изменяет макет в представлении графика на иерархическое представление узлов справа налево. Доступ к этому параметру можно получить с помощью сочетания клавиш: **Alt + стрелка влево**.|
|**Сверху вниз**|Изменяет макет в представлении графика на иерархическое представление узлов сверху вниз. Доступ к этому параметру можно получить с помощью сочетания клавиш: **Alt + стрелка вниз**.|
|**Снизу вверх**|Изменяет макет в представлении графика на иерархическое представление узлов снизу вверх. Доступ к этому параметру можно получить с помощью сочетания клавиш: **Alt + стрелка вверх**.|

## <a name="panscroll"></a>Панорамирование/Прокрутка
 Можно панорамировать область конструктора с использованием полос прокрутки или удерживая нажатой клавишу CTRL при нажатии и перетаскивании мыши. При панорамировании области конструктора с использованием перетаскивания, курсор изменяет свой внешний вид на четыре перекрестные стрелочки, указывающие в четырех направлениях.

## <a name="undoredo"></a>Отменить/Повторить
 Функция отменить/повторить включена в представлении графика для следующих действий:

- Добавление одного узла посредством перетаскивания.

- Добавление нескольких узлов из окна результатов поиска в обозревателе схемы или запросов начального представления.

- Удаление одного или нескольких узлов.

## <a name="zoom"></a>Масштаб
 Масштабирование доступно в нижнем правом углу представления графика.

 Масштабированием можно управлять следующими способами:

- Удерживая нажатой клавишу CTRL и прокручивая колесико мышки, когда мышь наведена на поверхность представления графика.

- Используя ползунковый элемент управления. Ползунок отображает текущий масштаб.

  Ползунок масштаба является непрозрачным, если он выбран, если на него наведена мышка или если вы используете клавишу CTRL с колесиком мышки для увеличения масштаба; во всех остальных случаях он является прозрачным.

## <a name="xml-editor-integration"></a>Интеграция редактора XML
 Можно переключаться между представлением графика и редактором XML, нажимая на узел и используя контекстное меню «Перейти к коду».

 Если изменить набор схем в редакторе XML, изменения будут синхронизированы в представлении графика. Дополнительные сведения см. в разделе [Интеграция с редактором XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>См. также:
 [Область конструктора](../xml-tools/xml-schema-designer-workspace.md)
