---
title: 'DA0501: средняя загрузка ЦП профилируемым процессом. | Документы Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0501
- vs.performance.DA0501
- vs.performance.501
ms.assetid: b01946b4-75e3-47d5-a1a1-cebfae66a3af
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1462ac73e599b870f015a02998c069f7613be0ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155779"
---
# <a name="da0501-average-cpu-consumption-by-the-process-being-profiled"></a>DA0501: средняя загрузка ЦП профилируемым процессом.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентификатор правила | DA501 |  
| Категория | Мониторинг ресурсов |  
| Метод профилирования | Все |  
| Сообщение | Среднее использование ЦП профилируемым процессом. |  
| Тип правила | Сведения |  
  
 При профилировании с помощью выборки, памяти .NET или методов разрешения конфликтов ресурсов необходимо собрать минимум 10 выборок, чтобы активировать это правило.  
  
## <a name="rule-description"></a>Описание правила  
 Это сообщение указывает долю времени, когда процессор был занят выполнением инструкций, поступающих из приложения. Содержащееся в отчете значение является средним по всем интервалам измерения, в которых профилируемый процесс был активным. Значение может быть больше 100 % на компьютере с несколькими процессорами.  
  
## <a name="how-to-use-rule-data"></a>Использование данных правила  
 Значение правила используется для сравнения производительности разных версий или сборок программы или для анализа производительности приложения в различных сценариях тестирования.
