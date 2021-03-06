---
title: 'CA1810: инициализируйте статические поля ссылочного типа встроенными | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
helpviewer_keywords:
- InitializeReferenceTypeStaticFieldsInline
- CA1810
ms.assetid: e9693118-a914-4efb-9550-ec659d8d97d2
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c4ad2f4db9290430bb8a378bd264078370ca7b66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543836"
---
# <a name="ca1810-initialize-reference-type-static-fields-inline"></a>CA1810. Инициализируйте статические поля ссылочных типов при объявлении
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|InitializeReferenceTypeStaticFieldsInline|
|CheckId|CA1810|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Ссылочный тип объявляет явный статический конструктор.

## <a name="rule-description"></a>Описание правила
 Если в типе объявляется явный статический конструктор, компилятор JIT добавляет проверку в каждый статический метод и конструктор экземпляров этого типа, чтобы убедиться, что статический конструктор уже вызывался ранее. Статическая инициализация активируется при доступе к любому статическому элементу или при создании экземпляра типа. Однако статическая инициализация не запускается при объявлении переменной типа, но не ее использования, что может быть важно, если инициализация меняет глобальное состояние.

 Когда все статические данные инициализируются встроенным образом и явный статический конструктор не объявлен, компиляторы MSIL добавляют `beforefieldinit` флаг и неявный статический конструктор, который инициализирует статические данные с определением типа MSIL. Когда JIT-компилятор обнаруживает `beforefieldinit` флаг, в большинстве случаев проверки статических конструкторов не добавляются. Статическая инициализация будет гарантированно выполняться в определенный момент перед обращением к статическим полям, но не до вызова статического метода или конструктора экземпляра. Обратите внимание, что статическая инициализация может произойти в любое время после объявления переменной типа.

 Проверки статических конструкторов могут привести к снижению производительности. Часто статический конструктор используется только для инициализации статических полей. в этом случае необходимо убедиться, что статическая инициализация выполняется перед первым доступом к статическому полю. `beforefieldinit`Поведение подходит для этих и большинства других типов. Это неприемлемо, только если статическая инициализация влияет на глобальное состояние, и одно из следующих условий имеет значение.

- Воздействие на глобальное состояние является дорогостоящим и не требуется, если тип не используется.

- Эффекты глобального состояния могут быть доступны без доступа к любым статическим полям типа.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, выполните инициализацию всех статических данных при их объявлении и удалите статический конструктор.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 В этом правиле можно отключить вывод предупреждений, если производительность не является проблемой. или если изменения глобального состояния, вызванные статической инициализацией, являются дорогостоящими или должны быть гарантированно выполнены до вызова статического метода типа или создания экземпляра типа.

## <a name="example"></a>Пример
 В следующем примере показан тип, `StaticConstructor` , который нарушает правило и тип, `NoStaticConstructor` который заменяет статический конструктор встроенной инициализацией для удовлетворения этого правила.

 [!code-csharp[FxCop.Performance.RefTypeStaticCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/cs/FxCop.Performance.RefTypeStaticCtor.cs#1)]
 [!code-vb[FxCop.Performance.RefTypeStaticCtor#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.RefTypeStaticCtor/vb/FxCop.Performance.RefTypeStaticCtor.vb#1)]

 Обратите внимание на добавление `beforefieldinit` флага в определении MSIL для `NoStaticConstructor` класса.

 **. класс Public Auto ANSI статикконструктор** **расширяет [mscorlib] System. Object** 
 **{** 
 **}//конец класса статикконструктор** 
 **. класс Public Auto ANSI beforefieldinit ностатикконструктор** **расширяет [mscorlib] System. Object** 
 **{** 
 **}//конец класса ностатикконструктор**
## <a name="related-rules"></a>Связанные правила
 [CA2207. Используйте встроенную инициализацию статических полей типов значений](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)
