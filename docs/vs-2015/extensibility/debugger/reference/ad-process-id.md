---
title: AD_PROCESS_ID | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID
helpviewer_keywords:
- AD_PROCESS_ID union
ms.assetid: 4cb40d12-2e92-4f09-83f4-689928bd65b3
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea06d8e007e2df88cb46c2f0e6dd4a79ebe711b7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153632"
---
# <a name="ad_process_id"></a>AD_PROCESS_ID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Указывает идентификатор процесса, который может быть либо системным ИДЕНТИФИКАТОРом, либо идентификатором GUID.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _AD_PROCESS_ID {  
   AD_PROCESS_ID_TYPE ProcessIdType;  
   union {  
      DWORD dwProcessId;   
      GUID  guidProcessId;   
      DWORD dwUnused;   
   } ProcessId;  
} AD_PROCESS_ID;  
```  
  
```csharp  
public struct AD_PROCESS_ID {  
   AD_PROCESS_ID_TYPE ProcessIdType;  
   DWORD              dwProcessId;   
   GUID               guidProcessId;   
   DWORD              dwUnused;   
};  
```  
  
## <a name="members"></a>Участники  
 `ProcessIdType`  
 Значение из перечисления [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md) , указывающее способ интерпретации `ProcessId` объединения (или для управляемого кода, к которому необходимо получить доступ).  
  
 двпроцессид  
 Идентификатор процесса в виде значения из системы.  
  
 гуидпроцессид  
 Идентификатор процесса в виде идентификатора GUID.  
  
 двунусед  
 Заполнение.  
  
## <a name="remarks"></a>Remarks  
 Эта структура передается следующим методам:  
  
- [GetProviderProgramNode](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)  
  
- [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)  
  
- [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)  
  
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)  
  
  И возвращается из следующих методов:  
  
- [GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)  
  
- [GetHostId](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)   
 [AD_PROCESS_ID_TYPE](../../../extensibility/debugger/reference/ad-process-id-type.md)   
 [жетфисикалпроцессид](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)   
 [жесостид](../../../extensibility/debugger/reference/idebugprogramhost2-gethostid.md)   
 [жетпровидерпрограмноде](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprogramnode.md)   
 [ватчфорпровидеревентс](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)
