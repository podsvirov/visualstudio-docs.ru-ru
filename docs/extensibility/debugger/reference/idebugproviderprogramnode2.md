---
title: IDebugProviderProgramNode2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 815a945f6fb591960ebf0bf4b4fcd9d842ffefd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720678"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Этот интерфейс маршалирует интерфейсы, связанные с программой, между границами процессов.

## <a name="syntax"></a>Синтаксис

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для того же объекта, который реализует [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) для поддержки интерфейсов упаковки через границы процесса.

## <a name="notes-for-callers"></a>Примечания для вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) для `IDebugProgramNode2` интерфейса, чтобы получить этот интерфейс. Если этот интерфейс получить нельзя, параметр DE не поддерживает упаковку интерфейсов.

## <a name="methods-in-vtable-order"></a>Методы в порядке vtable
 Этот интерфейс реализует следующий метод:

|Метод|Описание|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|Возвращает указанный интерфейс между границами процесса.|

## <a name="remarks"></a>Remarks
 Этот интерфейс реализуется, когда DE выполняется в отдельном пространстве процесса из отлаживаемой программы: например, когда DE выполняется в пространстве процесса Visual Studio, а не в пространстве процесса отлаживаемой программы.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
