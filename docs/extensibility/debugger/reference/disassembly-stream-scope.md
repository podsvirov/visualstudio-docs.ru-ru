---
title: DISASSEMBLY_STREAM_SCOPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DISASSEMBLY_STREAM_SCOPE
helpviewer_keywords:
- DISASSEMBLY_STREAM_SCOPE enumeration
ms.assetid: 43e2b364-cbbe-4755-a7e6-a03f3054c965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fae1f22c6db22cd6cff93cfb1b98a28620a1537c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737269"
---
# <a name="disassembly_stream_scope"></a>DISASSEMBLY_STREAM_SCOPE
Задает область потока дизассемблированного кода.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
typedef DWORD DISASSEMBLY_STREAM_SCOPE;
```

```csharp
public enum enum_DISASSEMBLY_STREAM_SCOPE {
    DSS_HUGE     = 0x10000000,
    DSS_FUNCTION = 0x0001,
    DSS_MODULE   = (DSS_HUGE) | 0x0002,
    DSS_ALL      = (DSS_HUGE) | 0x0003
};
```

## <a name="fields"></a>Поля
`DSS_HUGE`\
Указывает, что при разсборке контекста кода будет создаваться больше выходных данных, чем клиент, как правило, в одном вызове.

`DSS_FUNCTION`\
Указывает, что функция, содержащаяся в контексте кода, должна быть собрана. Указывает, что поток дизассемблированного кода представляет функцию, возвращаемую методом [superscope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

`DSS_MODULE`\
При возврате `IDebugDisassemblyStream2::GetScope` методом указывает, что поток дизассемблированного кода представляет модуль.

`DSS_ALL`\
Указывает Дизассемблированный код для всего адресного пространства.

## <a name="remarks"></a>Remarks
Передается в качестве аргумента в метод [жетдисассемблистреам](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) и возвращается методом [superscope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md) .

Эти значения можно объединить с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)
