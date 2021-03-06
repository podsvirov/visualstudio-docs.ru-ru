---
title: Представление "Вызывающий/вызываемый" — данные выборки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Caller/Callee view
- Caller/Callee view
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c2f20f67f2f86c94f83362af1df416b387884c13
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2020
ms.locfileid: "90843212"
---
# <a name="caller--callee-view---sampling-data"></a>Представление "Вызывающий/вызываемый" — данные выборки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В представлении "Вызывающий/вызываемый" отображаются данные профилирования для выбранной функции и ее родительских и дочерних функций. Представление "Вызывающий/вызываемый" содержит три таблицы.  
  
 **Текущая функция** отображается в средней таблице и показывает данные профилирования для выбранной функции. Значения включают все вызовы функции, попавшие в выборку.  
  
 **Функции, вызывавшие текущую функцию**, отображаются в верхней таблице и показывает индивидуальный вклад вызывающей (родительской) функции в значениях выбранной (текущей) функции.  
  
 **Функции, которые были вызваны текущей функцией**, отображаются в нижней таблице, в которой указываются данные профилирования для вызываемых (дочерних) функций выбранной функции, когда дочерняя функция вызывалась текущей функцией.  
  
> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Столбец|Description|  
|------------|-----------------|  
|**Идентификатор процесса**|Идентификатор процесса (PID) сеанса профилирования.|  
|**Имя процесса**|Имя процесса.|  
|**Имя модуля**|Имя модуля, содержащего функцию.|  
|**Путь к модулю**|Путь к модулю, содержащему функцию.|  
|**Исходный файл**|Исходный файл, содержащий определение данной функции.|  
|**Имя функции**|Полное имя функции.|  
|**Номер строки функции**|Номер строки, на которой эта функция начинается в исходном файле.|  
|**Адрес функции**|Адрес функции.|  
|**Тип**|Контекст функции:<br /><br /> -   **0** — текущая функция;<br />-   **1** — функция, вызывающая текущую функцию;<br />-   **2** — функция, вызываемая текущей функцией.|  
|**Имя корневой функции**|Имя текущей функции.|  
|**Включающие выборки**|- Для текущей функции — количество собранных выборок независимо от того, выполнялась ли эта функция или одна из ее дочерних функций.<br />- Для вызывающей функции — количество инклюзивных выборок текущей функции, которые были собраны при вызове этой функцией текущей функции.<br />- Для вызываемой функции — количество инклюзивных выборок этой функции, которые были собраны при вызове текущей функцией этой функции.|  
|**% инклюзивных выборок**|Процент от всех выборок сеанса профилирования, которые являются инклюзивными выборками данной функции.|  
|**Эксклюзивные выборки**|- Для текущей функции — количество выборок в сеансе профилирования, которые были собраны во время непосредственного выполнения функции, т. е. когда функция была вверху стека вызовов. Выборки, собранные во время выполнения дочерних функций этой функции, не учитываются эксклюзивными счетчиками.<br />- Для вызывающей функции — количество эксклюзивных выборок текущей функции, которые были собраны при вызове этой функцией текущей функции.<br />- Для вызываемой функции — количество эксклюзивных выборок этой функции, которые были собраны при вызове текущей функцией этой функции.|  
|**% эксклюзивных выборок**|Процент от всех выборок сеанса профилирования, которые являются исключающими выборками данной функции.|  
  
## <a name="see-also"></a>См. также:  
 [Представление "Вызывающий/вызываемый" — данные выборки памяти .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Представление "Вызывающий/вызываемый" — данные инструментирования памяти NET](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Представление "Вызывающий/вызываемый" — данные инструментирования](../profiling/caller-callee-view-instrumentation-data.md)
