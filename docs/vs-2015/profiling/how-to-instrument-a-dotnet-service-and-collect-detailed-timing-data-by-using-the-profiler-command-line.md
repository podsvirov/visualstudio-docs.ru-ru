---
title: Практическое руководство. Инструментирование службы .NET и сбор подробных данных об использовании времени с помощью командной строки профилировщика | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 271c6ba478cd3e0b8d7e50deb97b96ada0e4dfd8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562041"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Практическое руководство. Инструментирование службы .NET и сбор подробных данных об использовании времени с помощью командной строки профилировщика
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: инструментирование службы .NET и Сбор подробных сведений о времени с помощью командной строки Profiler](https://docs.microsoft.com/visualstudio/profiling/how-to-instrument-a-dotnet-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line).  
  
Эта статья описывает использование программ командной строки для Средств профилирования [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] с целью инструментирования службы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], а также для сбора подробных данных по использованию времени.  
  
> [!NOTE]
>  Вы не можете профилировать службу с помощью метода инструментирования, если ее невозможно перезапустить после запуска компьютера, например, если она запускается только при запуске операционной системы.  
>   
>  Программы командной строки средств профилирования расположены в подкаталоге \Team Tools\Performance Tools каталога установки [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. На 64-разрядных компьютерах доступны 64- и 32-разрядные версии этих программ. Для использования программ командной строки профилировщика необходимо добавить путь к инструментам для переменной среды PATH окна командной строки или добавить его в саму команду. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Добавление данных об уровневом взаимодействии в сеанс профилирования требует определенных процедур со средствами профилирования командной строки. См. раздел [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Чтобы собрать подробные данные по использованию времени из службы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] с помощью метода инструментирования, воспользуйтесь программой [VSInstr.exe](../profiling/vsinstr.md) для создания инструментированной версии компонента. Затем замените неинструментированную версию службы инструментированной, убедившись, что служба настроена для запуска вручную. Далее воспользуйтесь программой [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) для инициализации глобальных переменных среды профилирования и перезагрузите компьютер. Затем запустите профилировщик.  
  
 При запуске службы данные по времени автоматически сохраняются в файл данных. Вы можете приостановить и возобновить сбор данных в ходе сеанса профилирования.  
  
 Чтобы завершить сеанс профилирования, отключите службу и явным образом завершите работу профилировщика. В большинстве случаев рекомендуется сбрасывать переменные среды профилирования в конце сеанса.  
  
## <a name="starting-the-application-with-the-profiler"></a>Запуск приложения с помощью профилировщика  
  
#### <a name="to-start-profiling-a-net-framework-service"></a>Начало профилирования службы .NET Framework  
  
1.  Откройте окно командной строки.  
  
2.  Используйте средство **VSInstr**, чтобы создать инструментированную версию двоичного файла службы.  
  
3.  Замените исходный двоичный файл инструментированной версией. В диспетчере служб Windows убедитесь, что для службы установлен тип запуска "Вручную".  
  
4.  Инициализируйте переменные среды профилирования [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Тип:  
  
     **VSPerfClrEnv /globaltraceon**  
  
5.  Перезагрузите компьютер.  
  
6.  Откройте окно командной строки.  
  
7.  Запуск профилировщика. Тип:  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   Параметр [/start](../profiling/start.md)**:trace** инициализирует профилировщик.  
  
    -   Параметр [/output](../profiling/output.md)**:**`OutputFile` является обязательным для параметра **/start**. `OutputFile` указывает имя и расположение файла данных профилирования (VSP-файла).  
  
     С параметром **/start:trace** можно использовать любой из следующих параметров.  
  
    > [!NOTE]
    >  Параметры **/user** и **/crosssession** обычно являются обязательными для служб профилирования.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Указывает домен и имя пользователя учетной записи, которая является владельцем профилируемого процесса. Этот параметр является обязательным только в том случае, если процесс выполняется в качестве пользователя, отличного от пользователя, вошедшего в систему. Владелец процесса указан в столбце "Имя пользователя" на вкладке "Процессы" диспетчера задач Windows.|  
    |[/crossession](../profiling/crosssession.md)|Включает профилирование процессов в других сеансах. Этот параметр является обязательным, если приложение выполняется в другом сеансе. Идентификатор сеанса указан в столбце идентификатор сеанса на вкладке "процессы" диспетчера задач Windows. **/CS** можно указать как краткую версию **/crosssession**.|  
    |[/waitstart](../profiling/waitstart.md)[**:**`Interval`]|Задает интервал ожидания инициализации профилировщика до возвращения ошибки (в секундах). Если значение `Interval` не указано, профилировщик ожидает в течение неограниченного срока. По умолчанию параметр **/start** возвращает ошибку немедленно.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Для запуска профилировщика с приостановкой сбора данных добавьте параметр **/globaloff** в командную строку **/start**. Используйте параметр **/globalon** для возобновления профилирования.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Собирает данные из счетчика производительности процессора, указанного в файле конфигурации. Сведения счетчика добавляются в данные, собранные для каждого события профилирования.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Задает счетчик производительности Windows, данные которого будут собираться во время профилирования.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Используется с только с параметром **/wincounter**. Указывает время (в миллисекундах) между событиями сбора счетчика производительности Windows. Значение по умолчанию — 500 мс.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Задает события трассировки событий для Windows (ETW), собираемые во время профилирования. События трассировки событий Windows собираются в отдельный ETL-файл.|  
  
8.  Запустите службу из диспетчера служб Windows.  
  
## <a name="controlling-data-collection"></a>Управление сбором данных  
 Пока служба запущена, с помощью параметров программы **VSPerfCmd.exe** можно начинать и останавливать запись в файл данных профилировщика. Управление сбором данных позволяет собирать данные на конкретных этапах выполнения программы, например при запуске или завершении работы службы.  
  
#### <a name="to-start-and-stop-data-collection"></a>Запуск и остановка сбора данных  
  
-   Следующие пары параметров **VSPerfCmd** запускают и останавливают сбор данных. Каждый параметр необходимо указывать в отдельной командной строке. Сбор данных можно включать и отключать несколько раз.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Запускает (**/globalon**) или останавливает (**/globaloff**) сбор данных для всех процессов.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Запускает (**/processon**) или останавливает (**/processoff**) сбор данных для процесса с указанным идентификатором процесса (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Запускает (**/threadon**) или останавливает (**/threadoff**) сбор данных для потока с указанным идентификатором потока (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Завершение сеанса профилирования  
 Для завершения сеанса профилирования остановите службу, в которой выполняется инструментированный компонент, а затем выполните команду **VSPerfCmd** [/shutdown](../profiling/shutdown.md), чтобы выключить профилировщик и закрыть файл данных профилирования. Команда **VSPerfClrEnv /globaloff** удаляет переменные среды, используемые для профилирования.  
  
 Для вступления в силу новых параметров среды необходимо перезагрузить компьютер.  
  
#### <a name="to-end-a-profiling-session"></a>Завершение сеанса профилирования  
  
1.  Остановите службу из диспетчера служб.  
  
2.  Завершите работу профилировщика. Тип:  
  
     **VSPerfCmd /shutdown**  
  
3.  После завершения всего профилирования очистите переменные среды профилирования. Тип:  
  
     **VSPerfClrEnv /globaloff**  
  
4.  Замените инструментированный модуль исходным. При необходимости измените тип запуска службы.  
  
5.  Перезагрузите компьютер.  
  
## <a name="see-also"></a>См. также  
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)   
 [Представление данных метода инструментирования](../profiling/instrumentation-method-data-views.md)


