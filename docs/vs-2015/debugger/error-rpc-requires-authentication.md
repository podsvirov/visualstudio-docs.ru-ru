---
title: 'Ошибка: RPC требуется проверка подлинности | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535740"
---
# <a name="error-rpc-requires-authentication"></a>Ошибка: RPC требуется проверка подлинности
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Отладчику Visual Studio не удается подключиться к удаленному компьютеру. На локальном компьютере включена политика RPC, запрещающая удаленную отладку.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Запустите `\`*windir*`\system32\regedt32.exe`.  
  
2. Найдите и удалите `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3. Перезагрузите компьютер, чтобы изменения в реестре вступили в силу.  
  
4. Если проблема не исчезнет, обратитесь к администратору домена, посвященному параметру **Computer Configuration->административные шаблоны->System->удаленный вызов процедур — >ограничения для параметра групповой политики RPC-клиентов без проверки подлинности** .
