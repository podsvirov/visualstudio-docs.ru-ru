---
title: CONNECTION_PROTOCOL | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80737648"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Указывает протокол, используемый для обмена данными между сервером отладки и пакетом отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Поля
`CONNECTION_NONE`\
Не установлено соединение с сервером.

`CONNECTION_UNKNOWN`\
Соединение установлено, но имеет неизвестный тип.

`CONNECTION_LOCAL`\
Подключение к локальному серверу.

`CONNECTION_PIPE`\
Соединение осуществляется через именованный канал.

`CONNECTION_TCPIP`\
Подключение использует TCP/IP.

`CONNECTION_HTTP`\
Соединение использует HTTP (через веб-сервер).

`CONNECTION_OTHER`\
Установлен другой тип соединения (это значение в настоящее время не используется).

## <a name="remarks"></a>Remarks
Эти значения возвращаются методом [жетконнектионпротокол](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) .

## <a name="requirements"></a>Требования
Заголовок: мсдбг. h

Пространство имен: Microsoft. VisualStudio. Debugger. Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
