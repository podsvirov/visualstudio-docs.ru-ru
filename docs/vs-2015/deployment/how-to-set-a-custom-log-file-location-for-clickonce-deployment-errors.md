---
title: Как задать расположение настраиваемого файла журнала для ошибок развертывания ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a1b7c93e4b30bbfd373a5fad9d7001452d4f587
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842601"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Практическое руководство. Задание местоположения файла настраиваемого журнала для ошибок развертывания ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] обслуживает файлы журналов активации для всех развертываний. В этих журналах задокументированы все ошибки, относящиеся к установке и инициализации [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания. По умолчанию [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] создает один файл журнала для каждой активации развертывания. Эти файлы журналов хранятся в папке Temporary Internet Files. Файл журнала для развертывания отображается для пользователя, когда происходит сбой активации, и пользователь нажимает кнопку **сведения** в диалоговом окне «полученная ошибка».  
  
 Это поведение можно изменить для конкретного клиента с помощью редактора реестра (**regedit.exe**), чтобы задать путь к пользовательскому файлу журнала. В этом случае [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ведет журнал успешных и неудачных активаций для всех развертываний в одном файле.  
  
> [!CAUTION]
> Неправильное использование редактора реестра может вызвать серьезные проблемы, требующие переустановки операционной системы. Используйте редактор реестра на свой страх и риск.  
  
> [!NOTE]
> Чтобы предотвратить слишком большой размер файла журнала, его необходимо усечь или удалить.  
  
 Следующая процедура описывает, как задать расположение файла настраиваемого журнала для одного клиента.  
  
### <a name="to-set-a-custom-log-file-location"></a>Задание расположения настраиваемого файла журнала  
  
1. Откройте **Regedit.exe**.  
  
2. Перейдите к узлу `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .  
  
3. Присвойте строковому значению `LogFilePath` полный путь и имя файла предпочтительного расположения настраиваемого журнала.  
  
     Это расположение должно находиться в каталоге, к которому пользователь имеет доступ на запись. Например, в Windows Vista создайте следующую структуру папок и задайте для нее значение `LogFilePath` C:\Users \\<username \> \документс\логс\кликконце\инсталлатион.лог.  
  
## <a name="see-also"></a>См. также:  
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
