---
title: OBJECT_TYPE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc23045fa70554133eba3a7f1326681bf31ea379
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205143"
---
# <a name="object_type"></a>Object_Type
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает тип объекта из средства оценки выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```csharp  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## <a name="members"></a>Участники  
 OBJECT_TYPE_BOOLEAN  
 Указывает, что объект является логическим значением.  
  
 OBJECT_TYPE_CHAR  
 Указывает, что объект является символом.  
  
 OBJECT_TYPE_I1  
 Указывает, что объект является однобайтовым целым числом со знаком.  
  
 OBJECT_TYPE_U1  
 Указывает, что объект является однобайтовым беззнаковым целым числом.  
  
 OBJECT_TYPE_I2  
 Указывает, что объект является двухбайтовым целым числом со знаком.  
  
 OBJECT_TYPE_U2  
 Указывает, что объект представляет собой Двухбайтовое беззнаковое целое число.  
  
 OBJECT_TYPE_I4  
 Указывает, что объект является четырехзначным целым числом со знаком.  
  
 OBJECT_TYPE_U4  
 Указывает, что объект представляет собой целое число без знака длиной 4 байта.  
  
 OBJECT_TYPE_I8  
 Указывает, что объект является 8-байтовым целым числом со знаком.  
  
 OBJECT_TYPE_U8  
 Указывает, что объект является 8-байтовым целым числом без знака.  
  
 OBJECT_TYPE_R4  
 Указывает, что объект является четырьмя-байтовым числом с плавающей запятой.  
  
 OBJECT_TYPE_R8  
 Указывает, что объект является 8-байтовым числом с плавающей запятой.  
  
 OBJECT_TYPE_OBJECT  
 Указывает, что объект является объектом.  
  
 OBJECT_TYPE_NULL  
 Указывает, что объект имеет значение NULL.  
  
 OBJECT_TYPE_CLASS  
 Указывает, что объект является классом.  
  
## <a name="remarks"></a>Remarks  
 Передается в качестве аргумента методам [креатепримитивеобжект](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) и [креатеаррайобжект](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: ee. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [креатепримитивеобжект](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
