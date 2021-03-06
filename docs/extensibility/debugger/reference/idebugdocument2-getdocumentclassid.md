---
title: 'IDebugDocument2:: Жетдокументклассид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2::GetDocumentClassID
helpviewer_keywords:
- IDebugDocument2::GetDocumentClassID
ms.assetid: 111c2b85-ebfa-487f-b896-2ec4a3eac4d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 71683c91082f477da530ec1be1fdc7627d6a7635
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732029"
---
# <a name="idebugdocument2getdocumentclassid"></a>IDebugDocument2::GetDocumentClassID
Возвращает идентификатор класса документа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetDocumentClassID( 
   CLSID* pclsid
);
```

```csharp
int GetDocumentClassID( 
   out Guid pclsid
);
```

## <a name="parameters"></a>Параметры
`pclsid` заполняет Возвращает идентификатор GUID, который является ИДЕНТИФИКАТОРом класса документа.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Remarks
 Идентификатор GUID класса можно использовать для создания экземпляров отдельных классов, каждый из которых представляет документ.

## <a name="see-also"></a>См. также раздел
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
