---
title: Справочник по схемам зависимостей
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 774716dff6562b7792c6fa885c40db2a0a133136
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594569"
---
# <a name="dependency-diagrams-reference"></a>Схемы зависимостей: справочные материалы

В Visual Studio можно использовать *схему зависимостей* для визуализации высокоуровневой логической архитектуры системы. Схема зависимостей организует физические артефакты в системе в логические, абстрактные группы, называемые *слоями*. Слои описывают основные компоненты системы или задачи, выполняемые этими артефактами. Каждый слой может также содержать вложенные слои, описывающие более подробные задачи.

Чтобы узнать, какие выпуски Visual Studio поддерживают эту функцию, см. раздел [Поддержка инструментов моделирования и архитектуры в различных выпусках](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Схемы зависимостей для проектов .NET Core поддерживаются начиная с Visual Studio 2019 версии 16,2.

Между слоями можно установить предполагаемые или существующие зависимости. Эти зависимости, представленные в виде стрелок, показывают, какие слои могут использовать или в настоящее время используют функциональные возможности, представленные другими слоями. Организуя систему в слои, описывающие различные роли и функции, схема зависимостей может облегчить понимание, повторное использование и обслуживание кода.

Используйте схему зависимостей для выполнения следующих задач:

- представлять существующую или предполагаемую логическую архитектуру системы;

- выявлять конфликты между существующим кодом и предполагаемой архитектурой;

- визуализировать влияние изменений на предполагаемую архитектуру при рефакторинге, обновлении или развитии системы;

- дополнительно контролировать предполагаемую архитектуру в процессе разработки и обслуживания кода за счет добавления проверки операций возврата и построения.

В этом разделе описываются элементы, которые можно использовать на схеме зависимостей. Более подробные сведения о создании и отрисовке схем зависимостей см. в разделе [схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md). Дополнительные сведения о шаблонах слоев см. на [веб-сайте patterns & Practices](https://archive.codeplex.com/?p=apparch).

## <a name="reading-dependency-diagrams"></a>Чтение схем зависимостей

![Элементы на схемах зависимостей](../modeling/media/uml_layerrefreading.png)

В следующей таблице описаны элементы, которые можно использовать на схеме зависимостей.

|**Фигурная**|**Element**|**Описание**|
|-|-|-|
|1|**Уровень**|Логическая группа физических артефактов в системе. Артефактами могут быть пространства имен, проекты, классы, методы и т. п.<br /><br /> Чтобы просмотреть артефакты, связанные с слоем, откройте контекстное меню слоя и выберите **Просмотреть ссылки** , чтобы открыть **Обозреватель слоев**.<br /><br /> Дополнительные сведения см. в разделе [Обозреватель слоев](#Explorer).<br /><br /> -   **Запрещенные зависимости пространств имен** . указывает, что артефакты, связанные с этим слоем, не могут зависеть от указанных пространств имен.<br />-   **Запрещенные пространства имен** — указывает, что артефакты, связанные с этим слоем, не должны принадлежать к указанным пространствам имен.<br />-   **Обязательные пространства имен** — указывает, что артефакты, связанные с этим слоем, должны принадлежать одному из указанных пространств имен.|
|2|**Зависимость**|Указывает, что один слой может использовать функции другого слоя, но не наоборот.<br /><br /> -   **Direction** — задает направление зависимости.|
|3|**Двусторонняя зависимость**|Указывает, что один слой может использовать функции другого слоя и наоборот.<br /><br /> -   **Direction** — задает направление зависимости.|
|4|**Комментарий**|Используется для добавления общих примечаний к схеме или ее элементам.|
|5|**Добавить комментарий для ссылки**|Используется для связи комментариев с элементами на схеме.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Обозреватель слоев

Каждый слой можно связать с артефактами в решении, например с проектами, классами, пространствами имен, файлами проекта и другими частями программного обеспечения. Число на слое обозначает количество связанных с этим слоем артефактов. Число артефактов в слое следует толковать с учетом следующих факторов.

- Если слой связан с артефактом, содержащим другие артефакты, но слой не связан с другими артефактами напрямую, то число включает только связанный артефакт. Однако для анализа в ходе проверки слоя включаются другие артефакты.

     Например, если слой связан с одним пространством имен, то число связанных артефактов равно 1, даже если пространство имен содержит классы. Если слой также связан с каждым классом в пространстве имен, то число будет включать эти связанные классы.

- Если слой содержит другие слои, связанные с артефактами, то слой-контейнер также связан с этими артефактами, даже если число в слое-контейнере не включает эти артефакты.

Дополнительные сведения о связывании слоев и артефактов см. в разделах:

- [Схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md)

- [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Проверка связанных артефактов

На схеме зависимостей откройте контекстное меню для одного или нескольких слоев и выберите **Просмотреть ссылки**.

Откроется **Обозреватель слоев** , в котором отображаются артефакты, связанные с выбранными слоями. В **обозревателе слоев** имеется столбец, показывающий каждое из свойств ссылок артефактов.

> [!NOTE]
> Если вы не видите все эти свойства, разверните окно **Обозреватель слоев** .

|**Столбец в обозревателе слоев**|**Описание**|
|-|-|
|**Категории**|Вид артефакта, например класс, пространство имен, исходный файл и т. д.|
|**Уровень**|Связанный с артефактом слой|
|**Поддерживает проверку**|Если **значение — true**, процесс проверки слоев может проверить, соответствует ли проект зависимостям к или из этого элемента.<br /><br /> Если **значение равно false**, ссылка не участвует в процессе проверки слоев.<br /><br /> Дополнительные сведения см. в разделе [схемы зависимостей: рекомендации](../modeling/layer-diagrams-guidelines.md).|
|**Идентификатор**|Ссылка на связанный артефакт|

## <a name="see-also"></a>См. также раздел

- [Создание моделей для приложения](../modeling/create-models-for-your-app.md)
