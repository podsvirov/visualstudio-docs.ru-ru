---
title: Требуемые интерфейсы поставщика портов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers, required interfaces
- debugging [Debugging SDK], port suppliers
ms.assetid: 0c2cdd40-9f6f-425e-b305-858f7734161e
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a065389a6b9b67b8bce82394569ce65afb0f8d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821437"
---
# <a name="required-port-supplier-interfaces"></a>Интерфейс поставщика необходимого порта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Поставщик порта должен реализовывать интерфейс [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) . [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)  
  
 Так как поставщик порта предоставляет порты, он также должен реализовывать их. Поэтому он должен реализовывать следующие интерфейсы:  
  
- [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)  
  
     Описывает порт и может перечислить все процессы, запущенные в порте.  
  
- [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md)  
  
     Предоставляет для запуска и завершения процессов в порте.  
  
- [IDebugPortNotify2](../../extensibility/debugger/reference/idebugportnotify2.md)  
  
     Предоставляет механизм для программ, выполняющихся в контексте этого порта, для уведомления о создании и уничтожении узлов программы. Дополнительные сведения см. в разделе [Program Nodes](../../extensibility/debugger/program-nodes.md).  
  
- `IConnectionPointContainer`  
  
     Предоставляет точку подключения для [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md).  
  
## <a name="port-supplier-operation"></a>Операция поставщика порта  
 Приемник [IDebugPortEvents2](../../extensibility/debugger/reference/idebugportevents2.md) получает уведомления при создании и удалении процессов и программ в порте. Порт требуется для отправки [IDebugProcessCreateEvent2](../../extensibility/debugger/reference/idebugprocesscreateevent2.md) при создании процесса и [IDebugProcessDestroyEvent2](../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) при уничтожении процесса в порте. Порт также требуется для отправки [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) при создании программы и [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) при удалении программы в процессе, работающем в порте.  
  
 Порт обычно отправляет в ответ на методы [аддпрограмноде](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) и [ремовепрограмноде](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , соответственно, события создания и уничтожения программы.  
  
 Поскольку порт может запускать и завершать как физические процессы, так и логические программы, эти интерфейсы также должны быть реализованы модулем отладки:  
  
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)  
  
  Описывает физический процесс. Необходимо реализовать по крайней мере следующие методы:  

  - [EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)  

  - [GetName](../../extensibility/debugger/reference/idebugprocess2-getname.md)  

  - [GetServer](../../extensibility/debugger/reference/idebugprocess2-getserver.md)  

  - [GetPhysicalProcessId](../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  

  - [GetProcessId](../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)  

  - [GetAttachedSessionName](../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)  

- [IDebugProcessEx2](../../extensibility/debugger/reference/idebugprocessex2.md)  
  
    Предоставляет модель SDM для присоединения и отсоединения от процесса.  
  
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)  
  
  Описывает логическую программу. Необходимо реализовать по крайней мере следующие методы:  

  - [GetName](../../extensibility/debugger/reference/idebugprogram2-getname.md)  

  - [GetProcess](../../extensibility/debugger/reference/idebugprogram2-getprocess.md)  

  - [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)  
  
- [IDebugProgramEx2](../../extensibility/debugger/reference/idebugprogramex2.md)  
  
     Предоставляет способ для присоединения SDM к этой программе.  
  
## <a name="see-also"></a>См. также:  
 [Реализация поставщика порта](../../extensibility/debugger/implementing-a-port-supplier.md)
