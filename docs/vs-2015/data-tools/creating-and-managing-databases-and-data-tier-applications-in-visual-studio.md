---
title: Создание баз данных и приложений уровня данных и управление ими
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851686"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Создание баз данных и приложений уровня данных, а также управление ими в Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Внимание!
> Проекты баз данных, включенные в более ранние версии [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , теперь предоставляются в [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] средствах. Дополнительные сведения см. в разделе [SQL Server Developer Tools](https://msdn.microsoft.com/library/hh272686(VS.103).aspx).

 Проекты баз данных можно использовать для создания новых баз данных, новых приложений уровня данных (приложений уровня данных), а также для обновления существующих баз данных и приложений уровня данных. Проекты баз данных и проекты DAC позволяют применять методы управления версиями и управления проектами для разработки баз данных практически так же, как и для управляемого или машинного кода. Вы можете помочь группе разработчиков управлять изменениями баз данных и серверов баз данных путем создания *проекта DAC*, *проекта базы данных*или *серверного проекта* и помещения его в систему управления версиями. Члены команды могут затем извлечь файлы для создания, сборки и тестирования изменений в *изолированной среде разработки*или песочнице, прежде чем предоставлять общий доступ к ним группе. Чтобы обеспечить качество кода, ваша команда может завершить и протестировать все изменения для определенного выпуска базы данных в промежуточной среде перед развертыванием изменений в рабочей области.

 Список функций базы данных, поддерживаемых приложениями уровня данных, см. в разделе [функции, поддерживаемые приложениями уровня данных](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) на веб-сайте Майкрософт. При использовании в базе данных функций, которые не поддерживаются приложениями уровня данных, вместо этого следует использовать проект базы данных для управления изменениями в базе данных.

## <a name="common-high-level-tasks"></a>Общие задачи высокого уровня

|Задача высокого уровня|Вспомогательное содержимое|
|----------------------|------------------------|
|**Начните разработку приложения уровня данных:** DAC — это новая концепция, появившаяся в [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] , которая содержит определение для [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] базы данных и вспомогательных объектов экземпляра, используемых клиент-сервером или 3-уровневое приложение. DAC включает объекты базы данных, такие как таблицы и представления, а также сущности экземпляров, такие как имена входа. Можно использовать [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для создания проекта DAC, создания файла пакета DAC и отправки этого файла пакета DAC администратору базы данных для развертывания на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ядра СУБД.|-   [Создание приложений уровня данных и управление ими](https://msdn.microsoft.com/library/ee361996(VS.100).aspx) (веб-сайт Майкрософт)<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**Выполнение итеративной разработки базы данных:** Если вы являетесь разработчиком или тестировщиком, вы извлекаете части проекта, а затем обновляете их в изолированной среде разработки. С помощью этого типа среды можно тестировать изменения, не затрагивая других участников команды. После внесения изменений файлы возвращаются в систему управления версиями, где другие участники команды могут получить ваши изменения, а затем выполнить сборку и развертывание на тестовом сервере.|-   [Редакторы запросов и текста (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (веб-сайт Майкрософт)<br />-   [Отладчик Transact-SQL](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (веб-сайт Майкрософт)|
|Создание **прототипов, проверка результатов тестов и изменение скриптов и объектов базы данных:** Можно использовать [!INCLUDE[tsql](../includes/tsql-md.md)] редактор для выполнения одной из этих распространенных задач.|-   [Редакторы запросов и текста (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (веб-сайт Майкрософт)|

## <a name="see-also"></a>См. также:
 [Visual Studio Data Tools для .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
