---
title: Настройка брандмауэра Windows для удаленной отладки | Документация Майкрософт
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fa5d60d7fe662cff31b54bf3a13c203f4b6d8c9
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350697"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Настройка брандмауэра Windows для удаленной отладки

В сети, защищенной брандмауэром Windows, необходимо настроить брандмауэр для разрешения удаленной отладки. Visual Studio и средства удаленной отладки пытаются открыть правильные порты брандмауэра во время установки или запуска, но также может потребоваться открыть порты или разрешить отладку приложений вручную.

В этой статье описывается настройка брандмауэра Windows для включения удаленной отладки на компьютерах с Windows 10, 8/8.1 и 7, а также на компьютерах с Windows Server 2012 R2, 2012 и 2008 R2. Компьютер с Visual Studio и удаленный компьютер не должны работать под управлением разных операционных систем. Например, на компьютере с Visual Studio может использоваться Windows 10, а на удаленном компьютере — Windows Server 2012 R2.

>[!NOTE]
>Инструкции по настройке брандмауэра Windows немного различаются в зависимости от операционной системы. Кроме того, они другие в прежних версиях Windows. В параметрах Windows 8/8.1, Windows 10 и Windows Server 2012 используется слово *приложение*, тогда как в Windows 7 и Windows Server 2008 используется слово *программа*.

## <a name="configure-ports-for-remote-debugging"></a>Настройка портов для удаленной отладки

Visual Studio и удаленный отладчик пытаются открыть правильные порты во время установки или запуска. Однако в некоторых сценариях, таких использование стороннего брандмауэра, может потребоваться открыть порты вручную.

**Открытие порта**

1. В меню Windows **Пуск** найдите и откройте **Брандмауэр Windows в режиме повышенной безопасности**. В Windows 10 это **Брандмауэр Защитника Windows с повышенной безопасностью**.

1. Для нового входящего порта выберите **Правила для входящего трафика**, затем **Новое правило**. Для правила для исходящего трафика выберите **Правила для исходящего трафика**.

1. В окне **мастера создания правил для входящего трафика** выберите **Порт**, а затем нажмите кнопку **Далее**.

1. Выберите **TCP** или **UDP** в зависимости от номера порта из следующих таблиц.

1. В разделе **Определенные локальные порты** введите номер порта из следующих таблиц, а затем нажмите кнопку **Далее**.

1. Нажмите кнопку **Проверить соединение**, а затем **Далее**.

1. Выберите один тип сети или несколько для включения, в том числе тип сети для удаленного подключения, а затем нажмите кнопку **Далее**.

1. Присвойте правилу имя (например, **msvsmon**, **IIS** или **Веб-развертывание**), а затем нажмите кнопку **Готово**.

   Новое правило должно появиться и быть выбранным в списке **Правила для входящего трафика** или **Правила для исходящего трафика**.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Порты на удаленном компьютере, обеспечивающие удаленную отладку

Для удаленной отладки на удаленном компьютере должны быть открыты следующие порты.

::: moniker range="vs-2017"

