---
title: 'IDebugProgram2:: выполнить процесс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 366b35a90eb44496dc1b50cd85dfa0fef5656ddb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148655"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получите процесс, в котором выполняется эта программа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetProcess(  
   IDebugProcess2** ppProcess  
);  
```  
  
```csharp  
int GetProcess(  
   out IDebugProcess2 ppProcess  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppProcess`  
 заполняет Возвращает интерфейс [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) , представляющий процесс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если модуль отладки (DE) не реализует интерфейс [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) , реализация этого метода de всегда должна возвращаться, `E_NOTIMPL` поскольку de не может определить, какой процесс выполняется в и, следовательно, не может удовлетворить реализацию этого метода.  
  
 Реализация `IDebugEngineLaunch2` интерфейса означает, что de должен уметь создавать процесс, поэтому реализация интерфейса [IDEBUGPROGRAM2](../../../extensibility/debugger/reference/idebugprogram2.md) в de может определить процесс, в котором он выполняется.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
