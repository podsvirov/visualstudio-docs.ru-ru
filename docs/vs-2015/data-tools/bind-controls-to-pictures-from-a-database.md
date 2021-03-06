---
title: Привязка элементов управления к рисункам из базы данных | Документация Майкрософт
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
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b8f6ee192399c8af8a508b2f9c2817db954bb36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673018"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Привязка элементов управления к рисункам из базы данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Окно **Источники данных** можно использовать для привязки изображения в базе данных к элементу управления в приложении. Например, можно привязать изображение к <xref:System.Windows.Controls.Image> элементу управления в приложении WPF или к <xref:System.Windows.Forms.PictureBox> элементу управления в Windows Forms приложении.

 Рисунки в базе данных обычно хранятся в виде массивов байтов. Элементам управления " **Источники данных** ", хранящимся в виде массивов байтов, по умолчанию присваивается значение " **нет** ", поскольку байтовые массивы могут содержать любые данные из простого массива байтов в исполняемый файл большого приложения. Чтобы создать элемент управления с привязкой к данным для элемента массива байтов в окне **Источники данных** , которое представляет изображение, необходимо выбрать создаваемый элемент управления.

 В следующей процедуре предполагается, что окно **Источники данных** уже заполнено элементом, привязанным к изображению.

## <a name="bind-a-picture-in-a-database-to-a-control"></a>Привязка изображения в базе данных к элементу управления

1. Убедитесь, что область конструктора, в которую нужно добавить элемент управления, открыта в конструкторе WPF или конструктор Windows Forms.

2. В окне **Источники данных** разверните нужную таблицу или объект, чтобы отобразить их столбцы или свойства.

3. Выберите столбец или свойство, содержащие данные изображения, и выберите один из следующих элементов управления из раскрывающегося списка элементов управления:

    - Если конструктор WPF открыт, выберите **изображение**.

    - Если открыт конструктор Windows Forms, выберите **элемент PictureBox**.

    - Кроме того, можно выбрать другой элемент управления, который поддерживает привязку данных и может отображать изображения. Если элемент управления, который вы хотите использовать, отсутствует в списке доступных элементов управления, его можно добавить в список, а затем выбрать. Дополнительные сведения см. в разделе [Добавление пользовательских элементов управления в окно Источники данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>См. также:
 [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)
