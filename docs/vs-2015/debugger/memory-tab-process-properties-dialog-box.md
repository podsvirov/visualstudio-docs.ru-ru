---
title: Вкладка "Память", диалоговое окно "Свойства процесса" | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: a70785f2-5997-40ec-a90f-80a52449768b
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b70c5a982da866cbeb9e9907859ad4d270d79bd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203305"
---
# <a name="memory-tab-process-properties-dialog-box"></a>Вкладка "Память" диалогового окна "Свойства процесса"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

С помощью вкладки **Память** вы можете узнать, как процесс использует память. Чтобы открыть диалоговое окно [Свойства процесса](../debugger/process-properties-dialog-box.md), переместите фокус в окно [представления процессов](../debugger/processes-view.md). Выберите любой узел процесса в дереве, а затем в меню **Вид** выберите пункт **Свойства**.  
  
 На вкладке **Память** доступны следующие параметры:  
  
|Ввод|Описание|  
|-----------|-----------------|  
|**Байты виртуальной памяти**|Текущий размер (в байтах) виртуального адресного пространства, используемого процессом. Использование виртуального адресного пространства не требует использования страниц основной памяти или диска. Но виртуальное пространство ограничено, поэтому его чрезмерное использование может ограничить способность процесса загружать библиотеки.|  
|**Размер виртуальной памяти (пик) (байт)**|Максимальный размер (в байтах) виртуального адресного пространства, используемого процессом в определенный момент времени.|  
|**Рабочий набор**|Набор страниц памяти, недавно задействованных потоками в этом процессе. Если объем свободной памяти компьютера превышает определенный порог, страницы остаются в рабочем наборе процесса, даже если они не используются. Когда объем свободной памяти опускается ниже этого порога, страницы исключаются из рабочего набора. При необходимости они снова будут включены в рабочий набор при устранении ошибки, прежде чем будут выгружены из основной памяти.|  
|**Пиковый рабочий набор**|Максимальное количество страниц в рабочем наборе этого процесса в определенный момент времени.|  
|**Выгружаемый пул (байт)**|Текущий размер выгружаемого пула, выделенного процессом. Выгружаемый пул — это область системной памяти, которую компоненты операционной системы используют для выполнения назначенных задач. Страницы в выгружаемом пуле могут выгружаться в файл подкачки, если они не используются системой в течение длительного периода времени.|  
|**Невыгружаемый пул (байт)**|Текущее количество байтов в невыгружаемом пуле, выделенном процессом. Невыгружаемый пул — это область системной памяти, которую компоненты операционной системы используют по мере выполнения назначенных задач. Страницы невыгружаемого пула не могут выгружаться в файл подкачки. Они остаются в основной памяти при условии, что они выделены.|  
|**Байты исключительного пользования**|Текущее количество выделенных процессом байтов, которые не предоставляются в общий доступ другим процессам.|  
|**Свободно (байт)**|Общий объем неиспользуемого виртуального адресного пространства этого процесса.|  
|**Зарезервировано (байт)**|Общий объем виртуальной памяти, зарезервированной для использования этим процессом в будущем.|  
|**Свободно для образа (байт)**|Объем виртуального адресного пространства, который не используется и не зарезервирован образами в этом процессе.|  
|**Зарезервировано для образа (байт)**|Вся виртуальная память, которая зарезервирована выполняемыми в этом процессе образами.|
