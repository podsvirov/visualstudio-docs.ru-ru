---
title: 'IDebugDisassemblyStream2:: Seek | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::Seek
helpviewer_keywords:
- IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4954b3b278b3c7a6b798a4ffda3856ab8bb200c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732083"
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Перемещает указатель чтения в потоке дизассемблирования на указанное количество инструкций относительно указанной позиции.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT Seek( 
   SEEK_START          dwSeekStart,
   IDebugCodeContext2* pCodeContext,
   UINT64              uCodeLocationId,
   INT64               iInstructions
);
```

```csharp
int Seek( 
   enum_SEEK_START    dwSeekStart,
   IDebugCodeContext2 pCodeContext,
   ulong              uCodeLocationId,
   long               iInstructions
);
```

## <a name="parameters"></a>Параметры
`dwSeekStart`\
окне Значение из перечисления [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) , указывающее относительное положение для начала процесса поиска.

`pCodeContext`\
окне Объект [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) , представляющий контекст кода, относительно которого выполняется операция поиска. Этот параметр используется только в том случае `dwSeekStart`  =  `SEEK_START_CODECONTEXT` , если; в противном случае этот параметр игнорируется и может иметь значение null.

`uCodeLocationId`\
окне Идентификатор расположения кода, относительно которого выполняется операция поиска. Этот параметр используется, если `dwSeekStart`  =  `SEEK_START_CODELOCID` ; в противном случае этот параметр игнорируется и может иметь значение 0. Описание идентификатора расположения кода см. в разделе "Примечания" для метода [жеткоделокатионид](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) .

`iInstructions`\
окне Количество инструкций, которые нужно переместить относительно положения, указанного в параметре `dwSeekStart` . Это значение может быть отрицательным для перемещения назад.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK`. Возвращает значение, `S_FALSE` если положение поиска находилось до точки, находящейся за пределами списка доступных инструкций. В противном случае возвращается код ошибки.

## <a name="remarks"></a>Remarks
 Если поиск осуществлялся до начала списка, то в качестве места чтения устанавливается первая инструкция в списке. Если точка просмотра находится в положении после конца списка, то в качестве места чтения устанавливается Последняя инструкция в списке.

## <a name="see-also"></a>См. также раздел
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
