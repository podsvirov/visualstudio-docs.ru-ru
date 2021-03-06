---
title: Рефакторинг (C#) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667502"
---
# <a name="refactoring-c"></a>Рефакторинг (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Рефакторинг — это процесс улучшения кода после его написания путем изменения внутренней структуры кода без изменения внешнего поведения кода.

 Visual C# предоставляет следующие команды рефакторинга в меню **рефакторинга** :

- [Рефакторинг для извлечения метода (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Переименовать рефакторинг (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [Рефакторинг для инкапсуляции поля (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Рефакторинг для извлечения интерфейса (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Рефакторинг для удаления параметров (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Рефакторинг для упорядочения параметров (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Рефакторинг нескольких проектов
 Visual Studio поддерживает рефакторинг нескольких проектов для проектов, которые находятся в одном решении. Все операции рефакторинга, которые исправлять ссылки между файлами, исправлять эти ссылки во всех проектах одного языка. Это работает для всех ссылок между проектами. Например, если имеется консольное приложение, которое ссылается на библиотеку классов, при переименовании типа библиотеки классов (с помощью `Rename` операции рефакторинга) ссылки на тип библиотеки классов в консольном приложении также обновляются.

## <a name="changes-preview"></a>Предварительный просмотр изменений
 Многие операции рефакторинга дают возможность просматривать все изменения ссылок, выполненные операцией рефакторинга в коде, до внесения этих изменений. Для этих операций рефакторинга в диалоговом окне рефакторинга появится параметр **Предварительный просмотр изменений ссылок** . После выбора этого параметра и принятия операции рефакторинга появится **диалоговое окно Просмотр изменений** . Обратите внимание, что диалоговое окно **Просмотр изменений** имеет два представления. В нижнем представлении будет отображаться код со всеми обновлениями ссылок из-за операции рефакторинга. Нажатие кнопки **"Отмена"** в диалоговом окне " **Просмотр изменений** " приведет к прекращению операции рефакторинга, и в код не будут внесены изменения.

## <a name="refactoring-warnings"></a>Предупреждения рефакторинга
 Если компилятор не имеет полного представления о программе и возможно, что подсистема рефакторинга может не обновить все соответствующие ссылки, появится диалоговое окно предупреждение. Это диалоговое окно предупреждения также предоставляет возможность предварительного просмотра кода в диалоговом окне **Предварительный просмотр изменений** перед фиксацией изменений.

> [!NOTE]
> Если метод содержит синтаксическую ошибку (интегрированная среда разработки обозначается красной волнистой линией), то подсистема рефакторинга не обновит все ссылки на элемент в этом методе. Это поведение показано в приведенном ниже примере.

 По умолчанию при выполнении операции рефакторинга без предварительного просмотра изменений ссылок и обнаружении ошибки компиляции в программе в среде разработки отображается это диалоговое окно предупреждения.

 Если выполняется операция рефакторинга, в которой включены **изменения ссылок на предварительный просмотр** и в программе обнаружена ошибка компиляции, то среда разработки отобразит следующее предупреждение в нижней части диалогового окна " **Просмотр изменений** ", а не отображает диалоговое окно **предупреждения рефакторинга** .

 **Проект или одна из его зависимостей в настоящее время не построена. Ссылки не могут быть обновлены.**

 Это предупреждение рефакторинга доступно только для операций рефакторинга, предоставляющих параметр **Предварительный просмотр изменений ссылок** .

## <a name="error-tolerant-refactoring-and-verification-results"></a>Нечувствительные к ошибкам рефакторинг и результаты проверки
 Рефакторинг является нечувствительным к ошибкам. Иными словами, можно выполнить рефакторинг в проекте, который не может быть построен. Однако в таких случаях процесс рефакторинга может неправильно обновлять неоднозначные ссылки.

 В диалоговом окне **результаты проверки** можно уведомить вас, если подсистема рефакторинга обнаружит ошибки компиляции или обнаруживает, что операция рефакторинга случайно приводит к тому, что ссылка на код привязывается к чему-то, отличному от того, к чему она была изначально привязана (ошибка повторной привязки).

 Чтобы включить функцию результатов проверки, в меню **Сервис** выберите пункт **Параметры**. В диалоговом окне **Параметры** разверните узел **текстовый редактор**, а затем узел **C#**. Нажмите кнопку **Дополнительно** и установите флажок **проверить результаты рефакторинга** .

 В диалоговом окне **результаты проверки** различается различия между двумя видами проблем повторной привязки.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Ссылки, определение которых больше не будет переименованным символом
 Этот тип проблемы повторной привязки возникает, когда ссылка больше не ссылается на переименованный символ. Рассмотрим следующий пример кода:

```csharp
class Example
{
    private int a;
    public Example(int b)
    {
        a = b;
    }
}
```

 При использовании рефакторинга для переименования `a` в `b` это диалоговое окно отображается. Ссылка на переименованную переменную `a` теперь привязывается к параметру, который передается конструктору вместо привязки к полю.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Ссылки, определение которых теперь станет переименованным символом
 Этот тип проблемы перепривязки возникает, когда ссылка, которая ранее не ссылалась на переименованный символ, теперь ссылается на переименованный символ. Рассмотрим следующий пример кода:

```csharp
class Example
{
    private static void Method(object a) { }
    private static void OtherMethod(int a) { }
    static void Main(string[] args)
    {
        Method(5);
    }
}
```

 При использовании рефакторинга для переименования `OtherMethod` в `Method` это диалоговое окно отображается. Ссылка в `Main` теперь ссылается на перегруженный метод, принимающий `int` параметр, а не перегруженный метод, принимающий `object` параметр.

## <a name="see-also"></a>См. также:
 [Использование среды разработки Visual Studio для C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [руководство. Восстановление фрагментов кода для рефакторинга c#](../ide/how-to-restore-csharp-refactoring-snippets.md)