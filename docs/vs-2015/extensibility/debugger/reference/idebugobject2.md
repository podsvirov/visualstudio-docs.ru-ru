---
title: IDebugObject2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 979ede5601f1f31ca972bb9067b626954b1296f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695199"
---
# <a name="idebugobject2"></a>IDebugObject2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
> В Visual Studio 2015 такой способ реализации оценивающих выражений является устаревшим. Дополнительные сведения о реализации вычислителей выражений CLR см. в разделе средства [оценки выражений CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) и [Пример управляемого средства оценки выражений](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Этот интерфейс предоставляет дополнительные сведения об объекте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс, чтобы обеспечить поддержку псевдонимов и доступа к сведениям об объекте.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Интерфейс [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) может получить этот интерфейс с помощью [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3). Кроме того, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
 В дополнение к методам в интерфейсе [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) `IDebugObject2` интерфейс реализует следующее:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Возвращает поле или переменную (если есть), которые могут быть резервными копиями свойства, представленного этим объектом.|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Возвращает объект управляемого кода, представляющий значение этого объекта.|  
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Создает уникальный идентификатор для этого объекта или возвращает существующий псевдоним.|  
|[Псевдоним](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Возвращает псевдоним, связанный с этим объектом, если он есть.|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Возвращает тип этого объекта.|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Определяет, представляет ли этот объект данные пользователя.|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Определяет, является ли состояние "Изменить" и "продолжить" более допустимым.<br /><br /> Пользовательский оценщик выражений не реализует этот метод (он должен всегда возвращать `E_NOTIMPL` ).|  
  
## <a name="remarks"></a>Remarks  
 См. раздел [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md) для обсуждения псевдонимов.  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы оценки выражений](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md)   
 [идебугалиас](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)
