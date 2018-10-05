---
title: 'MSBuild: целевая рабочая среда и целевая платформа | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e699096af425897e3bd3c724b483cc3fea2ffb29
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572854"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild: целевая рабочая среда и целевая платформа
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [MSBuild Целевая рабочая среда и целевая платформа](https://docs.microsoft.com/visualstudio/msbuild/msbuild-target-framework-and-target-platform).  
  
  
Проект может быть создан для выполнения в *требуемой версии .NET Framework*, которая является конкретной версией платформы .NET Framework, и на *целевой платформе*, которая является конкретной программной архитектурой.  Например, можно настроить приложение для выполнения в .NET Framework 2.0 на 32-разрядной платформе, которая совместима с семейством процессоров 802x86 («x86»). Сочетание требуемой версии .NET Framework и целевой платформы называется *целевым контекстом*.  
  
## <a name="target-framework-and-profile"></a>Целевая платформа и профиль  
 Целевая платформа — это конкретная версия [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], для выполнения на которой создан проект. Спецификация целевой платформы является необходимым условием, поскольку она позволяет использовать возможности компилятора и ссылки на сборки, предназначенные исключительно для этой версии платформы.  
  
 В настоящее время доступны следующие версии платформы .NET Framework.  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 2.0 (входит в состав Visual Studio 2005)  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.0 (входит в состав [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)])  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 3.5 (входит в состав [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)])  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4 (входит в состав Visual Studio 2010)  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5 (входит в состав [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)])  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.5.1 (входит в состав [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)])  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]4.5.2  
  
-   [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 4.6 (входит в состав [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)])  
  
 Версии платформы .NET Framework отличаются друг от друга в списке сборок, доступном для использования в справочных целях. Например, приложения WPF можно создавать, только если проект предназначен для платформы .NET Framework версии 3.0 или выше.  
  
 Целевая версия .NET Framework указывается в свойстве `TargetFrameworkVersion` в файле проекта. Целевую версию .NET Framework для проекта можно изменить с помощью страниц свойств проекта в интегрированной среде разработки Visual Studio. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md). Доступными значениями для `TargetFrameworkVersion` являются `v2.0`, `v3.0`, `v3.5`, `v4.0`, `v4.5`, `v4.5.1`, `v4.5.2` и `v4.6`.  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
```  
  
 *Целевой профиль* — это подмножество целевой платформы. Например, профиль клиента .NET Framework 4 не содержит ссылок на сборки MSBuild.  
  
 Целевой профиль указывается в свойстве `TargetFrameworkProfile` в файле проекта. Целевой профиль можно изменить с помощью элемента управления целевой платформы на страницах свойств проекта в интегрированной среде разработки. Дополнительные сведения см. в [практическом руководстве по настройке конкретной версии .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
```  
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>  
<TargetFrameworkProfile>Client</TargetFrameworkProfile>  
```  
  
## <a name="target-platform"></a>Целевая платформа  
 *Платформа* — это сочетание оборудования и программного обеспечения, которое определяет конкретную среду выполнения. Например, примененная к объекту директива  
  
-   `x86` обозначает 32-разрядную операционную систему Windows, работающую с процессором Intel 80x86 или эквивалентным.  
  
-   `Xbox` обозначает платформу Microsoft Xbox 360.  
  
 *Целевая платформа* — это конкретная платформа, для выполнения на которой создан проект. Целевая платформа указывается в свойстве сборки `Platform` в файле проекта. Целевую платформу можно изменить с помощью страниц свойств проекта или **диспетчера конфигураций** в интегрированной среде разработки.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
</PropertyGroup>  
  
```  
  
 *Целевая конфигурация* — это подмножество целевой платформы. Например, конфигурация `x86``Debug` не поддерживает большинство видов оптимизации кода. Целевая конфигурация указывается в свойстве сборки `Configuration` в файле проекта. Целевую конфигурацию можно изменить с помощью страниц свойств проекта или **диспетчера конфигураций**.  
  
```  
<PropertyGroup>  
   <Platform>x86</Platform>  
   <Configuration>Debug</Configuration>  
<PropertyGroup>  
  
```  
  
## <a name="see-also"></a>См. также  
 [Настройка для различных версий](../msbuild/msbuild-multitargeting-overview.md)


