---
title: 'Иивисуализерсервице:: Жеткустомвиеверлист | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c2ee2682b04b03b2b0bb04e0ba9ef5d9a2df8a35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192068"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает список визуализаторов типов, о которых знает эта служба.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celtSkip`  
 окне Число пропускаемых визуализаторов.  
  
 `celRequested`  
 окне Количество визуализаторов для извлечения (также определяет размер `rgViewers` массива).  
  
 `rgViewers`  
 [вход, выход] Массив [DEBUG_CUSTOM_VIEWERных](../../../extensibility/debugger/reference/debug-custom-viewer.md) структур, которые необходимо заполнить.  
  
 `pceltFetched`  
 заполняет Число фактически извлеченных визуализаторов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 [Жеткустомвиеверлист](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) передает запрос этому методу в рамках его поддержки для визуализаторов типов. Если средство оценки выражений также предоставляет пользовательские средства просмотра для одного и того же типа, оно может добавлять соответствующие структуры [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) для этих пользовательских средств просмотра в список. Убедитесь, что [жеткустомвиеверкаунт](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) отражает эти дополнительные средства просмотра.  
  
 Сведения о различиях между визуализаторами и читателями см. в разделе [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) .  
  
## <a name="see-also"></a>См. также:  
 [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [жеткустомвиеверлист](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [жеткустомвиеверкаунт](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
