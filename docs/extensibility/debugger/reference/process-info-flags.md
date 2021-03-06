---
title: PROCESS_INFO_FLAGS | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PROCESS_INFO_FLAGS
helpviewer_keywords:
- PROCESS_INFO_FLAGS enumeration
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 36c4cbbe17a109eacd69b76500e8c10d21d2d554
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713963"
---
# <a name="process_info_flags"></a>PROCESS_INFO_FLAGS

Описывает или задает свойства процесса.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
typedef DWORD PROCESS_INFO_FLAGS;
```

```csharp
enum enum_PROCESS_INFO_FLAGS { 
   PIFLAG_SYSTEM_PROCESS    = 0x00000001,
   PIFLAG_DEBUGGER_ATTACHED = 0x00000002,
   PIFLAG_PROCESS_STOPPED   = 0x00000004,
   PIFLAG_PROCESS_RUNNING   = 0x00000008,
};
```

## <a name="fields"></a>Поля

`PIFLAG_SYSTEM_PROCESS`\
Указывает, что процесс является системным процессом.

`PIFLAG_DEBUGGER_ATTACHED`\
Указывает, что процесс отлаживается отладчиком. Это может быть [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] отладчик или некоторый другой отладчик, например WinDbg.

`PIFLAG_PROCESS_STOPPED`\
Указывает, что процесс остановлен. Допустимо, только если `PIFLAG_DEBUGGER_ATTACHED` также указано значение. Доступно в Visual Studio 2005 и более поздних версиях.

`PIFLAG_PROCESS_RUNNING`\
Указывает, что процесс выполняется. Допустимо, только если `PIFLAG_DEBUGGER_ATTACHED` также указано значение. Доступно в Visual Studio 2005 и более поздних версиях.

## <a name="remarks"></a>Remarks

Используется для `Flags` элемента структуры [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) .

Эти флаги можно сочетать с помощью побитовой операции `OR` .

## <a name="requirements"></a>Требования

Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)
