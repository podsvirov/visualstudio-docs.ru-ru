---
title: Пошаговое руководство. Повторное подписание манифестов приложения и развертывания | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5956ad23fe22c7c36b712fac61df268586142df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697563"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Практическое руководство. Повторное подписание манифестов приложения и развертывания
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

После внесения изменений в свойства развертывания в манифесте приложения для Windows Forms приложений, Windows Presentation Foundation приложений (XBAP) или решений Office необходимо повторно подписать манифесты приложения и развертывания с помощью сертификата. Этот процесс позволяет проверить, не установлены ли на компьютер конечного пользователя измененные злоумышленниками файлы.  
  
 Другой сценарий, в котором вы можете повторно подписать манифесты, — когда ваши клиенты хотят подписать манифесты приложения и развертывания с помощью собственного сертификата.  
  
## <a name="re-signing-the-application-and-deployment-manifests"></a>Повторное подписание манифестов приложения и развертывания  
 В этой процедуре предполагается, что вы уже внесли изменения в файл манифеста приложения (manifest). Дополнительные сведения см. [в разделе инструкции. изменение свойств развертывания](https://msdn.microsoft.com/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Повторное подписание манифестов приложения и развертывания с помощью Mage.exe  
  
1. Откройте окно **командной строки Visual Studio** .  
  
2. Измените каталоги на папку, содержащую файлы манифеста, которые необходимо подписать.  
  
3. Введите следующую команду, чтобы подписать файл манифеста приложения. Замените Манифестфиленаме именем файла манифеста и расширением. Замените Certificate на относительный или полный путь к файлу сертификата и замените Password паролем для сертификата.  
  
    ```  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Например, можно выполнить следующую команду, чтобы подписать манифест приложения для надстройки, приложения Windows Form или приложения Windows Presentation Foundation браузера. Временные сертификаты, созданные Visual Studio, не рекомендуются для развертывания в рабочих средах.  
  
    ```  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4. Введите следующую команду, чтобы обновить файл манифеста развертывания и подписать его, заменив имена заполнителей, как на предыдущем шаге.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Например, можно выполнить следующую команду, чтобы обновить и подписать манифест развертывания для надстройки Excel, приложения Windows Forms или приложения Windows Presentation Foundation браузера.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. При необходимости скопируйте главный манифест развертывания (Publish \\ *имя_приложения*. Application) в каталог развертывания версии (публиш\аппликатион Files \\ *AppName*_*Version*).  
  
## <a name="updating-and-re-signing-the-application-and-deployment-manifests"></a>Обновление и повторное подписание манифестов приложения и развертывания  
 В этой процедуре предполагается, что вы уже внесли изменения в файл манифеста приложения (manifest), но есть и другие файлы, которые были обновлены. При обновлении файлов также необходимо обновить хэш, представляющий файл.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Обновление и повторное подписание манифестов приложения и развертывания с помощью Mage.exe  
  
1. Откройте окно **командной строки Visual Studio** .  
  
2. Измените каталоги на папку, содержащую файлы манифеста, которые необходимо подписать.  
  
3. Удалите расширение. deploy из файлов в выходной папке публикации.  
  
4. Введите следующую команду, чтобы обновить манифест приложения новыми хэшами для обновленных файлов и подписать файл манифеста приложения. Замените Манифестфиленаме именем файла манифеста и расширением. Замените Certificate на относительный или полный путь к файлу сертификата и замените Password паролем для сертификата.  
  
    ```  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Например, можно выполнить следующую команду, чтобы подписать манифест приложения для надстройки, приложения Windows Form или приложения Windows Presentation Foundation браузера. Временные сертификаты, созданные Visual Studio, не рекомендуются для развертывания в рабочих средах.  
  
    ```  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5. Введите следующую команду, чтобы обновить файл манифеста развертывания и подписать его, заменив имена заполнителей, как на предыдущем шаге.  
  
    ```  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Например, можно выполнить следующую команду, чтобы обновить и подписать манифест развертывания для надстройки Excel, приложения Windows Forms или приложения Windows Presentation Foundation браузера.  
  
    ```  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6. Добавьте расширение. deploy обратно в файлы, кроме файлов манифеста приложения и развертывания.  
  
7. При необходимости скопируйте главный манифест развертывания (Publish \\ *имя_приложения*. Application) в каталог развертывания версии (публиш\аппликатион Files \\ *AppName*_*Version*).  
  
## <a name="see-also"></a>См. также:  
 [Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Управление доступом для кода для приложений ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce и Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Общие сведения о развертывании доверенных приложений](../deployment/trusted-application-deployment-overview.md)   
 [Как включить параметры безопасности ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Как задать зону безопасности для приложения ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Как задать пользовательские разрешения для приложения ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Как выполнить отладку приложения ClickOnce с ограниченными разрешениями](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Как добавить доверенный издатель на клиентский компьютер для приложений ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Как настроить поведение запроса о доверии ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
