---
title: -SafeMode (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28480399238c1c915056d3929f8fd188cfff7eca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665512"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Запускает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] в безопасном режиме, загружая только среду и службы по умолчанию.

## <a name="syntax"></a>Синтаксис

```
devenv /SafeMode
```

## <a name="remarks"></a>Remarks
 Этот параметр запрещает загрузку пакетов VSPackage сторонних производителей при запуске [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], обеспечивая надежность работы.

## <a name="description"></a>Описание
 В приведенном ниже примере [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] запускается в безопасном режиме.

## <a name="code"></a>Код

```
Devenv.exe /SafeMode
```

## <a name="see-also"></a>См. также:
 [Параметры командной строки для команды devenv](../../ide/reference/devenv-command-line-switches.md)
