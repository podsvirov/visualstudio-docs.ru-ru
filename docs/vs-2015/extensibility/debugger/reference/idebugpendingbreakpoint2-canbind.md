---
title: 'IDebugPendingBreakpoint2:: Канбинд | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::CanBind
helpviewer_keywords:
- IDebugPendingBreakpoint2::CanBind method
- CanBind method
ms.assetid: 84a2b189-ccf1-467e-8fab-0c0da68f0b91
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4e22da57eb5cc286bee18601079ea39da1b7b48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68143801"
---
# <a name="idebugpendingbreakpoint2canbind"></a>IDebugPendingBreakpoint2::CanBind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет, может ли отложенная точка останова быть привязана к расположению кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT CanBind (   
   IEnumDebugErrorBreakpoints2** ppErrorEnum  
);  
```  
  
```csharp  
int CanBind (   
   out IEnumDebugErrorBreakpoints2 ppErrorEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppErrorEnum`  
 заполняет Возвращает объект [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) , содержащий список объектов [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) , если могут возникнет ошибки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает значение, `S_OK.` `S_FALSE` Если точка останова не может выполнить привязку, в этом случае ошибки возвращаются `ppErrorEnum` параметром. В противном случае возвращается код ошибки. Возвращает значение `E_BP_DELETED` , если точка останова была удалена.  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается для определения того, что произойдет, если была выполнена привязка ожидающей точки останова. Вызовите метод [BIND](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) для фактической привязки ожидающей точки останова.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для простого `CPendingBreakpoint` объекта, предоставляющего интерфейс [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .  
  
```cpp#  
HRESULT CPendingBreakpoint::CanBind(IEnumDebugErrorBreakpoints2** ppErrorEnum)    
{    
   HRESULT hr;    
   HRESULT hrT;    
  
   // Check for a valid pointer to an error breakpoint enumerator   
   // interface; otherwise, return hr = E_INVALIDARG.    
   if (ppErrorEnum)    
   {    
      // Verify that the pending breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state.state != PBPS_DELETED)    
      {    
         // Verify that the breakpoint is a file/line breakpoint.    
         if (IsFlagSet(m_pBPRequest->m_bpRequestInfo.dwFields, BPREQI_BPLOCATION) &&  
             m_pBPRequest->m_bpRequestInfo.bpLocation.bpLocationType == BPLT_CODE_FILE_LINE)    
         {    
            hr = S_OK;    
         }    
         // If the breakpoint type is not a file/line breakpoint, then the   
         // result should be an error breakpoint.    
         else    
         {    
            // If the error breakpoint member variable does not have   
            // allocated memory.  
            if (!m_pErrorBP)    
            {    
               // Create, AddRef, and initialize a CErrorBreakpoint object.    
               if (CComObject<CErrorBreakpoint>::CreateInstance(&m_pErrorBP) == S_OK)    
               {    
                  m_pErrorBP->AddRef();    
                  m_pErrorBP->Initialize(this);    
               }    
            }    
  
            // Create a new enumerator of error breakpoints.    
             CComObject<CEnumDebugErrorBreakpoints>* pErrorEnum;    
            if (CComObject<CEnumDebugErrorBreakpoints>::CreateInstance(&pErrorEnum) == S_OK)    
            {    
               // Get the IDebugErrorBreakpoint2 information for the     
               // CErrorBreakpoint object.    
               CComPtr<IDebugErrorBreakpoint2> spErrorBP;    
               hrT = m_pErrorBP->QueryInterface(&spErrorBP);    
               assert(hrT == S_OK);    
               if (hrT == S_OK)    
               {    
                  // Initialize the new enumerator of error breakpoints   
                  // with the IDebugErrorBreakpoint2 information.      
                  IDebugErrorBreakpoint2* rgpErrorBP[] = { spErrorBP.p };    
                  hrT = pErrorEnum->Init(rgpErrorBP, &(rgpErrorBP[1]), NULL, AtlFlagCopy);    
                  if (hrT == S_OK)    
                  {    
                     // Verify that the passed IEnumDebugErrorBreakpoints2     
                     // interface can be successful queried by the  
                     // created CEnumDebugErrorBreakpoints object.    
                     hrT = pErrorEnum->QueryInterface(ppErrorEnum);    
                     assert(hrT == S_OK);    
                  }    
               }    
  
               // Otherwise, delete the CEnumDebugErrorBreakpoints object.    
               if (FAILED(hrT))    
               {    
                  delete pErrorEnum;    
               }    
            }    
  
            hr = S_FALSE;    
         }    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>См. также:  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [Выполняется](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
