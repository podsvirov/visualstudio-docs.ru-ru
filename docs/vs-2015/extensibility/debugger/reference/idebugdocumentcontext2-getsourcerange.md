---
title: 'IDebugDocumentContext2:: GetSourceRange | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcec6af2b8e7b1acfdc9c3cf38cb18654be78c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145005"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает диапазон исходного кода этого контекста документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pBegPosition`  
 [вход, выход] Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , которая заполняется начальной позицией. Присвойте этому аргументу значение null, если эти сведения не требуются.  
  
 `pEndPosition`  
 [вход, выход] Структура [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , которая заполняется конечной позицией. Присвойте этому аргументу значение null, если эти сведения не требуются.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Исходный диапазон — это весь диапазон исходного кода от текущего оператора до предыдущего оператора, который участвовал в коде. Исходный диапазон обычно используется для смешивания инструкций источника, включая комментарии, с кодом в окне дизассемблирования.  
  
 Чтобы получить диапазон только для операторов кода, содержащихся в данном контексте документа, вызовите метод [жетстатементранже](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [жетстатементранже](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
