---
title: Конструктор действий конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.While.UI
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 77954925533c51885a056f7156121e68851ad769
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115163"
---
# <a name="while-activity-designer"></a>Конструктор действия While

<xref:System.Activities.Statements.While>Действие выполняет действие, содержащееся в его <xref:System.Activities.Statements.While.Body%2A> ходе, а заданное <xref:System.Activities.Statements.While.Condition%2A> значение принимает **значение true**. Вложенное действие может быть не выполнено ни разу. Если вложенное действие должно быть выполнено хотя бы один раз, пользуйтесь вместо этого действием <xref:System.Activities.Statements.DoWhile>.

## <a name="while-properties-in-workflow-designer"></a>Свойства While в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.While>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Указывает дополнительное понятное имя конструктора действия <xref:System.Activities.Statements.While> в заголовке. Значение по умолчанию - While. Значение можно изменить в окне **Свойства** или непосредственно в заголовке конструктора действий.<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.While.Body%2A>|Неверно|Содержит действие, выполняемое, пока <xref:System.Activities.Statements.While.Condition%2A> выражение имеет **значение true**.|
|<xref:System.Activities.Statements.While.Condition%2A>|Верно|Содержит выражение Visual Basic, которое вычисляется, чтобы определить, должно ли выполняться действие в <xref:System.Activities.Statements.While.Body%2A> .|

## <a name="see-also"></a>См. также раздел

- [Поток управления](../workflow-designer/control-flow-activity-designers.md)
- [DoWhile](../workflow-designer/dowhile-activity-designer.md)
