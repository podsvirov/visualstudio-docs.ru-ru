---
title: 'IDebugProperty2:: Жетекстендединфо | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74810aab2f47a36c716891fd45b7424eb737b142
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164979"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает расширенные сведения для свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidExtendedInfo`  
 окне Идентификатор GUID, определяющий тип извлекаемой расширенной информации. Дополнительные сведения см. в разделе "Примечания".  
  
 `pExtendedInfo`  
 заполняет Возвращает `VARIANT` (C++) или объект (C#), который можно использовать для получения сведений о расширенных свойствах. Например, этот параметр может возвращать `IUnknown` интерфейс, для которого можно запросить интерфейс [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) . Дополнительные сведения см. в разделе "Примечания".  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает, `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` Если расширенные сведения для извлечения отсутствуют.  
  
## <a name="remarks"></a>Remarks  
 Этот метод существует для получения сведений, которые не извлекаются при вызове метода [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
 Следующие идентификаторы GUID обычно распознаются этим методом (значения GUID указаны для C#, так как имя недоступно в какой-либо сборке). Дополнительные идентификаторы GUID можно создать для внутреннего использования.  
  
|Имя|Идентификатор GUID|Описание|  
|----------|----------|-----------------|  
|гуиддокумент|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Возвращает `IUnknown` интерфейс в документ. Как правило, интерфейс [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) можно получить из этого `IUnknown` интерфейса.|  
|гуидкодеконтекст|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Возвращает `IUnknown` интерфейс в контекст документа. Как правило, интерфейс [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) можно получить из этого `IUnknown` интерфейса.|  
|гуидкустомвиеверсуппортед|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Возвращает строку, содержащую идентификатор CLSID пользовательского средства просмотра, обычно реализуемый средством оценки выражений.|  
|гуидекстендединфослот|{6df235ad-82c6-4292-9c97-7389770bc42f}|Возвращает 32-разрядное число, представляющее требуемый номер слота, если это свойство представляет локальный адрес управляемого кода.|  
|гуидекстендединфосигнатуре|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Возвращает строку, содержащую сигнатуру переменной, связанной с объектом свойства.|  
  
## <a name="see-also"></a>См. также:  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
