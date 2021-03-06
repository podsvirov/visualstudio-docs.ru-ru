---
title: 'IDebugProgramHost2:: @ HostName | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cb7ceae40282115dc455691789c3882a1620e829
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165123"
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает заголовок, понятное имя или имя файла ведущего процесса этой программы.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwType`  
 окне Значение из перечисления [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .  
  
 `pbstrHostName`  
 заполняет Возвращает запрошенное имя ведущего процесса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 В обычной реализации этого метода `dwType` параметр игнорируется, и возвращается понятное имя хост-компьютера. Другой возможной реализацией является передача `dwType` параметра в вызов метода- [HostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) для получения имени.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
