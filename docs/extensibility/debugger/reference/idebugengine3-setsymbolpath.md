---
title: 'IDebugEngine3:: Сетсимболпас | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80730661"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Задает путь или пути, по которым выполняется поиск отладочных символов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>Параметры

`szSymbolSearchPath`\
окне Строка, содержащая путь поиска символов или пути. Дополнительные сведения см. в разделе "Примечания". Не может иметь значение NULL.

`szSymbolCachePath`\
окне Строка, содержащая локальный путь, по которому можно кэшировать символы. Не может иметь значение NULL.

`Flags`\
окне Не используется; всегда имеет значение 0.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Строка `szSymbolSearchPath` представляет собой список из одного или нескольких путей, разделенных точкой с запятой, для поиска символов. Эти пути могут быть локальным путем, UNC-путем или URL-адресом. Эти пути также могут быть смесью различных типов. Если путь имеет формат UNC (например, \\ \симсервер\симболс), то модуль отладки должен определить, является ли путь сервером символов и должен ли он быть способен загружать символы с этого сервера, а затем кэшировать их по пути, указанному параметром `szSymbolCachePath` .

 Путь к символам также может содержать одно или несколько расположений кэша. Кэши перечисляются в порядке приоритета, сначала используется кэш с наивысшим приоритетом, который отделяется символами *. Пример:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Метод [лоадсимболс](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) выполняет фактическую загрузку символов.

## <a name="see-also"></a>См. также раздел
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
