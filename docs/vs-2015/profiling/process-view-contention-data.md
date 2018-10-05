---
title: Представление "Процесс" — данные о состязаниях | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process view
ms.assetid: 8821d98c-0771-43b2-a38b-e9039a3abd75
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 411de842beb616cf4ed7c51d0458e8d7bce82690
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563254"
---
# <a name="process-view---contention-data"></a>Представление "Процесс" — данные о состязаниях
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [представление "процесс" — данные о конфликтах](https://docs.microsoft.com/visualstudio/profiling/process-view-contention-data).  
  
В представлении "Процесс" отображаются данные о состязаниях для процессов и потоков, которые выполнялись во время сеанса профилирования.  
  
 Если символы доступны, то в списке указываются имена процессов. Если символы недоступны, то в списке указываются адреса процессов в памяти в шестнадцатеричном формате. Потоки указываются как дочерние элементы создавших их процессов.  
  
 В следующей таблице описаны значения столбцов в представлении "Процесс".  
  
|Столбец|Описание|  
|------------|-----------------|  
|**Время начала**|Количество миллисекунд или циклов процессора от начала профилирования до запуска процесса или потока.|  
|**Время блокировки**|Общее время, в течение которого выполнение функций процесса или потока заблокировано.|  
|**% времени блокировки**|Процент времени существования процесса или потока, в течение которой выполнение функций процесса или потока было заблокировано.|  
|**Состязания**|Количество блокировок выполнения функций процесса или потока.|  
|**% состязаний**|Процент всех состязаний в сеансе профилирования, которые являются состязаниями данного процесса или потока.|  
|**Время окончания**|Количество миллисекунд или циклов процессора от начала профилирования до завершения процесса или потока.|  
|**ID**|Созданный системой идентификатор процесса или потока.|  
|**Время существования**|Количество миллисекунд или циклов процессора от начала процесса или потока до конца процесса или потока, или конца профилирования.|  
|**Тип**|Тип строки — процесс или поток.<br /><br /> Только в отчетах командной строки **VSPerfReport**. Дополнительные сведения см. в разделе [VSPerfReport](../profiling/vsperfreport.md).|  
|**Name**|Имя процесса или потока.|  
|**Уникальный идентификатор**|Созданный профилировщиком идентификатор, уникальным образом определяющий процесс или поток.|  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Настройка столбцов представлений отчета](../profiling/how-to-customize-report-view-columns.md)   
 [Представление "Процесс"](../profiling/process-view.md)


