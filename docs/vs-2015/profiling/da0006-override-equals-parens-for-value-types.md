---
title: DA0006. Переопределение Equals() для типов значений | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAOverrideEquals
- vs.performance.6
- vs.performance.DA0006
- vs.performance.rules.DA0006
ms.assetid: 4d85bdd6-b571-47e0-afd6-ba3764e4eed5
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eaba2f099f2a4d04574acd5bcdd2ba8f8f44b4ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852367"
---
# <a name="da0006-override-equals-for-value-types"></a>DA0006. Переопределение Equals() для типов значений
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентификатор правила | DA0006 |  
| Категория |. Использование NET Framework |  
| Методы профилирования | Выборка |  
| Сообщение | Переопределите Equals и оператор равенства для типов значений. |  
| Тип сообщений | Предупреждение |  
  
## <a name="cause"></a>Причина  
 Вызовы метода Equals или операторов равенства открытого типа составляют значительную часть данных профилирования. Рекомендуется использовать более эффективный метод.  
  
## <a name="rule-description"></a>Описание правила  
 В унаследованной реализации Equals для типов значений используется библиотека <xref:System.Reflection> и сравнивается содержимое всех полей типа. Отражение является процессом, требующим с точки зрения вычислений больших затрат, и сравнение каждого поля на равенство может быть лишним. Если предполагается, что пользователи будут сравнивать, сортировать экземпляры или использовать их в качестве ключей хэш-таблиц, тип значения должен реализовывать Equals. Если язык программирования поддерживает перегрузку операторов, также необходимо предоставить реализацию операторов равенства и неравенства.  
  
 Дополнительные сведения о переопределении Equals и операторов равенства см. в разделе [Правила реализации метода Equals и оператора равенства (==)](https://msdn.microsoft.com/library/7h9bszxx.aspx).  
  
## <a name="how-to-investigate-a-warning"></a>Изучение причин предупреждения  
 Пример реализации Equals и операторов равенства см. в описании правила анализа кода [CA1815: Переопределяйте операторы Equals и равенства для типов значений](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)
