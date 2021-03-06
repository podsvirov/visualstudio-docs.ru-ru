---
title: Функция Сккремове | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 62974f585fe164c7ccf7ea21a19d22939d806d73
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199975"
---
# <a name="sccremove-function"></a>Функция SccRemove
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция удаляет файлы из системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccRemove(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 пвконтекст  
 окне Структура контекста подключаемого модуля системы управления версиями.  
  
 hWnd  
 окне Обработчик окна интегрированной среды разработки, который может использоваться подключаемым модулем системы управления версиями в качестве родительского для любых предоставляемых им диалоговых окон.  
  
 Nфайлы оставленные  
 окне Число файлов, указанных в `lpFileNames` массиве.  
  
 лпфиленамес  
 окне Массив полных имен локальных путей к удаляемым файлам.  
  
 лпкоммент  
 окне Комментарий, применяемый к каждому удаляемому файлу.  
  
 фоптионс  
 окне Флаги команды (не используется).  
  
 пвоптионс  
 окне Параметры, зависящие от подключаемого модуля системы управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля системы управления версиями для этой функции должна возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Удаление успешно выполнено.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не находится в системе управления версиями.|  
|SCC_E_OPNOTSUPPORTED|Система управления версиями не поддерживает эту операцию.|  
|SCC_E_ISCHECKEDOUT|Невозможно удалить файл, так как пользователь в данный момент извлечен.|  
|SCC_E_ACCESSFAILURE|Возникла проблема при доступе к системе управления версиями, возможно, из-за проблем с сетью или состязаниями.|  
|SCC_E_NOTAUTHORIZED|Пользователю не разрешено выполнять эту операцию.|  
|SCC_E_NONSPECIFICERROR|Неконкретный сбой; файл не был удален.|  
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|  
  
## <a name="remarks"></a>Remarks  
 Эта функция удаляет файлы из системы управления версиями, но не удаляет их с локального жесткого диска пользователя.  
  
## <a name="see-also"></a>См. также:  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
