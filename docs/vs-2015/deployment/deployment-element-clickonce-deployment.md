---
title: '&lt;&gt;элемент Deployment (развертывание ClickOnce) | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#subscription
- urn:schemas-microsoft-com:asm.v2#beforeApplicationStartup
- urn:schemas-microsoft-com:asm.v2#deploymentProvider
- urn:schemas-microsoft-com:asm.v2#update
- urn:schemas-microsoft-com:asm.v2#deployment
- urn:schemas-microsoft-com:asm.v2#expiration
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <deployment> element [ClickOnce deployment manifest]
ms.assetid: 4fafa9c2-97a0-4cea-b8fd-9746dca33af4
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a55b5519d5abb7b40aeca23fed1bc2f8ea2cc33d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194643"
---
# <a name="ltdeploymentgt-element-clickonce-deployment"></a>&lt;&gt;элемент Deployment (развертывание ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Идентифицирует атрибуты, используемые для развертывания обновлений и доступа к системе.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      <deployment   
   install  
   minimumRequiredVersion  
   mapFileExtensions  
   disallowUrlActivation  
   trustUrlParameters  
>   
   <subscription>   
         <update>   
            <beforeApplicationStartup/>   
            <expiration  
               maximumAge  
               unit  
            />  
         </update>    
   </subscription>   
   <deploymentProvider   
      codebase   
   />   
