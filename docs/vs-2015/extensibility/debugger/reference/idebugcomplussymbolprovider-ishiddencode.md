---
title: 'Идебугкомплуссимболпровидер:: Ишидденкоде | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider::IsHiddenCode
ms.assetid: 1352c6ab-7b92-4a16-b2d2-6520b628830e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ecbd7aaa05b48efcf43bb299c9c3dc2be9c679ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187206"
---
# <a name="idebugcomplussymbolproviderishiddencode"></a>IDebugComPlusSymbolProvider::IsHiddenCode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет, скрыт ли код в указанном адресе отладчика.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT IsHiddenCode(  
   IDebugAddress* pAddress  
);  
```  
  
```csharp  
int IsHiddenCode(  
   IDebugAddress pAddress  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pAddress`  
 окне Адрес отладки, представленный интерфейсом [идебугаддресс](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если код скрыт, возвращает `S_OK` ; в противном случае возвращает `S_FALSE` .  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для объекта **кдебугсимболпровидер** , предоставляющего интерфейс [идебугкомплуссимболпровидер](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) .  
  
```cpp#  
HRESULT CDebugSymbolProvider::IsHiddenCode(  
    IDebugAddress* pAddress  
)  
{  
    HRESULT hr = S_OK;  
    CDEBUG_ADDRESS address;  
    CComPtr<CModule> pModule;  
  
    ASSERT(IsValidObjectPtr(this, CDebugSymbolProvider));  
    ASSERT(IsValidInterfacePtr(pAddress, IDebugAddress));  
  
    METHOD_ENTRY( CDebugSymbolProvider::IsHiddenCode );  
  
    IfFalseGo( pAddress, S_FALSE );  
    IfFailGo( pAddress->GetAddress( &address ) );  
  
    ASSERT(address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD);  
    IfFalseGo( address.addr.dwKind == ADDRESS_KIND_METADATA_METHOD, S_FALSE );  
  
    IfFailGo( GetModule( address.GetModule(), &pModule) );  
  
    if (!pModule->IsHiddenCode( address.addr.addr.addrMethod.tokMethod,  
                                address.addr.addr.addrMethod.dwVersion,  
                                address.addr.addr.addrMethod.dwOffset ))  
    {  
  
        // S_FALSE indicates this sequence point is not hidden  
  
        hr = S_FALSE;  
    }  
  
Error:  
  
    METHOD_EXIT( CDebugSymbolProvider::IsHiddenCode, hr );  
  
    if (!SUCCEEDED(hr))  
    {  
        hr = S_FALSE;  
    }  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)
