---
title: 'CA1045: не передавайте типы по ссылке | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dad2f90a51a4247a4c111ef51e85a28ba1a118ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548477"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045. Не передавайте типы по ссылке
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Категория|Microsoft. Design|
|Критическое изменение|Критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный метод в открытом типе имеет `ref` параметр, принимающий тип-примитив, ссылочный тип или тип значения, не являющийся одним из встроенных типов.

## <a name="rule-description"></a>Описание правила
 Передача типов по ссылке (с помощью `out` или `ref` ) требует взаимодействия с указателями, понимание того, как типы значений и ссылочные типы различаются, и обрабатывает методы с несколькими возвращаемыми значениями. Кроме того, различие между `out` `ref` параметрами и не является широко понятным.

 Когда ссылочный тип передается по ссылке, метод намеревается использовать параметр для возврата другого экземпляра объекта. (Передача ссылочного типа по ссылке также называется использованием двойного указателя, указателя на указатель или двойного косвенного обращения.) При использовании соглашения о вызовах по умолчанию, которое передает "по значению", параметр, который принимает ссылочный тип, уже получает указатель на объект. Указатель, а не объект, на который он указывает, передается по значению. Передача по значению означает, что метод не может изменить указатель, чтобы он указывал на новый экземпляр ссылочного типа, но может изменить содержимое объекта, на который он указывает. Для большинства приложений это достаточно и дает вам необходимое поведение.

 Если метод должен возвращать другой экземпляр, используйте для этого возвращаемое значение метода. См <xref:System.String?displayProperty=fullName> . класс для различных методов, которые работают с строками и возвращают новый экземпляр строки. Эта модель позволяет вызывающему объекту решить, сохраняется ли исходный объект.

 Хотя возвращаемые значения являются наиболее распространенными и часто используются, правильное применение `out` и `ref` параметры требуют промежуточных навыков проектирования и программирования. Архитекторы библиотек, которые разрабатывается для общей аудитории, не должны ждать, чтобы пользователи работали с главными рабочими `out` `ref` параметрами или.

> [!NOTE]
> При работе с параметрами, которые являются большими структурами, дополнительные ресурсы, необходимые для копирования этих структур, могут вызвать воздействие на производительность при передаче по значению. В таких случаях можно использовать `ref` `out` Параметры или.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, вызванное типом значения, метод должен вернуть объект в качестве возвращаемого значения. Если метод должен возвращать несколько значений, перепроектирование его для возврата одного экземпляра объекта, содержащего значения.

 Чтобы устранить нарушение этого правила, вызванное ссылочным типом, убедитесь, что требуемое поведение возвращает новый экземпляр ссылки. Если это так, метод должен использовать его возвращаемое значение для этого.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Можно спокойно отключить предупреждение из этого правила. Однако такая схема может вызвать проблемы с удобством использования.

## <a name="example"></a>Пример
 В следующей библиотеке показаны две реализации класса, которые создают ответы на отзыв пользователя. Первая реализация ( `BadRefAndOut` ) заставляет пользователя библиотеки управлять тремя возвращаемыми значениями. Вторая реализация ( `RedesignedRefAndOut` ) упрощает взаимодействие с пользователем, возвращая экземпляр класса контейнера ( `ReplyData` ), который управляет данными как единым целым.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Пример
 В следующем приложении показана работа пользователя. Вызов переработанной библиотеки ( `UseTheSimplifiedClass` метода) более прост, и сведения, возвращаемые методом, легко управляются. Выходные данные двух методов идентичны.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Пример
 В следующем примере библиотеки показано `ref` , как используются параметры для ссылочных типов, и демонстрируется лучший способ реализации этой функции.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Пример
 Следующее приложение вызывает каждый метод в библиотеке, чтобы продемонстрировать поведение.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 В этом примере формируются следующие данные:

 **Изменение указателя, передаваемого по значению:** 
 **12345** 
 **12345** 
 **Изменение указателя, передаваемого по ссылке:** 
 **12345** 
 **12345 ABCD** 
 **Передача по возвращаемому значению:** 
 **12345 ABCD**
## <a name="related-rules"></a>Связанные правила
 [CA1021. Не используйте параметры out](../code-quality/ca1021-avoid-out-parameters.md)
