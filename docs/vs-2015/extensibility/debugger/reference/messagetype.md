---
title: MESSAGETYPE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c17564c992f4c8855d8a96165975a5d0e132755c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547212"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает тип и причину сообщения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Участники  
 MT_OUTPUTSTRING  
 Указывает, что сообщение должно быть отправлено в окно вывода. Это взаимоисключающее из `MT_MESSAGEBOX` .  
  
 MT_MESSAGEBOX  
 Указывает, что сообщение должно отображаться в окне сообщения. Это взаимоисключающее из `MT_OUTPUTSTRING` .  
  
 MT_TYPE_MASK  
 Значение маски для изоляции назначения сообщения.  
  
 MT_REASON_EXCEPTION  
 Указывает, что в результате исключения отображается окно сообщения. Это взаимоисключающее из `MT_REASON_TRACEPOINT` .  
  
 MT_REASON_TRACEPOINT  
 Указывает, что в результате попадания в точку трассировки отображается окно сообщения. Это взаимоисключающее с `MT_REASON_EXCEPTION` .  
  
 MT_REASON_MASK  
 Значение маски, которое позволяет изолировать причину отображения сообщения.  
  
## <a name="remarks"></a>Remarks  
 Эти значения возвращаются методами [жетеррормессаже](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) [и.](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)  
  
 Одно из значений причины можно объединить с одним из значений назначения выходных данных с помощью побитовой операции `OR` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)