</deployment>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 Элемент `deployment` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v1` . Элемент имеет перечисленные ниже атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`install`|Обязательный. Указывает, определяет ли приложение присутствие в меню " **Пуск** " Windows и на панели управления " **Установка и удаление программ** ". Допустимые значения: `true` и `false`. Если `false` значение равно, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение всегда будет запускать последнюю версию этого приложения из сети и не будет распознать `subscription` элемент.|  
|`minimumRequiredVersion`|Необязательный элемент. Указывает минимальную версию приложения, которая может выполняться на клиенте. Если номер версии приложения меньше номера версии, заданного в манифесте развертывания, приложение не будет запущено. Номера версий должны быть указаны в формате `N.N.N.N` , где `N` — целое число без знака. Если `install` атрибут имеет значение `false` , он `minimumRequiredVersion` не должен быть установлен.|  
|`mapFileExtensions`|Необязательный элемент. По умолчанию — `false`. Если `true` значение равно, все файлы в развертывании должны иметь расширение. deploy. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Это расширение будет удалено из этих файлов сразу после загрузки с веб-сервера. Если приложение публикуется с помощью [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , оно автоматически добавляет это расширение во все файлы. Этот параметр позволяет скачивать все файлы в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывании с веб-сервера, который блокирует передачу файлов, оканчивающихся на "ненадежные" расширения, например exe.|  
|`disallowUrlActivation`|Необязательный элемент. По умолчанию — `false`. Если это `true` значение, то предотвращает запуск установленного приложения путем щелчка URL-адреса или ввода URL-адреса в Internet Explorer. Если `install` атрибут отсутствует, этот атрибут игнорируется.|  
|`trustURLParameters`|Необязательный элемент. По умолчанию — `false`. Если задано `true` значение, URL-адрес должен содержать параметры строки запроса, передаваемые в приложение, во многом аналогично аргументам командной строки, передаваемым в приложение командной строки. Дополнительные сведения см. [в разделе инструкции. Получение сведений о строке запроса в приложении ClickOnce в сети](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).<br /><br /> Если `disallowUrlActivation` атрибут имеет значение `true` , он `trustUrlParameters` должен быть исключен из манифеста или явно задан как `false` .|  
  
 `deployment`Элемент также содержит следующие дочерние элементы.  
  
## <a name="subscription"></a>Подписка  
 Необязательный элемент. Содержит `update` элемент. У элемента `subscription` нет атрибутов. Если `subscription` элемент не существует, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение не будет проверять наличие обновлений. Если `install` атрибут `deployment` элемента имеет значение `false` , `subscription` элемент игнорируется, так как [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение, запускаемое из сети, всегда использует последнюю версию.  
  
## <a name="update"></a>обновить  
 Обязательный. Этот элемент является дочерним по отношению к `subscription` элементу и содержит либо `beforeApplicationStartup` элемент, либо `expiration` . `beforeApplicationStartup` и `expiration` не могут быть указаны в одном манифесте развертывания.  
  
 У элемента `update` нет атрибутов.  
  
## <a name="beforeapplicationstartup"></a>бефореаппликатионстартуп  
 Необязательный элемент. Этот элемент является дочерним по отношению к `update` элементу и не имеет атрибутов. Если `beforeApplicationStartup` элемент существует, приложение будет заблокировано при проверке наличия [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] обновлений, если клиент находится в режиме «в сети». Если этот элемент не существует, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] будет сначала проверять наличие обновлений на основе значений, указанных для `expiration` элемента. `beforeApplicationStartup` и `expiration` не могут быть указаны в одном манифесте развертывания.  
  
## <a name="expiration"></a>expiration  
 Необязательный элемент. Этот элемент является дочерним для `update` элемента и не имеет дочерних элементов. `beforeApplicationStartup` и `expiration` не могут быть указаны в одном манифесте развертывания. При выполнении проверки обновления и обнаружении обновленной версии новая версия кэшируется во время выполнения существующей версии. Новая версия затем устанавливается при следующем запуске [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложения.  
  
 `expiration`Элемент поддерживает следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`maximumAge`|Обязательный. Определяет, как старое текущее обновление должно превышено до того, как приложение выполняет проверку обновлений. Единица измерения времени определяется `unit` атрибутом.|  
|`unit`|Обязательный. Определяет единицу времени для `maximumAge` . Допустимые единицы: `hours` , `days` и `weeks` .|  
  
## <a name="deploymentprovider"></a>deploymentProvider  
 Для .NET Framework 2,0 этот элемент необходим, если манифест развертывания содержит `subscription` раздел. Для .NET Framework 3,5 и более поздних версий этот элемент является необязательным и по умолчанию будет иметь путь к серверу и файлу, в котором был обнаружен манифест развертывания.  
  
 Этот элемент является дочерним по отношению к элементу `deployment` и содержит следующий атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`codebase`|Обязательный. Определяет расположение манифеста развертывания, используемого для обновления приложения, в виде универсального кода ресурса (URI) [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Этот элемент также позволяет пересылать расположения обновлений для установки с компакт-диска. Должен быть допустимым URI.|  
  
## <a name="remarks"></a>Remarks  
 Можно настроить [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] приложение на проверку наличия обновлений при запуске, проверять наличие обновлений после запуска или никогда не проверять наличие обновлений. Чтобы проверить наличие обновлений при запуске, убедитесь, что `beforeApplicationStartup` элемент существует в `update` элементе. Чтобы проверить наличие обновлений после запуска, убедитесь, что `expiration` элемент существует в `update` элементе, а также указаны интервалы обновления.  
  
 Чтобы отключить проверку обновлений, удалите `subscription` элемент. При указании в манифесте развертывания, чтобы не проверять наличие обновлений, по-прежнему можно вручную проверить наличие обновлений с помощью <xref:System.Deployment.Application.ApplicationDeployment.CheckForUpdate%2A> метода.  
  
 Дополнительные сведения о том, как deploymentProvider связывается с обновлениями, см. в разделе [Выбор стратегии обновления ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="examples"></a>Примеры  
 В следующем примере кода показан `deployment` элемент в [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] манифесте развертывания. В примере используется `deploymentProvider` элемент для указания предпочтительного расположения обновления.  
  
```  
<deployment install="true" minimumRequiredVersion="2.0.0.0" mapFileExtension="true" trustUrlParameters="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="6" unit="hours" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="http://www.adatum.com/MyApplication.application" />  
  </deployment>  
```  
  
## <a name="see-also"></a>См. также:  
 [Манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md)
