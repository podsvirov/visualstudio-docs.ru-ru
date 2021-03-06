---
title: Добавить новые подключения | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 8a93c287-2834-4a83-a590-bdc3fe8d293f
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 44146613fb43b6fc4269741ba09b94629f888d5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673077"
---
# <a name="add-new-connections"></a>Добавление новых подключений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно проверить подключение к базе данных или службе, а также изучить содержимое базы данных и схемы с помощью **Обозреватель сервера**, **Cloud Explorer**или **Обозреватель объектов SQL Server**. Функциональные возможности этих окон перекрываются в некоторой степени. Основные отличия:

 Обозреватель сервера, установленные по умолчанию в Visual Studio. Может использоваться для проверки соединений и просмотра SQL Server баз данных, любых других баз данных с установленным поставщиком ADO.NET и некоторых служб Azure. Также показывает низкоуровневые объекты, такие как счетчики производительности системы, журналы событий и очереди сообщений. Если источник данных не имеет поставщика ADO.NET, он не отображается здесь, но его по-прежнему можно использовать из Visual Studio, подключаясь программно.

 Cloud Explorer установить это окно вручную в качестве расширения Visual Studio, выбрав **инструменты**  >  **расширения и обновления**в  >  **Интернете**в  >  **галерее Visual Studio**. Предоставляет специализированные функциональные возможности для изучения и подключения к службам Azure.

 Обозреватель объектов SQL Server установлен с SQL Server Data Tools и отображается в меню **вид** . Если вы не видите его там, перейдите в раздел " **программы и компоненты** " на панели управления, найдите Visual Studio и нажмите кнопку " **изменить** ", чтобы повторно запустить установщик после установки флажка для SQL Server Data Tools. Используйте **Обозреватель объектов SQL Server** для просмотра баз данных SQL (если они имеют поставщик ADO.NET), создания новых баз данных, изменения схем, создания хранимых процедур, получения строк подключения, просмотра данных и многого другого. Базы данных SQL, на которых не установлен поставщик ADO.NET, не будут отображаться здесь, но вы можете подключиться к ним программным способом.

## <a name="add-a-connection-in-server-explorer"></a>Добавление подключения в обозреватель сервера
 Чтобы создать подключение к базе данных, щелкните значок **Добавить подключение** в **Обозреватель сервера**или щелкните правой кнопкой мыши **Обозреватель сервера** в узле **подключения к данным** и выберите команду **Добавить подключение**. Отсюда можно также подключиться к базе данных на другом сервере, в службе SharePoint или в службе Azure.

 ![Значок нового подключения обозреватель сервера](../data-tools/media/raddata-server-explorer-new-connection-icon.png "значок нового подключения раддата обозреватель сервера")

 Откроется диалоговое окно **Добавление соединения** . Здесь мы указали имя SQL Server экземпляра LocalDB.

 ![Добавление нового подключения](../data-tools/media/raddata-add-new-connection-dialog.png "Диалоговое окно добавления нового соединения раддата")

## <a name="change-the-provider"></a>Изменение поставщика
 Если источник данных не является нужным, нажмите кнопку **изменить** , чтобы выбрать новый источник данных и (или) новый поставщик данных ADO.NET. Новый поставщик может запросить ваши учетные данные в зависимости от того, как вы его настроили.

 ![Изменить поставщик данных AD0.NET](../data-tools/media/raddata-change-ad0-net-data-provider.png "Поставщик данных раддата Change AD0.NET")

## <a name="test-the-connection"></a>Проверка подключения
 После выбора источника данных нажмите кнопку **проверить соединение**. Если это не удается, вам потребуется устранить неполадки, используя документацию поставщика.

 ![Проверка соединения](../data-tools/media/raddata-test-connection.png "раддата тестовое подключение")

 Если тест выполнен, можно приступать к созданию *источника данных*, который является термином Visual Studio, который на самом деле означает *модель данных* , основанную на базовой базе данных или службе.

## <a name="see-also"></a>См. также:
 [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
