---
title: 'IDebugProgram2:: Енумкодеконтекстс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::EnumCodeContexts
helpviewer_keywords:
- IDebugProgram2::EnumCodeContexts
ms.assetid: 478e06a2-07bb-4841-8887-deab0f42ebd0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 26bd68764b94aadccb796f33d127ba159e9c3727
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202760"
---
# <a name="idebugprogram2enumcodecontexts"></a>IDebugProgram2::EnumCodeContexts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает список контекстов кода для заданной позицией в исходном файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT EnumCodeContexts(   
   IDebugDocumentPosition2*  pDocPos,  
   IEnumDebugCodeContexts2** ppEnum  
);  
```  
  
```csharp  
int EnumCodeContexts(   
   IDebugDocumentPosition2     pDocPos,  
   out IEnumDebugCodeContexts2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pDocPos`  
 окне Объект [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) , представляющий абстрактное расположение в исходном файле, известном интегрированной среде разработки.  
  
 `ppEnum`  
 заполняет Возвращает объект [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md) , содержащий список контекстов кода.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод позволяет диспетчеру отладки сеансов (SDM) или интегрированной среде разработки сопоставлять расположение исходного файла с позицией в коде. Если источник создает несколько блоков кода (например, шаблоны C++), возвращается более одного контекста кода.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
