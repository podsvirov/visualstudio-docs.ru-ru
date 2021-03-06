---
title: EXCEPTION_STATE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- EXCEPTION_STATE
helpviewer_keywords:
- EXCEPTION_STATE enumeration
ms.assetid: 597f4f4c-9b70-485c-b5dc-3c2e3aecc664
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4e30d9cc9df592cc6feb97c14449dbc6a122ec63
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149359"
---
# <a name="exception_state"></a>EXCEPTION_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает состояние исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
typedef DWORD EXCEPTION_STATE;  
```  
  
```csharp  
public enum enum_EXCEPTION_STATE {   
   EXCEPTION_NONE                          = 0x0000,  
   EXCEPTION_STOP_FIRST_CHANCE             = 0x0001,  
   EXCEPTION_STOP_SECOND_CHANCE            = 0x0002,  
   EXCEPTION_STOP_USER_FIRST_CHANCE        = 0x0010,  
   EXCEPTION_STOP_USER_UNCAUGHT            = 0x0020,  
   EXCEPTION_STOP_ALL                      = 0x00FF,  
   EXCEPTION_CANNOT_BE_CONTINUED           = 0x0100,  
  
   // These are for exception types only  
   EXCEPTION_CODE_SUPPORTED                = 0x1000,  
   EXCEPTION_CODE_DISPLAY_IN_HEX           = 0x2000,  
   EXCEPTION_JUST_MY_CODE_SUPPORTED        = 0x4000,  
   EXCEPTION_MANAGED_DEBUG_ASSISTANT       = 0x8000,  
  
   // These are no longer used  
   EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT      = 0x0004,  
   EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT     = 0x0008,  
   EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT = 0x0040,  
   EXCEPTION_STOP_USER_UNCAUGHT_USE_PARENT     = 0x0080,  
};  
```  
  
## <a name="members"></a>Участники  
 EXCEPTION_NONE  
 Не останавливайтесь при возникновении исключения.  
  
 EXCEPTION_STOP_FIRST_CHANCE  
 Останавливаться при первом срабатывании исключения. При описании события исключения этот флаг указывает на то, что событие исключения является первым экземпляром события исключения.  
  
 EXCEPTION_STOP_SECOND_CHANCE  
 Останавливает при втором срабатывании исключения. При описании события исключения указывает, что событие исключения является событием второй-шансного исключения.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE  
 Останавливаться при первом срабатывании исключения в пользовательском режиме. При описании события исключения указывает, что событие исключения является первым экземпляром события исключения пользователя.  
  
 EXCEPTION_STOP_USER_UNCAUGHT  
 Останавливаться, когда не перехвачено исключение пользовательского режима. При описании события исключения указывает, что событие исключения является неперехваченным событием исключения пользовательского режима.  
  
 EXCEPTION_STOP_ALL  
 Останавливаться на любом исключении. Не используется при описании события исключения.  
  
 EXCEPTION_CANNOT_BE_CONTINUED  
 При описании события исключения указывает, что исключение не может быть продолжено.  
  
 EXCEPTION_CODE_SUPPORTED  
 Указывает, что исключение имеет код, поддерживающий его. Используется при отображении исключения  
  
 EXCEPTION_CODE_DISPLAY_IN_HEX  
 Указывает, что код исключения должен отображаться в шестнадцатеричном формате. Используется при отображении исключения.  
  
 EXCEPTION_JUST_MY_CODE_SUPPORTED  
 Указывает, что код исключения поддерживает Жустмикоде. Используется при отображении исключения.  
  
 EXCEPTION_MANAGED_DEBUG_ASSISTANT  
 Указывает, что отладчик управляемого кода должен выполнять обработку исключений. Если значение не задано, отладчик по умолчанию обрабатывает исключения. Он передается в метод [сеталлексцептионс](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) и не используется в структуре [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) .  
  
 EXCEPTION_STOP_FIRST_CHANCE_USE_PARENT  
 УСТАРЕЛО, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_SECOND_CHANCE_USE_PARENT  
 УСТАРЕЛО, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_USER_FIRST_CHANCE_USE_PARENT  
 УСТАРЕЛО, НЕ ИСПОЛЬЗУЙТЕ.  
  
 EXCEPTION_STOP_USER_SECOND_CHANCE_USE_PARENT  
 УСТАРЕЛО, НЕ ИСПОЛЬЗУЙТЕ.  
  
## <a name="remarks"></a>Remarks  
 Используется в качестве `dwState` члена структуры [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) для указания состояния исключения и того, что может быть сделано.  
  
 Эти значения также передаются методу [сеталлексцептионс](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md) для установки состояния всех исключений.  
  
 Эти флаги можно сочетать с помощью побитового или.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)
