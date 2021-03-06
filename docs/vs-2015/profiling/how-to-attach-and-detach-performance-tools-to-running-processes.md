---
title: Практическое руководство. Подключение средств оценки производительности к выполняющимся процессам и отключение от этих процессов | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.attach
helpviewer_keywords:
- performance tools, attach process
- profiling tools, detach process
- profiling tools, attach process
- performance tools, detach process
- profiler
ms.assetid: 56a99c39-e7f6-4f48-ae56-04ab8e022bf7
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b8fc664ee47cd34ab984d1ac448b45c2f17c5b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842764"
---
# <a name="how-to-attach-and-detach-performance-tools-to-running-processes"></a>Практическое руководство. Подключение средств оценки производительности к выполняющимся процессам и отключение от этих процессов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Профилировщик можно использовать для подключения к или отключения от выполняющегося процесса, чтобы упростить выборку и сбор данных производительности. Этот метод можно использовать для профилирования процесса, если необходимо запретить сбор данных о времени загрузки приложения или отследить производительность процесса после достижения им определенного состояния.  
  
> [!NOTE]
> Следующая процедура применима к подключению и отключению процессов из интегрированной среды разработки (IDE) [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Сведения об использовании средств командной строки см. в разделе [Профилирование из командной строки](../profiling/using-the-profiling-tools-from-the-command-line.md). Сведения о профилировании служб см. в разделе [Профилирование служб](../profiling/command-line-profiling-of-services.md).  
  
 Процессы, доступные для профилирования, зависят от разрешений на доступ пользователя, заданных администратором компьютера. Учетная запись пользователя, например, имеет разрешения на следующее:  
  
- расширенные возможности профилирования, если администратор задал драйвер и запускаемую службу;  
  
- только профилирование выборки (пользователи домена);  
  
- запрет доступа к профилированию для всех пользователей.  
  
  Дополнительные сведения см. в разделе [Профилирование и безопасность Windows Vista](../profiling/profiling-and-windows-vista-security.md) и параметры администрирования в средстве [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-attach-to-a-running-process"></a>Присоединение к выполняющемуся процессу  
  
1. В меню **Анализ** наведите указатель мыши на пункт **Профилировщик** и щелкните **Присоединить/отсоединить**.  
  
     \- или -  
  
     В **обозревателе производительности** щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Присоединить/отсоединить**.  
  
     Откроется диалоговое окно **Присоединить профилировщик к процессу**.  
  
2. Щелкните имя процесса, к которому необходимо подключиться.  
  
3. Нажмите кнопку **Присоединить**.  
  
### <a name="to-detach-from-a-running-process"></a>Отключение от выполняемого процесса  
  
1. В меню **Анализ** наведите указатель мыши на пункт **Профилировщик** и щелкните **Присоединить/отсоединить**.  
  
     \- или -  
  
     В **обозревателе производительности** щелкните правой кнопкой мыши сеанс производительности, а затем выберите **Присоединить/отсоединить**.  
  
     Откроется диалоговое окно **Присоединить профилировщик к процессу**.  
  
2. Щелкните имя процесса, который необходимо отключить.  
  
3. Щелкните **Отключить**.  
  
## <a name="see-also"></a>См. также:  
 [Управление сбором данных](../profiling/controlling-data-collection.md)   
 [Обзор сеанса анализа производительности](../profiling/performance-session-overview.md)   
 [Как начать и завершить сбор данных о производительности](../profiling/how-to-start-and-end-performance-data-collection.md)   
 [Профилирование и безопасность Windows Vista](../profiling/profiling-and-windows-vista-security.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)
