---
title: IDebugReference2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac7e825bd33c184d580ada96843366f6d1627f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842444"
---
# <a name="idebugreference2"></a>IDebugReference2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет ссылку на свойство кадра стека или другое свойство.  
  
> [!NOTE]
> `IDebugReference2` зарезервировано для будущего использования, и все его методы должны возвращать `E_NOTIMPL` .  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugReference2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Метод DE реализует этот интерфейс для представления ссылки на определенный тип значения. Например, значение может быть числовым значением в результате вычисления выражения, контекста памяти, используемого для отображения памяти, или списка регистров и их значений.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Чтобы получить этот интерфейс, вызовите метод [IsReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) . [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) [Жетдериведмостреференце](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) также возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugReference2` .  
  
|Метод|Description|  
|------------|-----------------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Возвращает структуру [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , описывающую эту ссылку.|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Задает значение этой ссылки из строки.|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Задает значение этой ссылки из другой ссылки.|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Перечисляет дочерние элементы этой ссылки.|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Возвращает родительский объект для этой ссылки.|  
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Возвращает наиболее производную ссылку на эту ссылку.|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Возвращает байты памяти, к которым относится эта ссылка.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Возвращает контекст памяти для этой ссылки.|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Возвращает размер этой ссылки в байтах.|  
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Задает этот тип ссылки.|  
|[Сравнить](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Сравнивает эту ссылку с другой.|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> Использование "Свойства" не следует путать с тем, что это означает переменную-член класса, хотя `IDebugReference2` может представлять такую сущность.  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) представляет свойство, а `IDebugReference2` представляет ссылку на свойство, как правило, ссылка на объект в отлаживаемой программе.  
  
 Основное различие между свойством и ссылкой состоит в том, что свойство ссылается на именованный экземпляр объекта, а ссылка ссылается на безымянный экземпляр. Например, свойство может ссылаться на объект в куче программы с помощью `"a.b"` . Другое свойство может ссылаться на тот же объект, что и `"c.d"` . Для обращения к этому свойству необходимо, чтобы `"a.b"` `"c.d"` в области было указано значение или. Ссылка на этот же объект не имеет имени; на объект можно ссылаться до тех пор, пока память для этого объекта является допустимой.  
  
 `IDebugProperty2`Интерфейс можно рассматривать как значение с именем, типом и адресом. `IDebugReference2`, С другой стороны, можно рассматривать как тип и адрес.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
