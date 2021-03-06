---
title: Как добавить метод удаления | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], Deleter
- BDC [SharePoint development in Visual Studio], removing data
- BDC [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting entity instances
- Business Data Connectivity service [SharePoint development in Visual Studio], deleting data
- Business Data Connectivity service [SharePoint development in Visual Studio], removing data
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dd97d28936e9f0cc50e9064fdc1a6a64bb20fc77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017043"
---
# <a name="how-to-add-a-deleter-method"></a>Как добавить метод удаления
  Вы можете разрешить конечному пользователю удалить запись данных из внешнего списка на сайте SharePoint, добавив метод удаления в модель. Дополнительные сведения см. [в разделе Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-deleter-method"></a>Создание метода удаления

1. В **конструкторе BDC**выберите сущность.

2. В строке меню выберите **Просмотреть**  >  **другие**  >  **сведения о методе BDC**Windows.

    Откроется окно **сведения о методе BDC** . Дополнительные сведения об этом окне см. в разделе Общие сведения о [средствах проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md).

3. В списке **Добавить метод** выберите **создать метод удаления**.

    Visual Studio добавляет в модель следующие элементы. Эти элементы отображаются в окне **сведения о методе BDC** .

   - Метод с именем **Delete**.

   - Входной параметр для метода.

   - Дескриптор типа для параметра.

   - Экземпляр метода для метода.

     Дополнительные сведения см. [в разделе Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

4. В **Обозреватель решений**откройте контекстное меню файла кода службы, созданного для сущности, и выберите пункт **Просмотреть код**.

    Файл кода службы сущности откроется в редакторе кода. Дополнительные сведения о файле кода службы сущности см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

5. Добавьте код в метод удаления, чтобы удалить запись. В следующем примере элемент строки удаляется из заказа на продажу с помощью образца базы данных AdventureWorks для SQL Server.

   > [!NOTE]
   > Метод в этом примере использует два входных параметра.

   > [!NOTE]
   > Замените значение `ServerName` поля именем сервера.

    [!code-csharp[SP_BDC#6](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#6)]
    [!code-vb[SP_BDC#6](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#6)]

## <a name="see-also"></a>См. также раздел
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Обзор средств проектирования моделей BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Как добавить параметр в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Как определить экземпляр метода](../sharepoint/how-to-define-a-method-instance.md)
