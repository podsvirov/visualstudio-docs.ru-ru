---
title: Практическое руководство. Подключение к данным в службе
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], connecting to web services
- data sources, creating from web services
- data [Visual Studio], reading from web services
- reading data, from web services
- web services, reading data
- web services, as data sources
- web services, connecting
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 0b49840a2190abfd223edf5643b8d70da1a59d6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282232"
---
# <a name="how-to-connect-to-data-in-a-service"></a>Практическое руководство. Подключение к данным в службе

Вы подключаете приложение к данным, возвращенным из службы, запустив [Мастер настройки источника данных](../data-tools/media/data-source-configuration-wizard.png) и выбрав пункт **Служба** на странице **Выбор типа источника данных** .

После завершения работы мастера в проект добавляется ссылка на службу, которая сразу же становится доступной в [окне Источники данных](add-new-data-sources.md#data-sources-window).

> [!NOTE]
> Элементы, которые отображаются в окне **Источники данных**, зависят от информации, возвращаемой службой. Некоторые службы могут предоставлять недостаточный объем информации для того, чтобы **Мастер настройки источника данных** создал объекты с возможностью привязки. Например, если служба возвращает нетипизированный набор данных, в окне **Источники данных** не отображаются никакие элементы после завершения работы мастера. Это обусловлено тем, что нетипизированные наборы данных не предоставляют схему, поэтому мастер не содержит достаточно сведений для создания источника.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-connect-your-application-to-a-service"></a>Подключение приложения к службе

1. В меню **Данные** выберите команду **Добавить новый источник данных**.

2. На странице **Выбор типа источника данных** выберите пункт **Служба** , а затем нажмите кнопку **Далее**.

3. Введите адрес службы, которую вы хотите использовать, или нажмите кнопку " **обнаружить** ", чтобы найти службы в текущем решении, а затем нажмите кнопку **"перейти"**.

4. При необходимости можно ввести новое **пространство имен** вместо значения по умолчанию.

    > [!NOTE]
    > Нажмите кнопку **Дополнительно** , чтобы открыть [диалоговое окно Настройка ссылки на службу](../data-tools/configure-service-reference-dialog-box.md).

5. Нажмите кнопку **ОК** , чтобы добавить ссылку на службу в проект.

6. Нажмите кнопку **Готово**.

     Источник данных добавлен в окно **Источники данных**.

## <a name="next-steps"></a>Дальнейшие действия

Чтобы добавить функциональные возможности в приложение, выберите элемент в окне **Источники данных** и перетащите его на форму, чтобы создать привязанные элементы управления. Дополнительные сведения см. [в разделе Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел

- [Привязка элементов управления WPF к службе данных WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)
- [Службы Windows Communication Foundation и WCF Data Services в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
