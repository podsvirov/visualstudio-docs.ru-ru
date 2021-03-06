---
title: Задать создание элемента управления при перетаскивании из окна "источники данных" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, select controls
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- data [Visual Studio], Data Sources window
ms.assetid: 20597ff8-0c98-43ec-8fb1-05376804ba48
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 222ecfa56b179379c2d007e8635e7b40d6b1b660
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655386"
---
# <a name="set-the-control-to-be-created-when-dragging-from-the-data-sources-window"></a>Задание поведения, при котором элемент управления создается при перетаскивании из окна "Источники данных"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Элементы управления с привязкой к данным можно создавать путем перетаскивания элементов из окна **Источники данных** на конструктор WPF или конструктор Windows Forms. Каждый элемент в окне **Источники данных** имеет элемент управления по умолчанию, который создается при перетаскивании в конструктор. Однако можно выбрать создание другого элемента управления.

## <a name="set-the-controls-to-be-created-for-data-tables-or-objects"></a>Задание элементов управления, создаваемых для таблиц или объектов данных
 Перед перетаскиванием элементов, представляющих таблицы данных или объекты из окна **Источники данных** , можно выбрать отображение всех данных в одном элементе управления или отображение каждого столбца или свойства в отдельном элементе управления.

 В этом контексте термин *объект* ссылается на пользовательский бизнес-объект, сущность (в EDM) или объект, возвращенный службой.

#### <a name="to-set-the-controls-to-be-created-for-data-tables-or-objects"></a>Задание элементов управления, создаваемых для таблиц или объектов данных

1. Убедитесь, что конструктор WPF или конструктор Windows Forms открыты.

2. В окне **Источники данных** выберите элемент, представляющий таблицу или объект данных, которые необходимо задать.

3. Щелкните раскрывающееся меню элемента, а затем выберите один из следующих элементов в меню:

   - Чтобы отобразить каждое поле данных в отдельном элементе управления, нажмите кнопку **Подробности**. При перетаскивании элемента данных в конструктор это действие создаст другой элемент управления с привязкой к данным для каждого столбца или свойства родительской таблицы данных или объекта, а также метки для каждого элемента управления.

   - Чтобы отобразить все данные в одном элементе управления, выберите другой элемент управления в списке, например **DataGrid** или **List** в приложении WPF, или **DataGridView** в Windows Forms приложении.

     Список доступных элементов управления зависит от открываемого конструктора, версии .NET Framework проекта, а также от того, были ли добавлены пользовательские элементы управления, поддерживающие привязку данных к **панели элементов**. Если элемент управления, который требуется создать, находится в списке доступных элементов управления, можно добавить элемент управления в список. Дополнительные сведения см. в разделе [Добавление пользовательских элементов управления в окно Источники данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Сведения о создании пользовательского элемента управления Windows Forms, который можно добавить в список элементов управления для таблиц данных или объектов в окне « **Источники данных** », см. в разделе [Создание Windows Forms пользовательского элемента управления, поддерживающего сложную привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).

## <a name="set-the-controls-to-be-created-for-data-columns-or-properties"></a>Задание элементов управления, создаваемых для столбцов или свойств данных
 Перед перетаскиванием элемента, представляющего столбец или свойство объекта из окна **Источники данных** в конструктор, можно задать создание элемента управления.

#### <a name="to-set-the-controls-to-be-created-for-columns-or-properties"></a>Задание элементов управления, создаваемых для столбцов или свойств

1. Убедитесь, что конструктор WPF или конструктор Windows Forms открыты.

2. В окне **Источники данных** разверните нужную таблицу или объект, чтобы отобразить их столбцы или свойства.

3. Выберите каждый столбец или свойство, для которого необходимо задать создание элемента управления.

4. Щелкните раскрывающееся меню для столбца или свойства, а затем выберите элемент управления, который нужно создать при перетаскивании элемента в конструктор.

     Список доступных элементов управления зависит от открываемого конструктора, версии .NET Framework проекта и пользовательских элементов управления, которые поддерживают привязку данных, добавленную на **панель элементов**. Если элемент управления, который требуется создать, находится в списке доступных элементов управления, можно добавить элемент управления в список. Дополнительные сведения см. в разделе [Добавление пользовательских элементов управления в окно Источники данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).

     Сведения о создании пользовательского элемента управления, который можно добавить в список элементов управления для столбцов или свойств данных в окне **Источники данных** , см. в разделе [Создание Windows Forms пользовательского элемента управления, поддерживающего простую привязку данных](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).

     Если вы не хотите создавать элемент управления для столбца или свойства, выберите **нет** в раскрывающемся меню. Это полезно, если необходимо перетащить родительскую таблицу или объект в конструктор, но не нужно включать конкретный столбец или свойство.

## <a name="see-also"></a>См. также:
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
