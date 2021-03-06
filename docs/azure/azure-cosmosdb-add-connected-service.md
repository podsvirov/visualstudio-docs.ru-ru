---
title: Добавление Azure CosmosDB с помощью Подключенные службы | Документация Майкрософт
description: Добавление в приложение поддержки CosmosDB Azure с помощью Visual Studio для добавления подключенной службы
author: AngelosP
manager: jillfra
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 08/17/2020
ms.author: angelpe
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2d23081f541fbc12581450c60c6eb4b09f20c64a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "88643273"
---
# <a name="add-azure-cosmos-db-to-your-app-by-using-visual-studio-connected-services"></a>Добавление Azure Cosmos DB в приложение с помощью Visual Studio Подключенные службы

С помощью Visual Studio можно подключить любой из следующих Azure Cosmos DB, используя функцию **подключенные службы** :

- .NET Framework консольное приложение
- ASP.NET MVC (.NET Framework) 
- ASP.NET Core
- .NET Core (включая консольное приложение, WPF, Windows Forms, библиотеку классов)
- Рабочая роль .NET Core
- Функции Azure
- Приложение универсальная платформа Windows
- Xamarin
- Cordova

Подключенные службы добавляют необходимые ссылки и код подключения в проект и вносят соответствующие изменения в файлы конфигурации.

> [!NOTE]
> Этот раздел относится к Visual Studio в Windows. Информацию о Visual Studio для Mac см. в статье [Подключенные службы в Visual Studio для Mac](/visualstudio/mac/connected-services).
## <a name="prerequisites"></a>Обязательные условия

- Visual Studio с установленной рабочей нагрузкой Azure.
- Проект одного из поддерживаемых типов

## <a name="connect-to-azure-cosmos-db-using-connected-services"></a>Подключение к Azure Cosmos DB с помощью Подключенные службы

1. Откройте проект в Visual Studio.

1. В **Обозреватель решений**щелкните правой кнопкой мыши узел **подключенные службы** и в контекстном меню выберите команду **Добавить подключенную службу**.

1. На вкладке **подключенные службы** выберите значок + для **зависимости службы**.

    ![Добавить зависимость службы](./media/vs-azure-tools-connected-services-storage/vs-2019/connected-services-tab.png)

1. На странице **Добавление зависимости** выберите **Azure Cosmos DB**.

    ![Добавить Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/azure-cosmosdb.png)

    Если вы еще не вошли в систему, войдите в свою учетную запись Azure. Если у вас нет учетной записи Azure, вы можете зарегистрироваться для получения [бесплатной пробной версии](https://azure.microsoft.com/account/free).

1. На экране **Azure Cosmos DB** выберите существующую Azure Cosmos DB и нажмите кнопку **Далее**.

    Если необходимо создать базу данных, перейдите к следующему шагу. В противном случае перейдите к шагу 7.

    ![Добавить существующий Cosmos DB в проект](./media/azure-cosmosdb-add-connected-service/created-cosmosdb.png)

1. Чтобы создать Azure Cosmos DB, выполните следующие действия.

   1. Выберите **создать новый Azure Cosmos DB** в нижней части экрана.

   1. Заполните **Azure Cosmos DB: создать новый** экран и нажмите кнопку **создать**.

       ![Новые Azure Cosmos DB](./media/azure-cosmosdb-add-connected-service/create-new-cosmosdb.png)

   1. Когда откроется диалоговое окно **настройка Azure Cosmos DB** , в списке появится новая база данных. Выберите новую базу данных в списке и нажмите кнопку **Далее**.

1. Введите имя строки подключения и укажите, должна ли строка подключения храниться в локальном файле секретов или в [Azure Key Vault](/azure/key-vault).

   ![Укажите строку подключения](./media/azure-cosmosdb-add-connected-service/connection-string.png)

1. На экране **Сводка изменений** отображаются все изменения, которые будут внесены в проект, если вы завершите процесс. Если изменения выглядят нормально, нажмите кнопку **Готово**.

   ![Сводка изменений](./media/azure-cosmosdb-add-connected-service/summary-of-changes.png)

1. Подключение появится в разделе " **зависимости службы** " на вкладке " **подключенные службы** ".

   ![Зависимости служб](./media/azure-cosmosdb-add-connected-service/service-dependencies-after.png)

## <a name="see-also"></a>См. также раздел

- [Страница продукта Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)
- [Документация по Azure Cosmos DB](/azure/cosmos-db/)
- [Подключенные службы ( Visual Studio для Mac)](/visualstudio/mac/connected-services)