|**Порты**|**Входящий или исходящий**|**Протокол**|**Описание**|
|-|-|-|-|
|4022|Входящий|TCP|Для Visual Studio 2017. Номер порта увеличивается на 2 с каждой версией Visual Studio. Более подробную информацию см. в разделе [Назначение портов удаленного отладчика Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|Входящий|TCP|Для Visual Studio 2017. Номер порта увеличивается на 2 с каждой версией Visual Studio. Этот порт используется только для удаленной отладки 32-разрядного процесса из 64-разрядной версии удаленного отладчика. Более подробную информацию см. в разделе [Назначение портов удаленного отладчика Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Исходящий|UDP|(Необязательно.) Требуется для обнаружения удаленного отладчика.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Порты**|**Входящий или исходящий**|**Протокол**|**Описание**|
|-|-|-|-|
|4024|Входящий|TCP|Для Visual Studio 2019. Номер порта увеличивается на 2 с каждой версией Visual Studio. Более подробную информацию см. в разделе [Назначение портов удаленного отладчика Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|Входящий|TCP|Для Visual Studio 2019. Номер порта увеличивается на 2 с каждой версией Visual Studio. Этот порт используется только для удаленной отладки 32-разрядного процесса из 64-разрядной версии удаленного отладчика. Более подробную информацию см. в разделе [Назначение портов удаленного отладчика Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|Исходящий|UDP|(Необязательно.) Требуется для обнаружения удаленного отладчика.|

::: moniker-end

Если выбрать параметр **Использовать режим совместимости управляемого кода** в разделе **Сервис** > **Параметры** > **Отладка**, следует открыть эти дополнительные порты удаленного отладчика. Режим совместимости управляемого кода позволяет использовать устаревшую версию отладчика Visual Studio 2010.

|**Порты**|**Входящий или исходящий**|**Протокол**|**Описание**|
|-|-|-|-|
|135, 139, 445|Исходящий|TCP|Обязательный.|
|137, 138|Исходящий|UDP|Обязательный.|

Если, согласно политике домена, обмен данными по сети должен выполняться по протоколу IPSec, необходимо открыть дополнительные порты как на компьютере с Visual Studio, так и на удаленном компьютере. Для отладки на удаленном веб-сервере IIS откройте порт 80 на удаленном компьютере.

|**Порты**|**Входящий или исходящий**|**Протокол**|**Описание**|
|-|-|-|-|
|500, 4500|Исходящий|UDP|Требуется, если в соответствии с политикой домена обмен данными по сети должен осуществляться по протоколу IPSec.|
|80|Исходящий|TCP|Требуется для отладки веб-сервера.|

Сведения о разрешении взаимодействия с конкретными приложениями через брандмауэр Windows см. в разделе [Настройка удаленной отладки через брандмауэр Windows](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Настройка удаленной отладки через брандмауэр Windows

Можно установить средства удаленной отладки на удаленном компьютере или запустить их из общей папки. В любом случае необходимо правильно настроить брандмауэр удаленного компьютера.

На удаленном компьютере средства удаленной отладки находятся в следующей папке:

*\<Visual Studio installation directory\>\\Common7\\IDE\\Remote Debugger\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Разрешение и настройка удаленного отладчика через брандмауэр Windows

1. В меню Windows **Пуск** найдите и откройте **Брандмауэр Windows** или **Брандмауэр Защитника Windows**.

1. Щелкните **Разрешить взаимодействие с приложением через брандмауэр Windows**.

1. Если **удаленный отладчик** или **удаленный отладчик Visual Studio** не отображаются в разделе **Разрешенные приложения и компоненты**, выберите **Изменить параметры**, а затем выберите **Разрешить другое приложение**.

1. Если приложение удаленного отладчика по-прежнему отсутствует в диалоговом окне **Добавление приложения**, нажмите кнопку **Обзор** и в зависимости от архитектуры приложения перейдите к папке *\<Visual Studio installation directory\>\\Common7\\IDE\\Remote Debugger\\\<x86*, *x64*, or *Appx*\>. Выберите *msvsmon.exe*, а затем нажмите кнопку **Добавить**.

1. В списке **Приложения** выберите только что добавленный **удаленный отладчик**. Выберите **Типы сетей**, затем выберите один тип сети или несколько для включения, в том числе тип сети для удаленного подключения.

1. Выберите **Добавить**, а затем нажмите кнопку **ОК**.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Устранение неполадок подключения удаленной отладки

Если вы не можете присоединиться к приложению с помощью удаленного отладчика, проверьте правильность всех портов брандмауэра, протоколов, типов сетей и параметров приложения для удаленной отладки.

- В меню Windows **Пуск** найдите и откройте **Брандмауэр Windows**, а затем выберите **Разрешить взаимодействие с приложением через брандмауэр Windows**. Убедитесь, что в списке **Разрешенные приложения и компоненты** отображается выбранный **удаленный отладчик** или **удаленный отладчик Visual Studio** и выбраны правильные типы сетей. В противном случае [добавьте необходимые приложения и параметры](#configure-remote-debugging-through-windows-firewall).

- В меню Windows **Пуск** найдите и откройте **Брандмауэр Windows в режиме повышенной безопасности**. Убедитесь, что в разделе **Правила для входящего трафика** (и при необходимости в разделе **Правила для исходящего трафика**) отображается **удаленный отладчик** или **удаленный отладчик Visual Studio** с зеленым флажком, а все параметры заданы правильно.

  - Чтобы просмотреть или изменить параметры правила, щелкните правой кнопкой мыши приложение **Удаленный отладчик** в списке и выберите пункт **Свойства**. Используйте вкладки **Свойства**, чтобы включить или отключить правило или изменить номера портов, протоколы или типы сетей.
  - Если приложение удаленного отладчика не отображается в списке правил, [добавьте и настройте нужные порты](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>См. также

- [Удаленная отладка](../debugger/remote-debugging.md)
- [Назначение портов удаленного отладчика Visual Studio](../debugger/remote-debugger-port-assignments.md)
