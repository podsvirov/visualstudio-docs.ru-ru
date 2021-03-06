---
title: dwTYPE_KIND | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737192"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Указывает способ интерпретации типа объекта [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) .

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Поля
`TYPE_KIND_METADATA`\
[TYPE_INFOное](../../../extensibility/debugger/reference/type-info.md) объединение должно интерпретироваться как структура [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) .

`TYPE_KIND_PDB`\
`TYPE_INFO`Объединение должно интерпретироваться как структура [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) .

`TYPE_KIND_BUILT`\
`TYPE_INFO`Объединение должно интерпретироваться как структура [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) .

## <a name="remarks"></a>Remarks
Значения этого перечисления отображаются в `dwKind` поле структуры [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) и используются для определения способа интерпретации `type` элемента объединения. `TYPE_INFO`Структура возвращается вызовом метода [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) .

## <a name="requirements"></a>Требования
Заголовок: sh. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
