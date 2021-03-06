---
title: Идебугалиас | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAlias
helpviewer_keywords:
- IDebugAlias interface
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6c05b6987804681176abdde0e8c94a7463a9163c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842644"
---
# <a name="idebugalias"></a>IDebugAlias
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Представляет числовой псевдоним для переменной. Псевдоним — это просто другое имя для переменной.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugAlias : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений (EE) реализует этот интерфейс для поддержки числовых псевдонимов переменных.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [Креатеалиас](../../../extensibility/debugger/reference/idebugobject2-createalias.md) создает псевдоним для определенного объекта. Чтобы найти псевдонимы, используйте [финдалиас](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) или [жеталлалиасес](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md).  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В интерфейсе определены следующие методы `IDebugAlias` .  
  
|Метод|Description|  
|------------|-----------------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|Возвращает объект, к которому относится этот псевдоним.|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|Возвращает имя псевдонима.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|Извлекает `ICorDebugValue` интерфейс, предоставляющий доступ к информации управляемого кода об этом объекте (только управляемый код).|  
|[Dispose](../../../extensibility/debugger/reference/idebugalias-dispose.md)|Помечает этот псевдоним как более не используемый.|  
  
## <a name="remarks"></a>Remarks  
 Псевдоним представляет собой десятичное число в виде строки, за которым следует символ #, например, 1001 #.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы оценки выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [креатеалиас](../../../extensibility/debugger/reference/idebugobject2-createalias.md)   
 [финдалиас](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)
