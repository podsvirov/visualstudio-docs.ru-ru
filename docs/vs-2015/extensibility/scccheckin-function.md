---
title: Функция SccCheckin | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccCheckin
helpviewer_keywords:
- SccCheckin function
ms.assetid: e3f26ac2-6163-42e1-a764-22cfea5a3bc6
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 27d2f5fc2bec3f7e082593e3adcd65a0407f0bc2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560525"
---
# <a name="scccheckin-function"></a>Функция SccCheckin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccCheckin](https://docs.microsoft.com/visualstudio/extensibility/scccheckin-function).  
  
Эта функция проверяет в ранее извлеченных файлов в системе управления версиями, сохранение изменений и создание новой версии. Эта функция вызывается с числом и массив имен файлов для возврата.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccCheckin (  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPSTR*    lpFileNames,  
   LPCSTR    lpComment,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, SCC подключаемый модуль можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 nFiles  
 [in] Число файлов, выбранных для возврата.  
  
 lpFileNames  
 [in] Массив имен файлов для проверки полный локальный путь.  
  
 lpComment  
 [in] Комментарий для применения к каждой из выбранных файлов, возврат. Это `NULL` если подключаемый модуль системы управления версиями следует запрашивать комментарий.  
  
 Возможности  
 [in] Флаги команды, либо 0 или `SCC_KEEP_CHECKEDOUT`.  
  
 pvOptions  
 [in] Параметры, специфичные для подключаемых модулей SCC.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Файлы успешно возвращен.|  
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка. Файл не был возвращен.|  
|SCC_E_NOTCHECKEDOUT|Пользователь не извлечен файл, поэтому не может проверить его.|  
|SCC_E_CHECKINCONFLICT|Не удалось выполнить Checkin, так как:<br /><br /> -Другой пользователь внес вперед и `bAutoReconcile` была ошибочной.<br /><br /> - или -<br /><br /> -Автообъединение невозможно (например, когда файлы являются двоичными).|  
|SCC_E_VERIFYMERGE|Файл был автоматически объединены, но еще не возвращен ожидающие проверки пользователя.|  
|SCC_E_FIXMERGE|Файл был автоматически объединены, но еще не возвращен из-за конфликта слияния, который необходимо разрешить вручную.|  
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|  
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|  
|SCC_I_RELOADFILE|Файл или проект должен быть перезагружен.|  
|SCC_E_FILENOTEXIST|Локальный файл не найден.|  
  
## <a name="remarks"></a>Примечания  
 Комментарий применяется ко всем файлам, возврат. Аргумент примечания могут быть `null` string, тогда подключаемый модуль системы управления версиями можно запрашивать пользователя строку комментария для каждого файла.  
  
 `fOptions` Значение может быть указан аргумент `SCC_KEEP_CHECKEDOUT` флаг, указывающий на намерение пользователя вернуть файл и снова попробуйте в деле.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
