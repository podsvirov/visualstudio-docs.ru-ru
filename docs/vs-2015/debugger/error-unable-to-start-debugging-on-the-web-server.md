---
title: 'Ошибка: не удается запустить отладку на веб-сервере | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185475"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Ошибка: не удается запустить отладку на веб-сервере
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При попытке отладить приложение ASP.NET, запущенное на веб-сервере, может появиться следующее сообщение об ошибке: "Не удается запустить отладку на веб-сервере".
  
Во многих случаях эта ошибка возникает из-за неправильной настройки служб IIS.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a>Проверьте конфигурацию IIS

После выполнения шагов по устранению проблемы, описанной здесь, и перед повторной попыткой отладки, может также потребоваться сброс IIS. Это можно сделать, открыв командную строку администратора и введя текст `iisreset` , или можно сделать это в диспетчере служб IIS. 

* Закройте и перезапустите пулы приложений, а затем повторите попытку.

    Возможно, работа пула приложений была остановлена или внесены другие изменения конфигурации, и вам может потребоваться остановить и перезапустить пул приложений.
    
    > [!NOTE]
    > Если пул приложений останавливается, может потребоваться удалить модуль переопределения URL-адресов с помощью панели управления, а затем переустановить его с использованием установщика веб-платформы (ВПИ). Это может быть вызвано значительным обновлением системы.

* Проверьте конфигурацию пула приложений, исправьте ее при необходимости и попробуйте еще раз.

    Если учетные данные пароля изменились, может потребоваться обновить их в пуле приложений. Кроме того, если вы недавно установили ASP.NET, пул приложений может быть настроен для неверной версии ASP.NET. Устраните проблему и перезапустите пул приложений.
    
* Убедитесь, что папка веб-приложения имеет нужные разрешения.

    Убедитесь, что вы предоставляете права на чтение и выполнение для папки веб-приложения IIS_IUSRS или IUSR (или определенному пользователю, связанному с пулом приложений). Устраните проблему и перезапустите пул приложений.

* Если вы используете файл HOSTS с локальными адресами, попробуйте использовать вместо IP-адреса компьютера петлевой адрес.

* Откройте страницу localhost в браузере.

     Если службы IIS не установлены правильно, должны отобразиться ошибки при вводе `http://localhost` в браузере.
     
     Сведения о развертывании в службах IIS см. в разделе [Remote Debugging ASP.NET на удаленном компьютере IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) или для ASP.NET Core [публикации в службах IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Убедитесь, что в IIS установлена правильная версия ASP.NET.  См. статью [развертывание приложения ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) или ASP.NET Core [Публикация в службах IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Создайте базовое приложение ASP.NET на сервере.

     Если добиться работы приложения с отладчиком не удается, попробуйте создать простое локальное приложение ASP.NET на сервере и выполнить отладку этого простого приложения. Если вы можете выполнить отладку базового приложения, это может помочь в определении различий между двумя конфигурациями.
  
* Устраните ошибки проверки подлинности, если используется только IP-адрес

     По умолчанию предполагается, что IP-адреса являются частью Интернет-зоны, и проверка подлинности NTLM для них не выполняется. Если веб-сайт настроен в службах IIS для обязательной проверки подлинности, проверка подлинности завершится ошибкой. Чтобы решить эту проблему, укажите вместо IP-адреса имя удаленного компьютера.
     
## <a name="other-causes"></a>Другие причины

При использовании более старой версии Visual Studio:

- Перезапустите Visual Studio с повышенными привилегиями и повторите попытку.

    Ошибка в более ранних версиях (Исправлена позже) требовала повышенных привилегий в некоторых сценариях отладки ASP.NET.
    
- Если запущено несколько экземпляров Visual Studio, повторно откройте проект в одном экземпляре Visual Studio и повторите попытку.

## <a name="see-also"></a>См. также:  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
