---
title: FRAMEINFO_FLAGS | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e5a930e81ff1105ba93ce3c3cff10ee8bff2f7e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538438"
---
# <a name="frameinfo_flags"></a>FRAMEINFO_FLAGS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Задает сведения, которые необходимо получить об объекте кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
typedef DWORD FRAMEINFO_FLAGS;  
```  
  
```csharp  
public enum enum_FRAMEINFO_FLAGS {  
   FIF_FUNCNAME              = 0x00000001,  
   FIF_RETURNTYPE            = 0x00000002,  
   FIF_ARGS                  = 0x00000004,  
   FIF_LANGUAGE              = 0x00000008,  
   FIF_MODULE                = 0x00000010,  
   FIF_STACKRANGE            = 0x00000020,  
   FIF_FRAME                 = 0x00000040,  
   FIF_DEBUGINFO             = 0x00000080,  
   FIF_STALECODE             = 0x00000100,  
   FIF_ANNOTATEDFRAME        = 0x00000200,  
   FIF_DEBUG_MODULEP         = 0x00000400,  
   FIF_FUNCNAME_FORMAT       = 0x00001000,  
   FIF_FUNCNAME_RETURNTYPE   = 0x00002000,  
   FIF_FUNCNAME_ARGS         = 0x00004000,  
   FIF_FUNCNAME_LANGUAGE     = 0x00008000,  
   FIF_FUNCNAME_MODULE       = 0x00010000,  
   FIF_FUNCNAME_LINES        = 0x00020000,  
   FIF_FUNCNAME_OFFSET       = 0x00040000,  
   FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,  
   FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,  
   FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,  
   FIF_FUNCNAME_ARGS_ALL     = 0x00700000,  
   FIF_ARGS_TYPES            = 0x01000000,  
   FIF_ARGS_NAMES            = 0x02000000,  
   FIF_ARGS_VALUES           = 0x04000000,  
   FIF_ARGS_ALL              = 0x07000000,  
   FIF_ARGS_NOFORMAT         = 0x08000000,  
   FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,  
   FIF_FILTER_NON_USER_CODE  = 0x20000000,  
   FIF_ARGS_NO_TOSTRING      = 0x40000000,  
   FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000  
};  
```  
  
## <a name="members"></a>Участники  
 FIF_FUNCNAME  
 Инициализируйте или используйте `m_bstrFuncName` поле.  
  
 FIF_RETURNTYPE  
 Инициализируйте или используйте `m_bstrReturnType` поле.  
  
 FIF_ARGS  
 Инициализируйте или используйте `m_bstrArgs` поле.  
  
 FIF_LANGUAGE  
 Инициализируйте или используйте `m_bstrLanguage` поле.  
  
 FIF_MODULE  
 Инициализируйте или используйте `m_bstrModule` поле.  
  
 FIF_STACKRANGE  
 Инициализируйте/используйте `m_addrMin` `m_addrMax` поля и (диапазон стека).  
  
 FIF_FRAME  
 Инициализируйте или используйте `m_pFrame` поле.  
  
 FIF_DEBUGINFO  
 Инициализируйте или используйте `m_fHasDebugInfo` поле.  
  
 FIF_STALECODE  
 Инициализируйте или используйте `m_fStaleCode` поле.  
  
 FIF_ANNOTATEDFRAME  
 Инициализируйте или используйте `m_fAnnotatedFrame` поле.  
  
 FIF_DEBUG_MODULEP  
 Инициализируйте или используйте `m_pModule` поле.  
  
 FIF_FUNCNAME_FORMAT  
 Форматирует имя функции. Результат возвращается в `m_bstrFunName` поле, а другие поля не заполняются.  
  
 FIF_FUNCNAME_RETURNTYPE  
 Добавляет тип возвращаемого значения в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_ARGS  
 Добавляет аргументы в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_LANGUAGE  
 Добавляет язык в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_MODULE  
 Добавляет имя модуля в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_LINES  
 Добавляет число строк в `m_bstrFuncName` поле.  
  
 FIF_FUNCNAME_OFFSET  
 Добавляет к `m_bstrFuncName` полю смещение в байтах от начала строки, если `FIF_FUNCNAME_LINES` указано значение. Если `FIF_FUNCNAME_LINES` параметр не указан или номера строк недоступны, добавляет смещение в байтах от начала функции.  
  
 FIF_FUNCNAME_ARGS_TYPES  
 Добавляет в поле Тип каждого аргумента функции `m_bstrFuncName` .  
  
 FIF_FUNCNAME_ARGS_NAMES  
 Добавляет в поле имя каждого аргумента функции `m_bstrFuncName` .  
  
 FIF_FUNCNAME_ARGS_VALUES  
 Добавляет в поле значение каждого аргумента функции `m_bstrFuncName` .  
  
 FIF_FUNCNAME_ARGS_ALL  
 Добавляет в поле Тип, имя и значение всех аргументов `m_bstrFuncName` .  
  
 FIF_ARGS_TYPES  
 Типы аргументов извлекаются и форматируются.  
  
 FIF_ARGS_NAMES  
 Имена аргументов извлекаются и форматируются.  
  
 FIF_ARGS_VALUES  
 Значения аргументов извлекаются и форматируются.  
  
 FIF_ARGS_ALL  
 Получение и форматирование типа, имени и значения всех аргументов.  
  
 FIF_ARGS_NOFORMAT  
 Указывает, что аргументы не форматируются (например, не добавляйте открывающую и закрывающую круглые скобки вокруг списка аргументов и не добавляйте разделитель между аргументами).  
  
 FIF_ARGS_NO_FUNC_EVAL  
 Указывает, что при извлечении значений аргументов не следует использовать вычисление функции (свойства).  
  
 FIF_FILTER_NON_USER_CODE  
 Модуль отладки предназначен для фильтрации кадров кода, не входящих в пользователь, так, чтобы они не включались.  
  
 FIF_ARGS_NO_TOSTRING  
 Не разрешать `ToString()` вычисление или форматирование функции при возврате аргументов функции.  
  
 FIF_DESIGN_TIME_EXPR_EVAL  
 Сведения о кадре должны быть предоставлены из размещенного домена приложения, а не ведущего процесса.  
  
## <a name="remarks"></a>Remarks  
 Эти флаги передаются [методам](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) и Pass для указания полей, которые должны быть инициализированы в структуре или структурах [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) .  
  
 Эти флаги также используются для указания того, какие поля структуры [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md) используются и допустимы при возврате структуры. Эти значения можно объединить с помощью побитовой операции `OR` .  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [фрамеинфо](../../../extensibility/debugger/reference/frameinfo.md)   
 [енумфрамеинфо](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)
