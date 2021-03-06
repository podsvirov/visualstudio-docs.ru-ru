---
title: '&lt; &gt; Конструктор действий RemoveFromCollection T | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ac088c6e5710fcd1b7c401402ad473488f89524
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672564"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>&lt; &gt; Конструктор активности RemoveFromCollection T
Конструктор **действий \<T> RemoveFromCollection** используется для создания и настройки <xref:System.Activities.Statements.RemoveFromCollection%601> действия.

## <a name="the-removefromcollectiont-activity"></a>Действие RemoveFromCollection \<T>
 Действие <xref:System.Activities.Statements.RemoveFromCollection%601> удаляет указанный элемент из определенной коллекции.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Использование \<T> конструктора действий RemoveFromCollection
 Конструктор **действий \<T> RemoveFromCollection** можно найти в категории **коллекция** **панели элементов**, щелкнув вкладку **область элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] (также можно выбрать пункт **панель инструментов** в меню **вид** или CTRL + ALT + X).

 Конструктор **действий \<T> RemoveFromCollection** можно перетащить из **панели элементов** в [!INCLUDE[wfd2](../includes/wfd2-md.md)] область, где обычно размещаются действия, например внутри <xref:System.Activities.Statements.Sequence> . При этом создается <xref:System.Activities.Statements.RemoveFromCollection%601> действие со значением по умолчанию <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection \<Int32> . <xref:System.Activities.Activity.DisplayName%2A>Значение можно изменить в заголовке конструктора действий ** \<T> RemoveFromCollection** или в поле **DisplayName** сетки свойств. Другие свойства следует изменять в таблице свойств.

### <a name="the-removefromcollectiont-properties"></a>Свойства RemoveFromCollection \<T>
 В следующей таблице показаны свойства <xref:System.Activities.Statements.RemoveFromCollection%601> и описано их использование в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Необязательное понятное имя действия <xref:System.Activities.Statements.RemoveFromCollection%601>. Значение по умолчанию — RemoveFromCollection \<Int32> .<br /><br /> Несмотря на то что свойство <xref:System.Activities.Activity.DisplayName%2A> не является обязательным, его все же рекомендуется использовать.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|Верно|Элемент, добавляемый в **коллекцию \<T> **. Этот элемент имеет тип *T*, имеющий тип *TypeArgument*. Чтобы указать элемент, введите выражение Visual Basic в таблице свойств.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|Верно|Коллекция, в которую следует добавить элемент. Эта коллекция имеет тип **ICollection \<TypeArgument> .** Чтобы указать коллекцию, введите Visual Basic выражение в сетке свойств.|
|*TypeArgument*|Верно|Тип T элементов, содержащихся в коллекции <xref:System.Collections.Generic.ICollection%601>. По умолчанию для этого типа *TypeArgument* задано значение **Int32**. Чтобы изменить тип, измените значение *TypeArgument* в поле со списком в сетке свойств.|
|<xref:System.Activities.Activity%601.Result%2A>|Неверно|Значение, которое указывает, удален ли из коллекции указанный объект. Чтобы указать переменную, к которой необходимо привязать результат, введите переменную в таблицу свойств.|

## <a name="see-also"></a>См. также:
 [Коллекция](../workflow-designer/collection-activity-designers.md) [AddToCollection \<T> ](../workflow-designer/addtocollection-t-activity-designer.md) [ClearCollection \<T> ](../workflow-designer/clearcollection-t-activity-designer.md) [ExistsInCollection \<T> ](../workflow-designer/existsincollection-t-activity-designer.md)