---
title: Отладка нарушения доступа в C++ | Документация Майкрософт
ms.custom: seodec18
ms.date: 02/05/2019
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 803f81d1a26438c2134349a85369d341353e17cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350424"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>Как отладить нарушение доступа в C++?

## <a name="problem-description"></a>Описание проблемы

Программа порождает нарушение доступа. Как это отладить?

## <a name="solution"></a>Решение

Если вы получаете нарушение прав доступа в строке кода, которая разыменовывает несколько указателей, может быть трудно определить указатель, который вызвал нарушение прав доступа. Начиная с Visual Studio 2015 с обновлением 1 диалоговое окно исключения теперь явно называет указатель, который вызвал нарушение прав доступа.

Например, если имеется следующий код, вы должны получить нарушение прав доступа:

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

При выполнении этого кода в Visual Studio 2015 с обновлением 1 вы увидите следующее диалоговое окно исключения:

![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")

Если не удается определить, почему указатель вызвал нарушение прав доступа, выполните трассировку кода, чтобы проверить правильность назначения указателя, ставшего причиной проблемы.  Если он передается как параметр, убедитесь, что он передается правильно и вы не создаете случайно [неполную копию](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy). Затем проверьте, не изменяются ли непреднамеренно значения где-нибудь в программе путем создания точки останова по данным для рассматриваемого указателя, чтобы убедиться, что он не изменяется в другом месте программы. Дополнительные сведения о точках останова по данным см. в разделе, посвященном точкам останова по данным, в статье [Using Breakpoints](../debugger/using-breakpoints.md).

## <a name="see-also"></a>См. также
- [Вопросы и ответы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)