---
title: 'Идебугженерикпарамфиелд:: Жетнамеофформалпарам | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugGenericParamField::GetNameOfFormalParam
- GetNameOfFormalParam
ms.assetid: 05032a83-49ce-4007-b5d6-7b56945b956c
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eb18022aa72b0384ce55c6febb0bca2d193c890a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180692"
---
# <a name="idebuggenericparamfieldgetnameofformalparam"></a>IDebugGenericParamField::GetNameOfFormalParam
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя этого универсального параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetNameOfFormalParam (  
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetNameOfFormalParam (  
   string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrName`  
 заполняет Имя этого универсального параметра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для объекта **кдебугженерикпарамфиелдтипе** , предоставляющего интерфейс [идебугженерикпарамфиелд](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .  
  
```cpp#  
HRESULT CDebugGenericParamFieldType::GetNameOfFormalParam(BSTR *pbstrName)  
{  
    HRESULT hr = S_OK;  
    CComBSTR bstrName;  
  
    METHOD_ENTRY( CDebugGenericParamFieldType::GetNameOfFormalParam );  
  
    IfFalseGo( pbstrName, E_INVALIDARG );  
    IfFailGo( this->LoadProps() );  
    IfNullGo( *pbstrName = SysAllocString(m_bstrName), E_OUTOFMEMORY );  
  
Error:  
  
    METHOD_EXIT( CDebugGenericParamFieldType::GetNameOfFormalParam, hr );  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
