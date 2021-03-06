---
title: 'IDiaSymbol:: get_typeIds | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_typeIds method
ms.assetid: 5166e647-fde5-4efe-92bf-77f8ae3fbc9b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 410f8afdac24139791c19c3936049c855a51d4f9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "91146907"
---
# <a name="idiasymbolget_typeids"></a>IDiaSymbol::get_typeIds
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает массив значений идентификаторов типов, относящихся к компилятору, для этого символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_typeIds (   
   DWORD  cTypeIds,  
   DWORD* pcTypeIds,  
   DWORD  typeIds[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cTypeIds`  
 окне Размер буфера для хранения данных.  
  
 `pcTypeIds`  
 заполняет Возвращает число `typeIds` записанных или, если `typeIds` имеет значение `NULL` , а затем общее число доступных идентификаторов типов.  
  
 `typeIds[]`  
 заполняет Массив, который должен быть заполнен идентификаторами типов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
> Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
