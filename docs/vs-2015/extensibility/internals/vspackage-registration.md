---
title: Регистрация VSPackage | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a11f05edb4e7d476fdbcab82d365f9327dd4869a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685285"
---
# <a name="vspackage-registration"></a>Регистрация VSPackage
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакеты VSPackage должны [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] быть извещены о том, что они установлены и должны быть загружены. Этот процесс выполняется путем записи сведений в реестр. Это типичное задание установщика.  
  
> [!NOTE]
> Это рекомендуемый подход во время разработки VSPackage для использования самостоятельной регистрации. Однако [!INCLUDE[vsipprvsip](../../includes/vsipprvsip-md.md)] партнеры не могут поставлять свои продукты, используя самостоятельную регистрацию в процессе установки.  
  
 Записи реестра в пакете установщик Windows обычно создаются в таблице реестра. Кроме того, можно зарегистрировать расширения файлов в таблице реестра. Однако установщик Windows предоставляет встроенную поддержку через программный идентификатор (ProgId), класс, расширение и таблицы команд. Дополнительные сведения см. в разделе [таблицы базы данных](https://msdn.microsoft.com/library/aa368259\(VS.85\).aspx).  
  
 Убедитесь, что записи реестра связаны с компонентом, который подходит для выбранной параллельной стратегии. Например, записи реестра для общего файла должны быть связаны с компонентом установщик Windows этого файла. Аналогичным образом, записи реестра для файла конкретной версии должны быть связаны с компонентом этого файла. В противном случае установка или удаление пакета VSPackage для одной версии [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] может нарушить работу пакета VSPackage в других версиях. Дополнительные сведения см. в разделе [Поддержка нескольких версий Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md) .  
  
> [!NOTE]
> Самым простым способом управления регистрацией является использование одних и тех же данных в одних и тех же файлах для регистрации разработчика и во время установки. Например, некоторые средства разработки установщика могут использовать файл в формате REG-Format во время сборки. Если разработчики сохраняют reg-файлы для собственных повседневных работ по разработке и отладке, то эти же файлы могут быть автоматически добавлены в установщик. Если вы не можете автоматически обмениваться данными регистрации, необходимо убедиться в том, что копия регистрационных данных в установщике актуальна.  
  
## <a name="registering-unmanaged-vspackages"></a>Регистрация неуправляемых пакетов VSPackage  
 Неуправляемые пакеты VSPackage (включая созданные в шаблоне пакета Visual Studio) используют файлы. RGS в стиле библиотеки ATL для хранения сведений о регистрации. Формат RGS-файла характерен для ATL и обычно не может использоваться средством разработки установки. Сведения о регистрации для установщика VSPackage необходимо поддерживать отдельно. Например, разработчики могут синхронизировать файлы в формате REG с изменениями файлов. RGS. Файлы reg можно объединять с помощью Regedit для разработки или использования установщиком.  
  
## <a name="registering-managed-vspackages"></a>Регистрация управляемых пакетов VSPackage  
 Средство RegPkg считывает атрибуты регистрации из управляемого пакета VSPackage и может либо записывать данные непосредственно в реестр, либо записывать файлы reg-Format, которые могут использоваться установщиком.  
  
> [!NOTE]
> Средство RegPkg не является распространяемым и не может использоваться для регистрации VSPackage в системе пользователя.  
  
## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Почему пакеты VSPackage не должны самостоятельно регистрироваться во время установки  
 Установщики VSPackage не должны полагаться на самостоятельную регистрацию. На первый взгляд, хранение значений реестра VSPackage только в пакете VSPackage кажется хорошей идеей. Учитывая, что разработчикам требуются значения реестра, доступные для их работы и тестирования, имеет смысл избегать сохранения отдельной копии данных реестра в установщике. Установщик может использовать сам пакет VSPackage для записи значений реестра.  
  
 Хотя в теории, самостоятельная регистрация имеет несколько недостатков, которые делают его непригодным для установки VSPackage:  
  
- Чтобы правильно поддерживать установку, удаление, откат установки и откат удаления, необходимо создать четыре настраиваемых действия для каждого управляемого пакета VSPackage, который самостоятельно регистрирует путем вызова RegPkg.  
  
- Подход к параллельной поддержке может потребовать создания четырех настраиваемых действий, которые вызывают RegSvr32 или RegPkg для каждой поддерживаемой версии [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Установка с самостоятельными модулями не может быть безопасно отменена, так как нет способа определить, используются ли самостоятельные ключи другой функцией или приложением.  
  
- Самостоятельно зарегистрированные библиотеки DLL иногда связываются с вспомогательными библиотеками DLL, которые отсутствуют или имеют неправильную версию. В отличие от этого, установщик Windows может регистрировать библиотеки DLL с помощью таблиц реестра без зависимости от текущего состояния системы.  
  
- Коду с собственной регистрацией может быть отказано в доступе к сетевым ресурсам, например библиотекам типов, если компонент указан как Run-from-Source и перечислен в таблице Селфрег. Это может привести к сбою установки компонента во время административной установки.  
  
## <a name="see-also"></a>См. также:  
 [установщик Windows](https://msdn.microsoft.com/library/cc185688\(VS.85\).aspx)   
 [Регистрация управляемого пакета](https://msdn.microsoft.com/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
