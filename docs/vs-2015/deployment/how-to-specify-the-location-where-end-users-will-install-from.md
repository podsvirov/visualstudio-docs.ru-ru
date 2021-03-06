---
title: Как указать расположение, из которого будут устанавливаться конечные пользователи. Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82181d906adc3454dfe77ef4fb21d8bdf99df16f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557988"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Практическое руководство. Указание расположения, из которого будет производиться установка пользователями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При публикации [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения расположение, в которое пользователи переходят по загрузке и установке, не обязательно является расположением, где первоначально публикуются приложение. Например, в некоторых организациях разработчик может опубликовать приложение на промежуточном сервере, а затем администратор переместит приложение на веб-сервер.  
  
 В этом случае можно использовать `Installation URL` свойство, чтобы указать веб-сервер, на который пользователи будут загружать приложение. Это необходимо, чтобы манифест приложения знал, где искать обновления.  
  
 Это `Installation URL` свойство можно задать на странице **Публикация** **конструктора проектов**.  
  
 **Примечание** . `Installation URL` Свойство также может быть задано с помощью **публикаций**. Дополнительные сведения см. в разделе [инструкции. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Указание URL-адреса установки  
  
1. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните **Свойства**.  
  
2. Перейдите на вкладку **Публикация**.  
  
3. В поле URL-адрес установки введите путь установки с помощью полного URL-адреса в формате `https://www.contoso.com/ApplicationName` или UNC, используя формат `\\Server\ApplicationName` .  
  
## <a name="see-also"></a>См. также:  
 [Как указать, где Visual Studio копирует файлы](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Публикация приложений ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
