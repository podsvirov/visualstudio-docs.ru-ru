---
title: 'CA1901: объявления P-Invoke должны быть переносимыми | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e669d87ad5ecc53c1523db16ab77578c6a703a33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545266"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: объявления P/Invoke должны быть переносимыми
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Категория|Microsoft. переносимость|
|Критическое изменение|Критическое — если P/Invoke видим за пределами сборки. Не критическое — если P/Invoke не виден за пределами сборки.|

## <a name="cause"></a>Причина
 Это правило оценивает размер каждого параметра и возвращаемое значение P/Invoke и проверяет, что их размер при маршалировании в неуправляемый код на 32-разрядных и 64-разрядных платформах является правильным. Наиболее распространенным нарушением этого правила является передача целого числа фиксированного размера, где требуется зависящая от платформы переменная с размером указателя.

## <a name="rule-description"></a>Описание правила
 В одном из следующих сценариев происходит нарушение этого правила:

- Возвращаемое значение или параметр вводится как целое число фиксированного размера, если его необходимо ввести как `IntPtr` .

- Возвращаемое значение или параметр типизировано как, `IntPtr` если его необходимо ввести как целое число с фиксированным размером.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Это нарушение можно устранить с помощью `IntPtr` или `UIntPtr` для представления дескрипторов вместо `Int32` или `UInt32` .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Не следует отключать это предупреждение.

## <a name="example"></a>Пример
 В следующем примере показано нарушение этого правила.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 В этом примере `nIconIndex` параметр объявляется как `IntPtr` , который имеет ширину 4 байта на 32-разрядной платформе и 8 байт в ширину на 64-разрядной платформе. В объявлении неуправляемого кода ниже видно, что `nIconIndex` — это 4-байтовое целое число без знака на всех платформах.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Пример
 Чтобы устранить нарушение, измените объявление на следующее:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>См. также:
 [Предупреждения переносимости](../code-quality/portability-warnings.md)
