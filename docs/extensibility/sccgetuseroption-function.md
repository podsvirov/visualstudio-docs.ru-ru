---
title: Функция Сккжетусероптион | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetUserOption
helpviewer_keywords:
- SccGetUserOption function
ms.assetid: 17863747-1901-4c53-a2b3-ed996085e120
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc7b68df3331c1240ad833048940e656da034ccf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700685"
---
# <a name="sccgetuseroption-function"></a>Функция SccGetUserOption
Эта функция получает разнообразные параметры, относящиеся к пользователю.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccGetUserOption(
   LPVOID pContext,
   LONG nOption,
   LPLONG lpVal
);
```

#### <a name="parameters"></a>Параметры
 pContext

окне Указатель контекста для подключаемого модуля системы управления версиями.

 ноптион

окне Параметр для извлечения (см. раздел Примечания для возможных параметров).

 лпвал

заполняет Значение, связанное с параметром.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Параметр успешно получен.|
|SCC_E_OPNOTSUPPORTED|Параметр не поддерживается.|
|SCC_E_NONSPECIFICERROR|Произошла неизвестная ошибка.|

## <a name="remarks"></a>Remarks
 Эта команда поддерживает следующие параметры:

|Параметр пользователя|Описание|
|-----------------|-----------------|
|`SCC_USEROPT_CHECKOUT_LOCALVER`|Определяет, хочет ли пользователь извлечь локальную версию файлов. `lpVal` назначается `SCC_USEROPT_COLV_YES` (пользователь хочет извлечь локальные файлы) или `SCC_USEROPT_COLV_NO` .|

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [Код ошибки](../extensibility/error-codes.md)
