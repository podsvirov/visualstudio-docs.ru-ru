---
title: 'IDebugProperty2:: GetPropertyInfo | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetPropertyInfo
helpviewer_keywords:
- IDebugProperty2::GetPropertyInfo
ms.assetid: 39d6e942-df72-4c84-a5d9-a386d112714c
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6a6d4c2fd943ddef0b4459460be1f67550e53d84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146273"
---
# <a name="idebugproperty2getpropertyinfo"></a>IDebugProperty2::GetPropertyInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает структуру [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , описывающую свойство.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetPropertyInfo (   
   DEBUGPROP_INFO_FLAGS dwFields,  
   DWORD                nRadix,  
   DWORD                dwTimeout,  
   IDebugReference2**   rgpArgs,  
   DWORD                dwArgCount,  
   DEBUG_PROPERTY_INFO* pPropertyInfo  
);  
```  
  
```cpp#  
int GetPropertyInfo (   
   enum_DEBUGPROP_INFO_FLAGS dwFields,  
   uint                      nRadix,  
   uint                      dwTimeout,  
   IDebugReference2[]        rgpArgs,  
   uint                      dwArgCount,  
   DEBUG_PROPERTY_INFO[]     pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 окне Сочетание значений из перечисления [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , которое указывает, какие поля должны быть заполнены в `pPropertyInfo` структуре.  
  
 `nRadix`  
 окне Основание системы счисления, используемое для форматирования любых числовых данных.  
  
 `dwTimeout`  
 окне Указывает максимальное время ожидания (в миллисекундах) перед возвратом из этого метода. Используйте `INFINITE` для бесконечного ожидания.  
  
 `rgpArgs`  
 [вход, выход] Зарезервировано для будущего использования; Задайте для значение null.  
  
 `dwArgCount`  
 окне Зарезервировано для будущего использования; присвойте ему значение 0.  
  
 `pPropertyInfo`  
 заполняет Структура [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) , которая заполняется описанием свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
