---
title: Возможности, доступные по типам приложений Office и проектов
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ba24bdeac9ad51d0173e765c8cb793be2473baf6
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585436"
---
# <a name="features-available-by-office-application-and-project-type"></a>Возможности, доступные по типам приложений Office и проектов
  В Visual Studio есть шаблоны проектов нескольких типов, которые поддерживают различные бизнес-сценарии для приложений Microsoft Office, включая следующие типы:

- Настройки на уровне документа.

- Надстройки VSTO.

  Не все приложения могут использовать любой тип проекта. Например, проекты уровня документа доступны только для Microsoft Office Word и Microsoft Office Excel. Аналогичным образом, некоторые возможности доступны только для проектов или приложений определенных типов. Например, панель действий доступна только в проектах уровня документа, а расширения ленты — только для некоторых приложений. Дополнительные сведения о различных типах проектов см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

> [!NOTE]
> Шаблоны проектов Office доступны только в некоторых выпусках [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. [в статье Настройка компьютера для разработки решений Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

## <a name="project-types-available-for-different-microsoft-office-applications"></a>Типы проектов, доступные для разных Microsoft Office приложений
 В следующей таблице указаны приложения, которые можно использовать в проекте каждого типа.

|Типы проектов|Приложение Microsoft Office|
|-------------------|----------------------------------|
|Настройки уровня документа.|Excel<br /><br /> Word|
|Надстройки VSTO|Excel<br /><br /> InfoPath (только InfoPath 2013 и InfoPath 2010).<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Project<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|

## <a name="features-available-in-different-project-types"></a>Функции, доступные в различных типах проектов
 В следующей таблице показано, какие функции доступны в каких типах проектов.

|Функция|Типы проектов, предоставляющие возможность|Дополнительные сведения|
|-------------|--------------------------------------------|---------------------|
|Панель действий.|Проекты уровня документа.|[Обзор панели действий](../vsto/actions-pane-overview.md)|
|Развертывание ClickOnce.|Проекты VS и уровня документа.|[Развертывание решения Office](../vsto/deploying-an-office-solution.md)|
|Настраиваемые области задач.|Проекты надстроек VSTO для следующих приложений:<br /><br /> — Excel<br />— InfoPath (только InfoPath 2013 и InfoPath 2010)<br />— Outlook<br />— PowerPoint<br />-Слово|[Настраиваемые области задач](../vsto/custom-task-panes.md)|
|Пользовательские XML-части.|Проекты уровня документа.<br /><br /> Проекты уровня приложения для следующих приложений:<br /><br /> — Excel<br />— PowerPoint<br />-Слово|[Общие сведения о пользовательских XML-частях](../vsto/custom-xml-parts-overview.md)|
|Кэш данных.|Проекты уровня документа.|[Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md)|
|Предоставление объекта в надстройке VSTO другим Microsoft Officeным решениям.|Проекты надстроек VSTO.|[Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|
|Следующие элементы управления ведущего приложения:<br /><br /> — Диаграмма<br />-ListObject<br />-NamedRange<br />— Элементы управления содержимым<br />-Bookmark|Проекты уровня документа.<br /><br /> Проекты надстроек VSTO для Word и Excel.|[Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)|
|Следующие элементы управления ведущего приложения:<br /><br /> -XMLMappedRange<br />-XMLNode<br />-XMLNodes|Проекты уровня документа.|[Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)|
|Развертывание нескольких проектов.|Проекты уровня документа.<br /><br /> Проекты надстроек VSTO.|[Пошаговое руководство. Развертывание нескольких решений Office в одном установщике ClickOnce](/previous-versions/dd465290(v=vs.110))|
|Области формы Outlook.|Проекты надстроек VSTO для Outlook.|[Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)|
|Действия, выполняемые после развертывания.|Проекты уровня документа.<br /><br /> Проекты надстроек VSTO.|[Пошаговое руководство. копирование документа на компьютер конечного пользователя после установки ClickOnce](/previous-versions/dd465291(v=vs.110))|
|Настройки ленты.|Проекты уровня документа.<br /><br /> Проекты надстроек VSTO для следующих приложений:<br /><br /> — Excel<br />— InfoPath (только InfoPath 2013 и InfoPath 2010)<br />— Outlook<br />— PowerPoint<br />-Проект<br />— Visio<br />-Слово|[Общие сведения о ленте](../vsto/ribbon-overview.md)|
|Визуальный конструктор документов.|Проекты уровня документа.|[Проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|

## <a name="see-also"></a>См. также
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Обзор панели действий](../vsto/actions-pane-overview.md)
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)
- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)
- [Кэшированные данные в настройках уровня документа](../vsto/cached-data-in-document-level-customizations.md)
- [Развертывание решения Office](../vsto/deploying-an-office-solution.md)