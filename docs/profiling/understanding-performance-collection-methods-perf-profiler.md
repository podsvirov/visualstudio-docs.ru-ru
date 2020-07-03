---
title: Общие сведения о методах сбора данных по производительности | Документы Майкрософт
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: 03a49763a682f6b98b02fe40ba957efa8f5483c8
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290973"
---
# <a name="understand-performance-collection-methods"></a>Общие сведения о методах сбора данных о производительности

В статье описаны методы сбора данных, которые применяются в инструментах Профилировщика производительности Visual Studio. 

## <a name="sampling"></a>Дискретизация

Методы профилирования с выборкой позволяют собирать статистические данные о работе, выполняемой приложением во время сеанса профилирования. При этом данные о приложении собираются с регулярным интервалом или частотой выборки (например, каждую миллисекунду), после чего они анализируются для создания модели, демонстрирующей, как долго приложение выполняло ту или иную задачу. Метод с выборкой не является ресурсоемким и практически не влияет на выполнение профилируемого приложения. К числу инструментов Профилировщика производительности, в которых используется метод с выборкой, относится [Загрузка ЦП](../profiling/cpu-usage.md).

## <a name="instrumentation"></a>Инструментирование

Профилирование инструментирования позволяет собирать подробные сведения о работе, выполняемой приложением во время сеанса профилирования. Сбор данных выполняется инструментами, которые либо вставляют код в двоичный файл для получения сведений о времени, либо используют перехватчики обратного вызова для сбора и отправки точных сведений о времени и количестве вызовов во время выполнения приложения. Применение метода инструментирования связано с высокими издержками, если сравнивать его с подходами, основанными на выборке. К инструментам Профилировщика производительности, использующим инструментирование, относится [Распределение объектов .NET](../profiling/dotnet-alloc-tool.md).