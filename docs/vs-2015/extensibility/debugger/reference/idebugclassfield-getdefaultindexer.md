---
title: 'Идебугклассфиелд:: Жетдефаултиндексер | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::GetDefaultIndexer
helpviewer_keywords:
- IDebugClassField::GetDefaultIndexer method
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6be0a1925a1e5d48941c1c0e13ac1b4789687229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191018"
---
# <a name="idebugclassfieldgetdefaultindexer"></a>IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя индексатора по умолчанию.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```csharp  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrIndexer`  
 заполняет Возвращает строку, содержащую имя индексатора по умолчанию.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK или возвращает значение S_FALSE, если индексатор по умолчанию отсутствует. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Индексатором по умолчанию для класса является свойство, которое помечено как `Default` свойство для доступа к массиву. Это относится только к [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] . Ниже приведен пример индексатора по умолчанию, объявленного в [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] и его использования.  
  
```vb  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## <a name="see-also"></a>См. также:  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
