---
title: Задание расположения настраиваемого файла журнала (ошибки развертывания ClickOnce)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- troubleshooting ClickOnce deployments
- ClickOnce deployment, troubleshooting
- ClickOnce deployment, error logging
ms.assetid: 77424414-7f0e-4b99-94bb-ea130de92d09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5b5cf73a685eb68e389e6531022200acbefbfd2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809746"
---
# <a name="how-to-set-a-custom-log-file-location-for-clickonce-deployment-errors"></a>Практическое руководство. Задание местоположения файла пользовательского журнала для ошибок развертывания ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] обслуживает файлы журналов активации для всех развертываний. В этих журналах задокументированы все ошибки, относящиеся к установке и инициализации [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания. По умолчанию [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] создает один файл журнала для каждой активации развертывания. Эти файлы журналов хранятся в папке Temporary Internet Files. Файл журнала для развертывания отображается для пользователя, когда происходит сбой активации, и пользователь нажимает кнопку **сведения** в диалоговом окне «полученная ошибка».

 Это поведение можно изменить для конкретного клиента с помощью редактора реестра (**regedit.exe**), чтобы задать путь к пользовательскому файлу журнала. В этом случае [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ведет журнал успешных и неудачных активаций для всех развертываний в одном файле.

> [!CAUTION]
> Неправильное использование редактора реестра может вызвать серьезные проблемы, требующие переустановки операционной системы. Используйте редактор реестра на свой страх и риск.

> [!NOTE]
> Чтобы предотвратить слишком большой размер файла журнала, его необходимо усечь или удалить.

 Следующая процедура описывает, как задать расположение файла настраиваемого журнала для одного клиента.

### <a name="to-set-a-custom-log-file-location"></a>Задание расположения настраиваемого файла журнала

1. Откройте **Regedit.exe**.

2. Перейдите к узлу `HKCU\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment` .

3. Присвойте строковому значению `LogFilePath` полный путь и имя файла предпочтительного расположения настраиваемого журнала.

     Это расположение должно находиться в каталоге, к которому пользователь имеет доступ на запись. Например, в Windows Vista создайте следующую структуру папок и задайте для нее значение `LogFilePath` *C:\Users \\ \<username> \документс\логс\кликконце\инсталлатион.лог*.

## <a name="see-also"></a>См. также раздел
- [Устранение неполадок развертываний ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)