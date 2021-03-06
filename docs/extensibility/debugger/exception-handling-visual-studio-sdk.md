---
title: Обработка исключений (пакет SDK для Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], exception handling
ms.assetid: 7279dc16-db14-482c-86b8-7b3da5a581d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34b83c7181a7ba405e642d9911e2c53df3f4401d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738762"
---
# <a name="exception-handling-visual-studio-sdk"></a>Обработка исключений (пакет SDK для Visual Studio)
Ниже описан процесс, который происходит при возникновении исключений.

## <a name="exception-handling-process"></a>Процесс обработки исключений

1. При первом вызове исключения, но перед его обработкой обработчика исключений в отлаживаемой программе модуль отладки (DE) отправляет [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) в Диспетчер отладки сеансов (SDM) в качестве события остановки. `IDebugExceptionEvent2`Отправляется, если только параметры исключения (заданные в диалоговом окне исключения в пакете отладки) указывают, что пользователю нужно останавливаться на уведомлениях о первом экземпляре исключения.

2. Модель SDM вызывает [IDebugExceptionEvent2:: except](../../extensibility/debugger/reference/idebugexceptionevent2-getexception.md) , чтобы получить свойство исключения.

3. Пакет отладки вызывает [IDebugExceptionEvent2:: канпасстодебугжее](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) , чтобы определить, какие параметры необходимо предоставить пользователю.

4. Пакет отладки запрашивает у пользователя способ обработки исключения, открыв диалоговое окно первый экземпляр исключения.

5. Если пользователь решит продолжить, SDM вызывает [IDebugExceptionEvent2:: канпасстодебугжее](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md).

    - Если метод возвращает S_OK, вызывается [IDebugExceptionEvent2::P асстодебугжее](../../extensibility/debugger/reference/idebugexceptionevent2-passtodebuggee.md).

         -или-

         Если метод возвращает S_FALSE, то отлаживаемая программа получает вторую шанс обработки исключения.

6. Если отлаживаемая программа не имеет обработчика для второго шанса исключения, параметр DE отправляет `IDebugExceptionEvent2` в SDM **EVENT_SYNC_STOP**.

7. Пакет отладки запрашивает у пользователя способ обработки исключения, открыв диалоговое окно первый экземпляр исключения.

8. Пакет отладки вызывает [IDebugExceptionEvent2:: канпасстодебугжее](../../extensibility/debugger/reference/idebugexceptionevent2-canpasstodebuggee.md) , чтобы определить, какие параметры необходимо предоставить пользователю.

9. Пакет отладки запрашивает у пользователя способ обработки исключения, открыв диалоговое окно второй-шанс исключения.

10. Если метод возвращает S_OK, вызывает `IDebugExceptionEvent2::PassToDebuggee` .

## <a name="see-also"></a>См. также раздел
- [События отладчика Call](../../extensibility/debugger/calling-debugger-events.md)
