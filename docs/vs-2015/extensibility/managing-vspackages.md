---
title: Управление пакетами VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194372"
---
# <a name="managing-vspackages"></a>Управление пакетами VSPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В большинстве случаев вам не нужно беспокоиться об управлении пакетами VSPackage, так как шаблоны проектов и элементов регистрируются и загружаются автоматически. Однако в некоторых случаях для управления пакетом может потребоваться несколько дополнительных изучений.  
  
## <a name="using-the-experimental-instance"></a>Использование экспериментального экземпляра  
 Чтобы узнать больше об экспериментальном экземпляре, см. [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).  
  
## <a name="registering-and-unregistering-vspackages"></a>Регистрация и отмена регистрации пакетов VSPackage  
 Сведения о регистрации и отмене регистрации пакетов VSPackage и других типов расширений см. в статье [Регистрация пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md)и их отмена.  
  
## <a name="loading-a-vspackage"></a>Загрузка VSPackage  
 Пакеты VSPackage можно установить в значение автозагрузки, если включен определенный идентификатор GUID КМДУИКОНТЕКСТ. Дополнительные сведения см. в разделе [Загрузка пакетов VSPackage](../extensibility/loading-vspackages.md).  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>Использование AsyncPackage для загрузки пакетов VSPackage в фоновом режиме  
 Класс AsyncPackage позволяет загружать пакеты в фоновом потоке для улучшения скорости реагирования пользовательского интерфейса в Visual Studio. Дополнительные сведения см. в разделе [как использовать AsyncPackage для загрузки пакетов VSPackage в фоновом режиме](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).  
  
## <a name="rule-based-ui-context-for-extensions"></a>Контекст пользовательского интерфейса на основе правил для расширений  
 Контексты пользовательского интерфейса на основе правил позволяют авторам расширений определять точные условия, при которых активируется контекст пользовательского интерфейса и загружаются связанные пакеты VSPackage. Дополнительные сведения см. [в разделе руководство. использование контекста пользовательского интерфейса на основе правил для расширений Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).  
  
## <a name="troubleshooting-vspackages"></a>Устранение неполадок, связанных с пакетами VSPackage  
 Узнайте о методах устранения неполадок пакетов VSPackage, которые не загружаются или в которых возникают ошибки: [Устранение неполадок пакетов VSPackage](../extensibility/troubleshooting-vspackages.md)  
  
## <a name="see-also"></a>См. также:  
 [VSPackages](../extensibility/internals/vspackages.md)
