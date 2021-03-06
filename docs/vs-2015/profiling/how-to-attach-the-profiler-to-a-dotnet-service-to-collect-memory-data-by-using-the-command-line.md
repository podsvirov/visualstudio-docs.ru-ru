---
title: Практическое руководство. Подключение профилировщика к службе .NET для сбора данных по использованию памяти с помощью командной строки | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a1601b855cfc895aa01c6b72cbbe36b59980bd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842901"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Практическое руководство. Присоединение профилировщика к службе .NET для сбора данных об использовании памяти с помощью командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описывается использование программ командной строки для Средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с целью подключения профилировщика к службе [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] и сбора данных по использованию памяти. С помощью этих программ можно собирать сведения о количестве выделений памяти и объемах выделяемой памяти, а также сведения о времени существования объектов памяти.  

> [!NOTE]
> Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Программы командной строки средств профилирования расположены в подкаталоге \Team Tools\Performance Tools каталога установки [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. На 64-разрядных компьютерах доступны 64- и 32-разрядные версии этих программ. Для использования средств командной строки профилировщика необходимо добавить путь к этим средствам в переменную среды PATH окна командной строки или указать этот путь при вызове команды. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Для сбора данных по использованию памяти, полученных от службы [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], нужно воспользоваться программой [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md), чтобы инициализировать соответствующие переменные среды на том компьютере, где запущена служба. Чтобы настроить компьютер для профилирования, его нужно перезагрузить.  

 Затем следует воспользоваться программой [VSPerfCmd](../profiling/vsperfcmd.md) для подключения профилировщика к процессу службы. Когда профилировщик будет подключен к службе, можно будет приостанавливать и возобновлять сбор данных.  

 Чтобы завершить сеанс профилирования, необходимо отключить профилировщик от службы и явным образом завершить его работу. В большинстве случаев рекомендуется сбрасывать переменные среды профилирования в конце сеанса.  

## <a name="attaching-the-profiler"></a>Подключение профилировщика  

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Подключение профилировщика к службе .NET Framework  

1. При необходимости установите службу.  

2. Откройте окно командной строки.  

3. Инициализируйте переменные среды профилирования. Тип:  

    **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]  

   - Параметры **/globalsamplegclife** и **/globalsamplegclife** задают тип собираемых данных по использованию памяти. Задайте один и только один из указанных ниже параметров.  

     **/глобалсамплегк**  
     Включает сбор данных по выделению памяти.  

     **/глобалсамплегклифе**  
     Включает сбор данных по выделению памяти и времени существования объектов.  

   - Параметр **/samplelineoff** отключает сбор сведений о номерах строк исходного кода.  

4. Перезагрузите компьютер, чтобы применить новую конфигурацию среды.  

5. При необходимости запустите службу.  

6. Откройте окно командной строки. Если необходимо, добавьте путь к профилировщику в переменную среды PATH.  

