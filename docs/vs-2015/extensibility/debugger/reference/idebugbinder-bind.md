---
title: 'Идебугбиндер:: BIND | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 547f94cb4534bcb281cce0fdc2ff7db5fefe3593
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62423547"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод получает контекст памяти или объект, который содержит текущее значение символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Bind(   
   IDebugObject*  pContainer,  
   IDebugField*   pField,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int Bind(  
   IDebugObject     pContainer,  
   IDebugField      pField,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pContainer`  
 окне [Идебугобжект](../../../extensibility/debugger/reference/idebugobject.md) , содержащий дочерний элемент, на который ссылается `pField` .  
  
 `pField`  
 окне [Идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , представляющий символ.  
  
 `ppObject`  
 заполняет Возвращает объект `IDebugObject` , представляющий экземпляр символа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идебугбиндер](../../../extensibility/debugger/reference/idebugbinder.md)   
 [идебугобжект](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
