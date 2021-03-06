---
ms.openlocfilehash: b8002d9e911c8d8c07a5aaf5286168e49a374a7c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85292198"
---

1. Закройте и снова откройте консоль управления IIS, чтобы отобразить обновленные параметры конфигурации в пользовательском интерфейсе.

2. В службах IIS щелкните правой кнопкой мыши элемент **Веб-сайт по умолчанию** и выберите **Развернуть** > **Включить публикацию веб-развертывания**.

    ![Настройка конфигурации веб-развертывания](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

   Если меню **Развернуть** не отображается, ознакомьтесь с предыдущим разделом, чтобы проверить, выполняется ли веб-развертывание.

3. Просмотрите параметры в диалоговом окне **Включить публикацию веб-развертывания**.

4. Щелкните **Настройка**.

    Выходные данные в панели **Результаты** показывают, что права доступа предоставлены конкретному пользователю, а в указанном в диалоговом окне месте был создан файл с расширением *.publishsettings*.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    В зависимости от конфигурации Windows Server и служб IIS в XML-файле будут представлены разные значения. Ниже описываются некоторые значения, которые могут вам встретиться.

   * Файл *msdeploy.axd*, на который ссылается атрибут `publishUrl`, представляет собой динамически создаваемый файл обработчика HTTP для веб-развертывания. (В целях тестирования, как правило, можно использовать `http://myhostname:8172`.)
   * Порту `publishUrl` присваивается значение 8172, которое по умолчанию используется для веб-развертывания.
   * Порту `destinationAppUrl` присваивается значение 80, которое по умолчанию используется для служб IIS.
   * Если вам не удается подключиться к удаленному узлу в Visual Studio с использованием имени узла (на последующих шагах), попробуйте использовать вместо имени узла IP-адрес.

     > [!NOTE]
     > Если вы выполняете публикацию в службах IIS, работающих на виртуальной машине Azure, необходимо открыть порты для веб-развертывания и служб IIS в группе безопасности сети. Дополнительные сведения см. в статье [Установка и запуск служб IIS](/azure/virtual-machines/windows/quick-create-portal#install-web-server).

5. Скопируйте этот файл на компьютер, на котором выполняется среда Visual Studio.