7. Запуск профилировщика. Тип:  

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Sample**  [/Output](../profiling/output.md) **:** `OutputFile` [ `Options` ]  

   - Параметр **/start:sample** инициализирует профилировщик.  

   - Параметр **/output**`OutputFile` является обязательным при использовании параметра **/start**. `OutputFile` указывает имя и расположение файла данных профилирования (VSP-файла).  

     С параметром **/start:sample** можно использовать один или несколько из указанных ниже параметров.  

   > [!NOTE]
   > Параметры **/user** и **/crosssession** обычно являются обязательными для служб.  

   |                                 Параметр                                  |                                                                                                                                                   Описание                                                                                                                                                    |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` |                      Задает домен и имя пользователя учетной записи, которая является владельцем процесса. Этот параметр является обязательным, если процесс выполняется от имени пользователя, отличного от вошедшего в систему. Владелец процесса указан в столбце "Имя пользователя" на вкладке "Процессы" диспетчера задач Windows.                       |
   |              [/crossession](../profiling/crosssession.md)              | Включает профилирование процессов в других сеансах входа. Этот параметр является обязательным, если приложение ASP.NET выполняется в другом сеансе. Идентификатор сеанса указан в столбце "Идентификатор сеанса" на вкладке "Процессы" диспетчера задач Windows. **/CS** можно указать как краткую версию **/crosssession**. |
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain` **\\** ]`UserName` |                                                    Задает необязательный домен и имя пользователя учетной записи для входа в систему, от имени которой запускается служба. Учетная запись для входа указана в столбце "Вход от имени" службы в диспетчере служб Windows.                                                     |
   |          [/CrossSession&#124;CS](../profiling/crosssession.md)          |                                                                                                                             Включает профилирование процессов в других сеансах входа.                                                                                                                              |
   |    [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`     |                                                                                                                    Задает счетчик производительности Windows, данные которого будут собираться во время профилирования.                                                                                                                     |
   |         [/automark](../profiling/automark.md) **:** `Interval`          |                                                                                  Используется с только с параметром **/wincounter**. Указывает время (в миллисекундах) между событиями сбора счетчика производительности Windows. Значение по умолчанию — 500 мс.                                                                                   |
   |       [/events](../profiling/events-vsperfcmd.md) **:** `Config`        |                                                                                     Задает события трассировки событий для Windows (ETW), собираемые во время профилирования. События трассировки событий Windows собираются в отдельный ETL-файл.                                                                                     |

8. Подключите профилировщик к службе. Тип:  

    **VSPerfCmd**[/attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/TargetCLR](../profiling/targetclr.md)**:** `Version` ]    

   - Укажите идентификатор или имя процесса службы. Просмотреть идентификаторы и имена всех запущенных процессов можно в диспетчере задач Windows.  

   - **TargetCLR:** `Version` Указывает версию общеязыковой среды выполнения (CLR) для профилирования, когда в приложении загружается более одной версии среды выполнения. Необязательный параметр.  

## <a name="controlling-data-collection"></a>Управление сбором данных  
 Пока служба запущена, с помощью параметров программы **VSPerfCmd.exe** можно останавливать и начинать запись данных в файл данных профилировщика. Управление сбором данных позволяет собирать данные на конкретных этапах выполнения программы, например при запуске или завершении работы приложения.  

#### <a name="to-start-and-stop-data-collection"></a>Запуск и остановка сбора данных  

- Следующие пары параметров **VSPerfCmd** запускают и останавливают сбор данных. Каждый параметр необходимо указывать в отдельной командной строке. Сбор данных можно включать и отключать несколько раз.  

    |Параметр|Описание|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Запускает ( **/globalon**) или останавливает ( **/globaloff**) сбор данных для всех процессов.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Запускает ( **/processon**) или останавливает ( **/processoff**) сбор данных для процесса с указанным идентификатором процесса (`PID`).|  
    |**/Attach:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/attach** запускает сбор данных для процесса с указанным идентификатором или именем процесса. **/Detach** останавливает сбор данных для указанного процесса или для всех процессов, если конкретный процесс не указан.|  

## <a name="ending-the-profiling-session"></a>Завершение сеанса профилирования  
 Для завершения сеанса профилирования профилировщик не должен выполнять сбор данных. Чтобы остановить сбор данных в приложении, для которого выполняется профилирование методом выборки, можно остановить службу или вызвать параметр **VSPerfCmd /detach**. Затем можно вызвать параметр **VSPerfCmd** [/shutdown](../profiling/shutdown.md), чтобы завершить работу профилировщика и закрыть файл данных профилирования. Команда **VSPerfClrEnv/globaloff** очищает переменные среды профилирования, однако конфигурация системы не сбрасывается до перезагрузки компьютера.  

#### <a name="to-end-a-profiling-session"></a>Завершение сеанса профилирования  

1. Чтобы отключить профилировщик от целевого приложения, выполните одно из указанных ниже действий.  

    - Остановите службу.  

         -или-  

    - Введите команду **VSPerfCmd /detach**.  

2. Завершите работу профилировщика. Тип:  

     **VSPerfCmd /shutdown**  

3. (Необязательно) Сбросьте переменные среды профилирования. Тип:  

     **VSPerfClrEnv /globaloff**  

4. Перезагрузите компьютер.  

## <a name="see-also"></a>См. также:  
 [Службы профилирования](../profiling/command-line-profiling-of-services.md)   
 [Представления данных в памяти .NET](../profiling/dotnet-memory-data-views.md)
