---
title: Конструктор действий по сохранению конструктор рабочих процессов
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 75236d7955cba6b8c62b9a4504f02c66cebe4062
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114767"
---
# <a name="persist-activity-designer"></a>Конструктор действия Persist

Конструктор **сохранения** действий используется для создания и настройки <xref:System.Activities.Statements.Persist> действия.

## <a name="the-persist-activity"></a>Действие Persist

Действие <xref:System.Activities.Statements.Persist> сохраняет рабочий процесс на диск, если это возможно. Действие <xref:System.Activities.Statements.Persist> не может быть выполнено в зоне несохраняемости, например в пределах действия <xref:System.Activities.Statements.TransactionScope>. Если вы используете <xref:System.Activities.Statements.Persist> действие в области без сохранения состояния, во время выполнения создается исключение.

### <a name="using-the-persist-activity-designer"></a>Использование конструктора действия Persist

Конструктор **хранимых** операций можно найти в категории **Среда выполнения** **панели элементов**, щелкнув вкладку **область элементов** (также можно выбрать **область элементов** в меню **вид** или CTRL + ALT + X).

Конструктор действий по **сохранению** можно перетащить из **панели элементов** в конструктор рабочих процессовную область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . <xref:System.Activities.Statements.Persist>Будет создано действие с **отображаемым значением DisplayName** по умолчанию. <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора **хранимых** операций или в поле **DisplayName** сетки свойств.

### <a name="the-persist-properties"></a>Свойства Persist

В следующей таблице показаны свойства <xref:System.Activities.Statements.Persist> и описано их использование в конструкторе. Эти свойства можно изменять в сетке свойств, а некоторые из них можно редактировать на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.Persist>. По умолчанию используется значение Persist. Несмотря на то что использовать отображаемое имя необязательно, его все же рекомендуется задавать.|

## <a name="see-also"></a>См. также раздел

- [Параметры выполнения](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
