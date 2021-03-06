---
title: Создание локализованного пакета начального загрузчика | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- localized bootstrapper packages
- dependencies, creating localized bootstrapper packages
- prerequisites, creating localized bootstrapper packages
ms.assetid: 66a1bc7e-6540-4164-963d-557196a69d8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c673c6488b93802877ef088d9d9a1a4793cf50b
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852489"
---
# <a name="how-to-create-a-localized-bootstrapper-package"></a>Практическое руководство. Создание локализованного пакета начального загрузчика
После создания пакета начального загрузчика можно создать локализованные версии пакета начального загрузчика, создав два дополнительных файла для каждого языкового стандарта: файл условий лицензии на программное обеспечение (например, *EULA. RTF*) и манифест пакета (*package.xml*).

 По умолчанию в Visual Studio 2010 локализованные пакеты начальной загрузки включены только для .NET Framework 4, .NET Framework 4 Client Profile, F# Runtime 2.0 и F# Runtime 4.0. Чтобы создать локализованные пакеты для других начальных загрузчиков, сделайте следующее.

1. Создайте папку с именем в виде имени локали в *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> *.

2. Создайте файл, содержащий условия лицензионного соглашения на использование программного обеспечения, для пакета начального загрузчика и сохраните его в новую папку.

3. Создайте манифест пакета с именем *package.xml*, обновите строки и язык и региональные параметры и вставьте файл в новую папку. Если вы уже создали начальный загрузчик Visual Studio на целевом языке, вы можете скопировать файл *package.xml* Visual Studio и изменить его на этом шаге.

> [!NOTE]
> Если для развертывания приложений используется проект установки, приложение можно локализовать, изменив свойство **Локализация**.

 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-a-localized-bootstrapper-package"></a>Создание пакета локализованного начального загрузчика

1. Создайте папку с именем, соответствующим языковому стандарту.

     На 32-разрядных компьютерах создайте папку в папке *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> \\ * .

     На 64-разрядных компьютерах создайте папку в папке *\Program Files (86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages \\ \<BootstrapperPackageName> \\ * .

     В следующей таблице показано, какие имена папок можно использовать для соотнесения с языковым стандартом.

    |Языковой стандарт|Имя папки|
    |------------|-----------------|
    |Китайский (упрощенное письмо)|zh-Hans|
    |Китайский (традиционное письмо)|zh-Hant|
    |Чешский|cs|
    |Немецкий|de|
    |Английский|en|
    |Испанский|es|
    |Французский|fr|
    |Итальянский|it|
    |Корейский|ko|
    |Японский|ja|
    |Польский|pl|
    |Португальский (Бразилия)|pt-BR|
    |Русский|ru|
    |Турецкий|tr|

2. Создайте файл, содержащий условия лицензионного соглашения на использование программного обеспечения, для пакета начального загрузчика и сохраните его в новую папку.

3. Создайте манифест пакета с именем *package.xml* и вставьте его в новую папку. Дополнительные сведения см. [в разделе инструкции. Создание манифеста пакета](../deployment/how-to-create-a-package-manifest.md).

4. Обновите раздел `<Strings>` манифеста пакета, так чтобы язык строк соответствовал языковому стандарту.

5. Измените значение `<String Name="Culture">` таким образом, чтобы оно соответствовало имени папки.

6. Сохраните файл *package.xml* .

### <a name="to-create-a-bootstrapper-package-for-net-framework-35-service-pack-1-localized-in-french"></a>Создание пакета начального загрузчика для .NET Framework 3.5 Service Pack 1 с локализацией на французском языке

1. Создайте папку с именем *fr*. Имя папки должно совпадать с именем языкового стандарта.

     На 32-разрядных компьютерах создайте папку в папке *\Program Files\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1 \\ * .

     На 64-разрядных компьютерах — в папке *\Program Files (86)\Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\\*.

2. Установите локализованную версию условий лицензионного соглашения на использование программного обеспечения в папку *fr* .

3. Скопируйте файл *\Program Files (x86) \Microsoft SDKs\Windows\v7.0A\Bootstrapper\Packages\DotNetFX35SP1\en\package.xml* в папку *fr* и откройте его в конструкторе XML.

4. Обновите раздел `<Strings>` манифеста пакета, так чтобы строки с сообщениями об ошибках были на французском языке.

5. Измените `<String Name="Culture">` значение на *fr*.

6. Сохраните файл *package.xml* .

## <a name="see-also"></a>См. также
- [Создание пакетов начального загрузчика](../deployment/creating-bootstrapper-packages.md)
- [Обязательные требования к развертыванию приложений](../deployment/application-deployment-prerequisites.md)
- [Как создать манифест пакета](../deployment/how-to-create-a-package-manifest.md)