---
title: решения Word
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c2d3b9ea3257db11eed766079b169a7bc81fe28a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985378"
---
# <a name="word-solutions"></a>решения Word
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания настроек на уровне документа и надстроек VSTO для Microsoft Office Word. Эти решения можно использовать для автоматизации Word, расширения функциональных возможностей Word и настройки пользовательского интерфейса Word. Дополнительные сведения о различиях между настройками уровня документа и надстройками VSTO см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 В данном подразделе содержатся следующие сведения.

- [Автоматизируйте Word](#automating).

- [Разработка настроек на уровне документа для Word](#doclevel).

- [Разработка надстроек VSTO для Word](#applevel).

- [Настройка пользовательского интерфейса Word](#UI).

## <a name="automate-word"></a><a name="automating"></a> Автоматизация Word
 Объектная модель Word предоставляет различные типы, которые можно использовать для автоматизации Word. Например, можно программным образом создавать таблицы, форматировать документы и задавать текст в диапазонах и абзацах. Дополнительные сведения см. в статье [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md).

 При разработке своих решений Word в Visual Studio можно также использовать *ведущие элементы* и *элементы управления ведущего приложения* . Данные элементы являются объектами, которые расширяют некоторые часто используемые объекты в объектной модели Word, например объекты <xref:Microsoft.Office.Interop.Word.Document> и <xref:Microsoft.Office.Interop.Word.ContentControl> . Расширенные объекты ведут себя как объекты Word, на которых они основаны, но добавляют объектам дополнительные события и возможности по привязке данных. Дополнительные сведения см. в разделе [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md).

## <a name="develop-document-level-customizations-for-word"></a><a name="doclevel"></a> Разработка настроек на уровне документа для Word
 Настройка на уровне документа для Microsoft Office Word состоит из сборки, связанной с конкретным документом. Как правило, сборка расширяет документ посредством настройки пользовательского интерфейса и автоматизации Word. В отличие от надстройки VSTO, которая связана с самим Word, функциональные возможности, реализуемые в настройке, доступны только в том случае, когда соответствующий документ открыт в Word.

 Для создания проекта настройки на уровне документа для Word используйте шаблоны проектов для документа Word или шаблона Word в диалоговом окне **Новый проект** Visual Studio. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Дополнительные сведения о принципах работы настроек уровня документа см. в статье [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).

### <a name="word-customization-programming-model"></a>Модель программирования настройки Word
 При создании проекта на уровне документа для Word Visual Studio создает класс с именем `ThisDocument`, который служит базой для вашего решения. Этот класс представляет документ, связанный с решением, и служит отправной точкой для написания собственного кода.

 Дополнительные сведения о `ThisDocument` классе и других функциях, которые можно использовать в проекте уровня документа, см. в разделе [Program настроек на уровне документа](../vsto/programming-document-level-customizations.md).

## <a name="develop-vsto-add-ins-for-word"></a><a name="applevel"></a> Разработка надстроек VSTO для Word
 Надстройка VSTO для Microsoft Office Word состоит из сборки, загружаемой в Word. Как правило, сборка расширяет Word посредством настройки пользовательского интерфейса и автоматизации Word. В отличие от настройки на уровне документа, связанной с конкретным документом, функциональные возможности, реализуемые в надстройке VSTO, не ограничиваются ни одним документом.

 Для создания проекта надстройки VSTO для Word используйте шаблоны проектов надстройки Word в диалоговом окне **Новый проект** Visual Studio. Дополнительные сведения см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 Общие сведения о работе надстроек VSTO см. в разделе [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="word-add-in-programming-model"></a>Модель программирования надстроек Word
 При создании проекта надстройки VSTO для Word среда Visual Studio создает класс с именем `ThisAddIn`, который служит базой для вашего решения. Этот класс служит отправной точкой для написания собственного кода, а также предоставляет объектную модель Word для надстройки VSTO.

 Дополнительные сведения о `ThisAddIn` классе и других функциях, которые можно использовать в надстройке VSTO, см. в разделе [программирование VSTO-надстроек](../vsto/programming-vsto-add-ins.md).

## <a name="customize-the-user-interface-of-word"></a><a name="UI"></a> Настройка пользовательского интерфейса Word
 Для настройки пользовательского интерфейса Word можно использовать несколько способов. Некоторые параметры доступны для всех типов проектов. Также есть параметры, доступные только для надстроек VSTO или настроек на уровне документа.

### <a name="options-for-all-project-types"></a>Параметры для всех типов проектов
 В следующей таблице перечислены параметры настройки, доступные для настроек на уровне документа и надстроек VSTO.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Настройка ленты.|[Общие сведения о ленте](../vsto/ribbon-overview.md)|
|Добавление элементов управления Windows Forms или расширенных элементов управления Word в настраиваемый документ (для настройки на уровне документа) или в любой открытый документ (для надстройки VSTO).|[Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Как добавить элементы управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|

### <a name="options-for-document-level-customizations"></a>Параметры для настроек уровня документа
 В следующей таблице перечислены параметры настройки, доступные только для настроек на уровне документа.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Добавление панели действий в документ.|[Обзор панели действий](../vsto/actions-pane-overview.md)<br /><br /> [Как добавить панель действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Добавление расширенных элементов управления XMLNode и XMLNodes на поверхность документа.|[Как добавить элементы управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Как добавить элементы управления XMLNodes в документы Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|

### <a name="options-for-vsto-add-ins"></a>Параметры для надстроек VSTO
 В следующей таблице перечислены параметры настройки, доступные только для надстроек VSTO.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)|Содержит общие сведения об основных типах, предоставляемых объектной моделью Word.|
|[Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)|Содержит сведения о расширенных объектах (предоставляемых из [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]), которые можно использовать в решениях Word.|
|[Общие сведения об элементах управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Содержит сведения о добавлении элементов управления Windows Forms в документы Word.|
|[Пошаговое руководство. Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Содержит сведения о создании базовой настройки на уровне документа для Word.|
|[Пошаговое руководство. Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Содержит сведения о создании базовой надстройки VSTO для Word.|
|[Пошаговое руководство. Добавление элементов управления в документ во время выполнения в надстройке VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Содержит сведения о добавлении кнопки Windows Forms и <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в документ во время выполнения с помощью надстройки VSTO.|
|[Word 2010 в разработке решений для Office](/previous-versions/office/developer/office-2010/ff601860(v=office.14))|Содержит ссылки на статьи и справочную документацию о разработке решений Word (не только о разработке решений Office с помощью Visual Studio).|
