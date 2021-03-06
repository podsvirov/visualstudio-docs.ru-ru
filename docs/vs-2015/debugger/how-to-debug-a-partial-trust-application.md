---
title: Как выполнять отладку приложения с частичным доверием | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], partial trust applications
- partial trust applications
- security [Visual Studio], partial trust applications
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 030fef750cc1e0f0932de32fca1a0ffef56bc8f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704489"
---
# <a name="how-to-debug-a-partial-trust-application"></a>How to: Debug a Partial Trust Application
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Применяется к приложениям Windows и консольным приложениям.  
  
 [Технология ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md) упрощает развертывание приложений с частичным доверием, использующих преимущества [управления доступом для кода](https://msdn.microsoft.com/library/859af632-c80d-4736-8d6f-1e01b09ce127) , чтобы ограничить доступ к ресурсам на компьютере.  
  
 Отладка приложения частичного доверия может быть сложной задачей, так как приложения частичного доверия имеют различные права (и поэтому ведут себя по-разному) в зависимости от того, откуда они установлены. Если из интернета, то у приложения частичного доверия будут мало прав. Если из локальной интрасети, прав будет больше, а если с локального компьютера, оно будет иметь полные права. Также возможны настраиваемые зоны, с настраиваемыми разрешениями. Может потребоваться отладка приложений частичного доверия при любых условиях из упомянутых. К счастью, Visual Studio упрощает и это.  
  
 Перед началом сеанса отладки в Visual Studio можно выбрать нужную зону для имитации места, откуда установлено приложение. При запуске отладки приложение будет иметь права, соответствующие приложению частичного доверия из этой зоны. Это позволяет увидеть поведение приложения так, как оно будет выглядеть для пользователя, загрузившего его из этой зоны.  
  
 Если приложение пытается выполнить действие, на которое не имеет разрешения, то возникнет исключение. В этот момент помощник по исключениям предоставляет возможность добавить дополнительные права, что позволяет перезапустить отладку с достаточными правами и избежать проблем.  
  
 Позже можно вернуться назад и увидеть, какие права были добавлены во время отладки. Если было необходимо добавить разрешение во время отладки, значит, вероятно, необходимо добавить запрос согласия пользователя в этой точке кода.  
  
> [!NOTE]
> Визуализаторы отладчика требуют больше прав, чем разрешено приложениям частичного доверия. Визуализатор не загрузит переменную или объект, если остановка произошла в коде с частичным доверием. Чтобы отлаживать, используя визуализатор, необходимо запустить код с полным доверием.  
  
### <a name="to-choose-a-zone-for-your-partial-trust-application"></a>Выбор зоны для приложения частичного доверия  
  
1. В меню **проект** выберите**Свойства** _имя_проекта_.  
  
2. На страницах свойств *имяПроекта* перейдите на страницу **Безопасность** .  
  
3. Выберите **включить параметры безопасности ClickOnce**.  
  
4. В разделе **зона, из которой будет установлено приложение**, щелкните раскрывающийся список и выберите зону, из которой нужно смоделировать приложение.  
  
     **Разрешения, необходимые для сетки приложения** , показывают все доступные разрешения. Установленный флажок указывает разрешения, данные приложению.  
  
5. Если выбранная зона была **(настраиваемая)**, выберите правильные пользовательские параметры в столбце **параметр** сетки **разрешения** .  
  
6. Нажмите кнопку **ОК**, чтобы закрыть страницы свойств.  
  
### <a name="to-add-an-extra-permission-when-a-security-exception-occurs"></a>Добавление дополнительного разрешения при возникновении исключения безопасности  
  
1. Откроется диалоговое окно **Помощник по исключениям** с сообщением: **SecurityException не обработано.**  
  
2. В диалоговом окне **Помощник по исключениям** в разделе **действия**щелкните **Добавить разрешение в проект**.  
  
3. Откроется диалоговое окно **перезапуск отладки** .  
  
    - Если вы хотите перезапустить сеанс отладки с новым разрешением, нажмите кнопку **Да**.  
  
    - Если вы еще не хотите перезапускать, нажмите кнопку **нет**.  
  
### <a name="to-view-extra-permissions-added-while-debugging"></a>Просмотр дополнительных разрешений, добавленных во время отладки  
  
1. В меню **проект** выберите**Свойства** _имя_проекта_.  
  
2. На страницах свойств *имяПроекта* перейдите на страницу **Безопасность** .  
  
3. Просмотрите разрешения, **необходимые для сетки приложения** . Любое дополнительное разрешение, которое вы добавили, имеет два значка в **включенном** столбце: обычная галочка, в которой есть все включенные разрешения, и дополнительный значок, который выглядит как выноска, содержащая букву "i".  
  
4. Используйте вертикальную полосу прокрутки, чтобы просмотреть все **разрешения, необходимые** для сетки приложения.  
  
## <a name="see-also"></a>См. также:  
 [Безопасность и развертывание ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)
