---
title: ADDRESS_KIND | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6152ff5f493134812916f28e0b908bf98ecdbb35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62561877"
---
# <a name="address_kind"></a>ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает типы адресов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>Термины  
 ADDRESS_KIND_NATIVE  
 Собственный адрес, представленный структурой [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) .  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 Неуправляемый адрес относительно `this` `Me` указателя (в Visual Basic), представленный структурой [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) .  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 Неуправляемый физический адрес, представленный структурой [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) .  
  
 ADDRESS_KIND_METHOD  
 Метод класса, представленный структурой [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) .  
  
 ADDRESS_KIND_FIELD  
 Поле класса, представленное структурой [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) .  
  
 ADDRESS_KIND_LOCAL  
 Адрес предназначен для локальной переменной и представлен структурой [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) .  
  
 ADDRESS_KIND_PARAM  
 Метод или параметр функции, представленный структурой [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) .  
  
 ADDRESS_KIND_ARRAYELEM  
 Элемент массива, представленный структурой [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) .  
  
 ADDRESS_KIND_RETVAL  
 Возвращаемое значение, представленное структурой [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) .  
  
## <a name="remarks"></a>Remarks  
 Метод [метода](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) WebMethod возвращает структуру [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) , содержащую объединение возможных структур, [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) структуру. `dwKind`Поле `DEBUG_ADDRESS_UNION` структуры содержит `ADDRESS_KIND` значение и описывает способ интерпретации поля объединения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Выадресовать](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
