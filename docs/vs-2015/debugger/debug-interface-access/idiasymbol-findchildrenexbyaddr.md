---
title: 'IDiaSymbol:: Финдчилдренексбяддр | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f791074d029be78eb7d45e06dce8a8cce145f71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149993"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает дочерние символы символа, которые являются допустимыми по указанному адресу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findChildrenExByAddr (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `symtag`  
 окне Задает Теги символов для извлекаемых дочерних элементов, как определено в [перечислении симтаженум](../../debugger/debug-interface-access/symtagenum.md). Задайте значение, чтобы `SymTagNull` получить все дочерние элементы.  
  
 `name`  
 окне Указывает имя извлекаемых дочерних элементов. Задайте значение, чтобы `NULL` получить все дочерние элементы.  
  
 `compareFlags`  
 окне Задает параметры сравнения, применяемые к соответствию имен. Значения из перечисления [перечисления намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать отдельно или в сочетании.  
  
 `address`  
 окне Адрес символа.  
  
 `ppResult`  
 заполняет Возвращает объект [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md) , содержащий список извлеченных дочерних символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` , если найден хотя бы один дочерний элемент символа, или значение `S_FALSE` , если не найдено потомков. в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 В число возвращаемых локальных символов входят сведения о диапазоне в реальном времени.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление Симтаженум](../../debugger/debug-interface-access/symtagenum.md)   
 [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession:: Финдчилдрен](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
