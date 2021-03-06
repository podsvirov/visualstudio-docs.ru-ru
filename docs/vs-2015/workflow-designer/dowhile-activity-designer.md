---
title: Конструктор действий DoWhile | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.DoWhile.UI
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b63c3e2e0907bcaf13ada4cbb20ce5527a240fe3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656774"
---
# <a name="dowhile-activity-designer"></a>Конструктор действия DoWhile
<xref:System.Activities.Statements.DoWhile>Действие выполняет действие, содержащееся по <xref:System.Activities.Statements.DoWhile.Body%2A> крайней мере один раз, пока заданное условие не примет **значение false**. Если необходимо, чтобы действие, содержащееся в теле цикла, выполнялось ноль или более раз, используйте действие <xref:System.Activities.Statements.While>.

## <a name="dowhile-properties-in-the-workflow-designer"></a>Свойства DoWhile в конструкторе рабочих процессов
 В следующей таблице показаны свойства действия <xref:System.Activities.Statements.DoWhile>, которые применяются чаще всего, и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.DoWhile.Body%2A>|Неверно|Действие, выполняемое, пока условие имеет **значение true**. Чтобы добавить <xref:System.Activities.Statements.DoWhile.Body%2A> действие, перетащите действие из области элементов в поле **текст** в конструкторе действия **DoWhile** с текстом подсказки "перетащите действие сюда".|
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|Верно|Условие оценивается после каждой итерации цикла. Чтобы задать <xref:System.Activities.Statements.DoWhile.Condition%2A> , введите [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] выражение в поле **условие** в конструкторе действий **DoWhile** или в сетке свойств.|

## <a name="see-also"></a>См. также:
 [При](../workflow-designer/while-activity-designer.md) [потоке управления](../workflow-designer/control-flow-activity-designers.md)