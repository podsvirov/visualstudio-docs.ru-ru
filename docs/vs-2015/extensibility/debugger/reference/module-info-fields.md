---
title: MODULE_INFO_FIELDS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b80235f4ae769acbe3c61ad4b597898ee774d6a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547329"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает флаги для отладочной информации модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
typedef DWORD MODULE_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_MODULE_INFO_FIELDS {   
   MIF_NONE              = 0x0000,  
   MIF_NAME              = 0x0001,  
   MIF_URL               = 0x0002,  
   MIF_VERSION           = 0x0004,  
   MIF_DEBUGMESSAGE      = 0x0008,  
   MIF_LOADADDRESS       = 0x0010,  
   MIF_PREFFEREDADDRESS  = 0x0020,  
   MIF_SIZE              = 0x0040,  
   MIF_LOADORDER         = 0x0080,  
   MIF_TIMESTAMP         = 0x0100,  
   MIF_URLSYMBOLLOCATION = 0x0200,  
   MIF_FLAGS             = 0x0400,  
   MIF_ALLFIELDS         = 0x07ff  
};  
```  
  
## <a name="members"></a>Участники  
 MIF_NONE  
 Инициализировать или использовать ни одно из полей в структуре.  
  
 MIF_NAME  
 Инициализируйте или используйте `m_bstrName` поле в структуре [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .  
  
 MIF_URL  
 Инициализируйте или используйте `m_bstrUrl` поле в `MODULE_INFO` структуре.  
  
 MIF_VERSION  
 Инициализируйте или используйте `m_bstrVersion` поле в `MODULE_INFO` структуре.  
  
 MIF_DEBUGMESSAGE  
 Инициализируйте или используйте `m_bstrDebugMessage` поле в `MODULE_INFO` структуре.  
  
 MIF_LOADADDRESS  
 Инициализируйте или используйте `m_addrLoadAddress` поле в `MODULE_INFO` структуре.  
  
 MIF_PREFFEREDADDRESS  
 Инициализируйте или используйте `m_addrPreferredLoadAddress` поле в `MODULE_INFO` структуре.  
  
 MIF_SIZE  
 Инициализируйте или используйте `m_dwSize` поле в `MODULE_INFO` структуре.  
  
 MIF_LOADORDER  
 Инициализируйте или используйте `m_dwLoadOrder` поле в `MODULE_INFO` структуре.  
  
 MIF_TIMESTAMP  
 Инициализируйте или используйте `m_TimeStamp` поле в `MODULE_INFO` структуре.  
  
 MIF_URLSYMBOLLOCATION  
 Инициализируйте или используйте `m_bstrUrlSymbolLocation` поле в `MODULE_INFO` структуре.  
  
 MIF_FLAGS  
 Инициализируйте или используйте `m_dwModuleFlags` поле в `MODULE_INFO` структуре.  
  
 MIF_ALLFIELDS  
 Инициализация или использование всех полей в `MODULE_INFO` структуре.  
  
## <a name="remarks"></a>Remarks  
 Эти значения передаются в качестве аргумента в метод " [info](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) ", чтобы указать, какие поля структуры [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) должны быть инициализированы.  
  
 Эти значения также используются в `MODULE_INFO` структуре для указания, какие поля используются и являются допустимыми.  
  
 Эти флаги можно сочетать с помощью побитовой операции `OR` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
