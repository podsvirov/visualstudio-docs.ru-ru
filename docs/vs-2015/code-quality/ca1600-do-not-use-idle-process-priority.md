---
title: 'CA1600: не использовать приоритет процесса простоя | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3f6233136dcf7f1db5d622a02419d33e0eedacf5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545682"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600. Не используйте приоритет процесса простоя
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Категория|Microsoft. Mobility|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Это правило происходит, когда для процессов задано значение `ProcessPriorityClass.Idle` .

## <a name="rule-description"></a>Описание правила
 Не задавайте для приоритета процесса значение Idle. Процессы, которые `System.Diagnostics.ProcessPriorityClass.Idle` будут занимать ЦП, когда в противном случае они будут бездействовать, и, следовательно, блокируют ожидание.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Задайте для параметра процессы значение `ProcessPriorityClass.BelowNormal` .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это правило следует подавлять только в том случае, если требуется приоритет процесса простоя, а вопросы мобильности можно игнорировать без каких-либо последствий.
