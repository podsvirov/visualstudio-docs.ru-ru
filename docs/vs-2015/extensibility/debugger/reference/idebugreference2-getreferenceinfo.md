---
title: 'IDebugReference2:: Жетреференцеинфо | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77cccb562db79d9f6a53113bda0c4434e19c6813
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155830"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает структуру [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , описывающую ссылку. Зарезервировано для будущего использования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetReferenceInfo (   
   DEBUGREF_INFO_FLAGS   dwFields,  
   DWORD                 nRadix,  
   DWORD                 dwTimeout,  
   IDebugReference2**    rgpArgs,  
   DWORD                 dwArgCount,  
   DEBUG_REFERENCE_INFO* pReferenceInfo  
);  
```  
  
```csharp  
int GetReferenceInfo (   
   enum_DEBUGREF_INFO_FLAGS  dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_REFERENCE_INFO[]    pReferenceInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 окне Сочетание флагов из перечисления [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , определяющее поля, которые должны быть заполнены в структуре [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) .  
  
 `nRadix`  
 окне Основание системы счисления, используемое при форматировании любой числовой информации.  
  
 `dwTimeout`  
 окне Максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.  
  
 `rgpArgs`  
 окне Массив объектов [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) . Зарезервировано для будущего использования; Задайте для значение null.  
  
 `dwArgCount`  
 окне Число ссылочных аргументов в `rgpArgs` массиве. Зарезервировано для будущего использования; Задайте значение 0.  
  
 `pReferenceInfo`  
 заполняет Структура [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) , которая заполняется описанием свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также:  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
