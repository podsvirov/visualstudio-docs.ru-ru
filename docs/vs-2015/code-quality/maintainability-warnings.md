---
title: Предупреждения о поддержке | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.maintainabilityrules
helpviewer_keywords:
- warnings, maintainability
- managed code analysis warnings, maintainability warnings
- maintainability warnings
ms.assetid: 537e70ca-a88c-49df-bfc7-0ee63bbe4f16
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e448a72e2ff92b3e3028829d4b1e7658c304ee3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667897"
---
# <a name="maintainability-warnings"></a>предупреждения удобства обслуживания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предупреждения об обслуживании поддерживают обслуживание библиотек и приложений.

## <a name="in-this-section"></a>в этом разделе

|Правило|Описание|
|----------|-----------------|
|[CA1500. Имена переменных не должны совпадать с именами полей](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Метод экземпляра объявляет параметр или локальную переменную, имя которой соответствует полю экземпляра объявляющего типа, что приводит к ошибкам.|
|[CA1501. Избегайте излишнего наследования](../code-quality/ca1501-avoid-excessive-inheritance.md)|Тип расположен глубже четырех уровней в иерархии наследования. Глубокие иерархии вложенных типов трудно отслеживать, понимать и поддерживать.|
|[CA1502. Избегайте чрезмерной сложности](../code-quality/ca1502-avoid-excessive-complexity.md)|Это правило измеряет число линейно независимых путей в методе, которое определяется числом и сложностью условных ветвей.|
|[CA1504. Проверьте имена полей, которые могут ввести в заблуждение](../code-quality/ca1504-review-misleading-field-names.md)|Имя поля экземпляра начинается с "s_", либо имя статического поля (Shared в [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) начинается с "m_".|
|[CA1505. Избегайте кода, неудобного для поддержки](../code-quality/ca1505-avoid-unmaintainable-code.md)|Тип или метод имеет низкий индекс обслуживаемости. Низкий индекс удобства поддержки означает, что тип или метод, вероятно, трудно поддерживать, поэтому их следует переработать.|
|[CA1506. Избегайте чрезмерной взаимозависимости классов](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Данное правило измеряет взаимозависимость классов путем подсчета количества уникальных ссылок на типы, содержащихся в типе или методе.|

## <a name="see-also"></a>См. также:
 [Оценка сложности и удобства сопровождения управляемого кода](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
