---
title: Функция Скцендбатч | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEndBatch
helpviewer_keywords:
- SccEndBatch function
ms.assetid: 100e7833-fe0a-45c0-9fca-3e61fd1165b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51fe7e0bc0d417ffa182fbc68fd2779ed0b625d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700926"
---
# <a name="sccendbatch-function"></a>Функция Скцендбатч
Эта функция завершает пакет операций системы управления версиями. Эти пакеты не могут быть вложенными.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccEndBatch(void);
```

## <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Выполнение пакета операций успешно завершено.|
|SCC_E_UNKNOWNERROR|Неконкретный сбой.|

## <a name="remarks"></a>Remarks
 Пакеты управления версиями используются для выполнения одних и тех же операций с системой управления версиями в нескольких проектах или в нескольких контекстах. Пакеты можно использовать для исключения избыточных диалоговых окон из-за работы пользователя во время пакетной операции. [Сккбегинбатч](../extensibility/sccbeginbatch-function.md) и `SccEndBatch` функция используются в качестве пары для указания начала и конца операции. Они не могут быть вложенными.

## <a name="see-also"></a>См. также раздел
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
- [SccBeginBatch](../extensibility/sccbeginbatch-function.md)
