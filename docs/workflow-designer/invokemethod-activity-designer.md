---
title: Конструктор действия конструктор рабочих процессов InvokeMethod
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.InvokeMethod.UI
ms.assetid: 15e6efdc-52ca-46d8-9c5e-063f7c8265a6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8660cd82f9d671da3b535ac228e8ce62c875dc07
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593204"
---
# <a name="invokemethod-activity-designer"></a>Конструктор действия InvokeMethod

Конструктор **InvokeMethod** используется для создания и настройки <xref:System.Activities.Statements.InvokeMethod> действия.

## <a name="the-invokemethod-activity"></a>Действие InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> Вызывает открытый метод заданного объекта или типа.

### <a name="use-the-invokemethod-activity-designer"></a>Использование конструктора действия InvokeMethod

Доступ к конструктору действия **InvokeMethod** в категории **примитивы** **панели элементов**. Конструктор действий **InvokeMethod** можно перетащить из **панели элементов** в конструктор рабочих процессовную поверхность, где обычно размещаются все действия, например внутри <xref:System.Activities.Statements.Sequence> . При удалении конструктора действий создается <xref:System.Activities.Statements.InvokeMethod> действие со значением InvokeMethod по умолчанию <xref:System.Activities.Activity.DisplayName%2A> . <xref:System.Activities.Activity.DisplayName%2A>Можно изменить в заголовке конструктора действий **InvokeMethod** или в поле **DisplayName** сетки свойств.

### <a name="the-invokemethod-properties"></a>Свойства InvokeMethod

В следующей таблице показаны <xref:System.Activities.Statements.InvokeMethod> Свойства и описано, как они используются в конструкторе. Эти свойства можно изменить в сетке свойств, а некоторые можно изменить на конструктор рабочих процессов поверхности.

|Имя свойства|Обязательно|Использование|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Неверно|Понятное имя действия <xref:System.Activities.Statements.InvokeMethod>. Значение по умолчанию - InvokeMethod.<br /><br /> Хотя <xref:System.Activities.Activity.DisplayName%2A> использование не является строго обязательным, лучше использовать его.|
|<xref:System.Activities.Statements.InvokeMethod.MethodName%2A>|Верно|Имя метода, вызываемого, когда выполняется действие. Вызываемый метод должен быть объявлен как **открытый**. Это свойство может быть изменено на поверхности конструктора и является обязательным.|
|<xref:System.Activities.Statements.InvokeMethod.Parameters%2A>|Неверно|Коллекция параметров вызванного метода. Параметры должны добавляться в коллекцию в том же порядке, в котором они представлены в сигнатуре метода. Чтобы отобразить диалоговое окно **Параметры** , в котором можно задать это свойство, нажмите кнопку с многоточием в поле **Параметры** сетки свойств. Нажмите кнопку **Создать аргумент** , чтобы добавить параметры.|
|<xref:System.Activities.Statements.InvokeMethod.Result%2A>|Неверно|Возвращаемое значение вызова метода.|
|<xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A>|Верно|Указывает, вызывается ли метод асинхронно. Значение по умолчанию равно **False**.|
|<xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>|Неверно|Объект, в котором содержится метод для вызова. Это свойство можно изменить в области конструктора.<br /><br /> Необходимо указать либо <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>, либо <xref:System.Activities.Statements.InvokeMethod.TargetType%2A>.|
|<xref:System.Activities.Statements.InvokeMethod.TargetType%2A>|Неверно|Тип параметра <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>. Это свойство можно изменить в области конструктора. Это свойство необходимо устанавливать, только если вызванный метод является статическим.|

Для передачи параметров в качестве параметра **out** C# (например, `Method1(out myParam))` Используйте **Аргумент** of вместо **инаутаргумент**

Методы с аргументами, именуемыми **TargetObject** или **result** , нельзя вызывать с помощью <xref:System.Activities.Statements.InvokeMethod> действия. Это происходит потому, что действие <xref:System.Activities.Statements.InvokeMethod> регистрирует <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A>, <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A> и <xref:System.Activities.Statements.InvokeMethod.Result%2A> в <xref:System.Activities.Activity.CacheMetadata%2A>.

Алгоритм регистрирования параметров в <xref:System.Activities.Activity.CacheMetadata%2A> отображается в следующем списке:

1. Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.TargetObject%2A>.

2. Зарегистрируйте аргумент <xref:System.Activities.Statements.InvokeMethod.Result%2A>.

3. Переходите от одного пункта коллекции <xref:System.Activities.Statements.InvokeMethod.Parameters%2A> к другому и зарегистрируйте каждый аргумент.

Результирующее исключение типа <xref:System.Activities.InvalidWorkflowException> со следующим сообщением: «InvokeMethod»: переменная, аргумент RuntimeArgument или DelegateArgument уже существует с именем «TargetObject». Имена должны быть уникальными в среде.

Это ограничение не распространяется на <xref:System.Activities.Statements.InvokeMethod.TargetType%2A> и <xref:System.Activities.Statements.InvokeMethod.RunAsynchronously%2A> . Они не являются аргументами рабочего процесса и поэтому не зарегистрированы в <xref:System.Activities.Statements.InvokeMethod.GenericTypeArguments%2A> коллекции <xref:System.Activities.Statements.InvokeMethod> действия в <xref:System.Activities.Activity.CacheMetadata%2A> методе.

## <a name="see-also"></a>См. также раздел

- [Примитивы](../workflow-designer/primitives-activity-designers.md)
- [Assign](../workflow-designer/assign-activity-designer.md)
- [Задержка](../workflow-designer/delay-activity-designer.md)
- [WriteLine](../workflow-designer/writeline-activity-designer.md)
