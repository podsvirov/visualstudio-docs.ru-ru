---
title: Как включить файл данных в приложение ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9120a5b3cb60f6c607ed97ab2df24bb157c72371
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153769"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>How to: Include a Data File in a ClickOnce Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Каждому [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] устанавливаемому приложению назначается каталог данных на локальном диске конечного компьютера, где приложение может управлять собственными данными. Файлы данных могут включать файлы любого типа: текстовые файлы, XML-файлы или даже файлы базы данных Microsoft Access (MDB). В следующих процедурах показано, как добавить в приложение файл данных любого типа [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Включение файла данных с помощью Mage.exe  
  
1. Добавьте файл данных в каталог приложения с остальными файлами приложения.  
  
    Как правило, каталог приложения будет каталогом, помеченным текущей версией развертывания, например, v 1.0.0.0.  
  
2. Обновите манифест приложения, чтобы получить список файлов данных.  
  
    **Mage-u v 1.0.0.0 \ Application. manifest-FromDirectory v 1.0.0.0**  
  
    При выполнении этой задачи повторно создается список файлов в манифесте приложения, а также автоматически создаются хэш-подписи.  
  
3. Откройте манифест приложения в предпочтительном текстовом или XML-редакторе и найдите `file` элемент для недавно добавленного файла.  
  
    Если вы добавили XML-файл с именем `Data.xml` , он будет выглядеть примерно так, как показано в следующем примере кода.  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. Добавьте атрибут `type` к этому элементу и укажите для него значение `data` .  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. Повторно подпишите манифест приложения с помощью пары ключей или сертификата, а затем повторно подпишите манифест развертывания.  
  
    Необходимо повторно подписать манифест развертывания, так как его хэш манифеста приложения изменился.  
  
    **Mage-s манифест приложения-CF cert_file-PWD Password**  
  
    **Mage-u манифест развертывания — манифест приложения АППМ**  
  
    **манифест развертывания Mage-s-CF CertFile-PWD пароль**  
  
6. 
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Включение файла данных с помощью MageUI.exe  
  
1. Добавьте файл данных в каталог приложения с остальными файлами приложения.  
  
2. Как правило, каталог приложения будет каталогом, помеченным текущей версией развертывания, например, v 1.0.0.0.  
  
3. В меню **файл** выберите команду **Открыть** , чтобы открыть манифест приложения.  
  
4. Перейдите на вкладку **файлы** .  
  
5. В текстовом поле в верхней части вкладки введите каталог, содержащий файлы приложения, а затем нажмите кнопку **заполнить**.  
  
     Файл данных появится в сетке.  
  
6. Установите для файла данных значение **типа** **данных**.  
  
7. Сохраните манифест приложения, а затем повторно подпишите его.  
  
     MageUI.exe предложит повторно подписать файл.  
  
8. Повторно подписать манифест развертывания  
  
     Необходимо повторно подписать манифест развертывания, так как его хэш манифеста приложения изменился.  
  
## <a name="see-also"></a>См. также:  
 [Доступ к локальным и удаленным данным в приложениях ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)
