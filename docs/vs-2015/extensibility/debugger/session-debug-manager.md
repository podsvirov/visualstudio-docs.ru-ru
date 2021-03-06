---
title: Диспетчер отладки сеансов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157824"
---
# <a name="session-debug-manager"></a>Диспетчер отладки сеансов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Диспетчер отладки сеансов (SDM) управляет любым количеством отладочных модулей (DE) отладки любого количества программ в нескольких процессах на любом количестве компьютеров. В дополнение к мультиплексору модуля отладки, модель SDM предоставляет унифицированное представление сеанса отладки в интегрированной среде разработки.  
  
## <a name="session-debug-manager-operation"></a>Операция диспетчера отладки сеанса  
 Диспетчер отладки сеансов (SDM) управляет DE. На компьютере может одновременно выполняться несколько отладочных модулей. Для мультиплексирования DEs модель SDM упаковывает ряд интерфейсов из алгоритма DEs и предоставляет их в интегрированной среде разработки как единый интерфейс.  
  
 Для повышения производительности некоторые интерфейсы не мультиплексированы. Вместо этого они используются непосредственно из DE, а вызовы к этим интерфейсам не проходят через SDM. Например, интерфейсы, используемые для памяти, кода и контекстов документов, не являются мультиплексированными, так как они ссылаются на определенную инструкцию, память или документ в определенной программе, отлаживаемой с помощью определенного DE. Не нужно участвовать в этом уровне связи.  
  
 Это неверно для всех контекстов. Вызовы интерфейса контекста вычисления выражения проходят через SDM. Во время оценки выражения модель SDM создает оболочку для интерфейса [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , который он предоставляет интегрированной среде разработки, поскольку при вычислении этого выражения может потребоваться несколько алгоритмов DEs, которые являются отладкой программ в том же процессе, который может выполняться в одном потоке.  
  
 Модель SDM обычно выступает в качестве механизма делегирования, но может выступать в качестве механизма вещания. Например, во время оценки выражения модель SDM выступает в качестве механизма вещания для уведомления всех алгоритмов DEs о том, что они могут выполнять код в указанном потоке. Аналогично, когда SDM получает событие остановки, оно передается во все программы, которые должны прекратить работу. При вызове этапа SDM передается на все программы, которые они могут продолжать выполнять. Точки останова также передаются в каждый де.  
  
 Модель SDM не следит за текущей программой, потоком или кадром стека. Сведения о процессе, программе и потоке отправляются в SDM в сочетании с конкретными событиями отладки.  
  
## <a name="see-also"></a>См. также:  
 [Модуль отладки](../../extensibility/debugger/debug-engine.md)   
 [Компоненты отладчика](../../extensibility/debugger/debugger-components.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)
