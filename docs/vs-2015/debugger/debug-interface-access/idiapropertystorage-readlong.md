---
title: 'Идиапропертистораже:: Реадлонг | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08661272bea779ff0789619d58bf6f2837a21917
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538321"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает `LONG` значения в наборе свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 окне Идентификатор считываемого свойства ( `PROPID` определяется в втипес. h как `ULONG` ).  
  
 `pValue`  
 заполняет Возвращает значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает значение, `E_INVALIDARG` Если свойство не относится к типу `LONG` .  
  
## <a name="remarks"></a>Remarks  
 `LONG`Определено Windows как 32-разрядное целое число со знаком.  
  
## <a name="see-also"></a>См. также:  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
