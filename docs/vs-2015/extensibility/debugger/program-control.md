---
title: Управление программой | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 6be80904-e66c-4cae-8891-1113b799fb01
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8102bc488d5c74f751fb93584016aa6904fbe2d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842681"
---
# <a name="program-control"></a>Элемент управления программой
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В отладке Visual Studio все следующие пошаговые и продолжающиеся подпрограммы выполняются на уровне программы:  
  
- Задание следующего оператора, то есть перевод компьютера в следующую инструкцию для выполнения в определенной среде кадров  
  
- Выполнение, то есть продолжение выхода из режима пошагового выполнения  
  
- Шаг с заходом в следующую инструкцию  
  
- Продолжение текущего режима пошагового выполнения  
  
- Приостановка потоков, содержащихся в программе  
  
- Возобновление потоков, содержащихся в программе  
  
> [!NOTE]
> Просмотр стека вызовов реализуется на уровне потока. Чтобы перечислить сведения о кадрах при просмотре стека вызовов для потока, необходимо реализовать все методы интерфейса [IEnumDebugFrameInfo2](../../extensibility/debugger/reference/ienumdebugframeinfo2.md) .  
  
## <a name="methods-of-program-control"></a>Методы управления программой  
 В следующей таблице показаны методы [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , которые должны быть реализованы для минимально функционального модуля отладки (de) и управления выполнением.  
  
|Метод|Description|  
|------------|-----------------|  
|[IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)|Возобновляет выполнение всех потоков, содержащихся в программе, из остановленного состояния. Требуется для управления выполнением.|  
|[IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)|Возобновляет выполнение всех потоков, содержащихся в программе, из остановленного состояния. Требуется для управления выполнением.|  
|[IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)|Выполняет шаг в заданном потоке. Возобновляет выполнение всех остальных потоков, содержащихся в программе. Требуется для управления выполнением.|  
  
 Для многопоточных программ также необходимо реализовать метод [IDebugProgram2:: EnumThreads](../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) и все методы интерфейса [IEnumDebugThreads2](../../extensibility/debugger/reference/ienumdebugthreads2.md) .  
  
## <a name="see-also"></a>См. также:  
 [Элемент управления выполнением и анализ состояния](../../extensibility/debugger/execution-control-and-state-evaluation.md)
