---
title: Общие сведения о конфигурациях сборок | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a7e7c184fd150c46b3a8be0ec583d4223487ad32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672771"
---
# <a name="understanding-build-configurations"></a>Общие сведения о конфигурациях построения
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете сохранять разные конфигурации решения и свойства проекта для использования разных типов сборок. Чтобы создать, выбрать, изменить или удалить конфигурацию, можно использовать **Configuration Manager**. Чтобы открыть его, выберите в строке меню **Сборка**, **Configuration Manager** или просто введите **Configuration** в поле **Быстрый запуск**. Можно также использовать список **Конфигурации решения** на панели инструментов **Стандартные**, чтобы выбрать конфигурацию или открыть **Configuration Manager**.

> [!NOTE]
> Если не удается найти параметры конфигурации решения на панели инструментов и не удается получить доступ к **Configuration Manager**, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] можно применить параметры разработки. Дополнительные сведения см. [в разделе руководство. Управление конфигурациями с применением Visual Basic параметров разработчика](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md).

 По умолчанию конфигурации отладки и выпусков включены в проекты, которые создаются с использованием шаблонов [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Конфигурация отладки поддерживает отладку приложения, а конфигурация выпусков выполняет сборку версии приложения, которую можно развернуть. Дополнительные сведения см. в разделе [Практическое руководство. настроить конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md). Можно также создать пользовательские конфигурации решений и проектов. Дополнительные сведения см. [в разделе инструкции. Создание и изменение конфигураций](../ide/how-to-create-and-edit-configurations.md).

## <a name="solution-configurations"></a>Конфигурации решения
 Конфигурация решения указывает, как следует создавать и развертывать проекты в решении. Чтобы изменить конфигурацию решения или определить новую конфигурацию в **Configuration Manager**, в меню **Активная конфигурация решения** щелкните **Изменить** или **Создать**.

 Каждая запись в поле **Контексты проекта** в конфигурации решений представляет проект в решении. Для каждой комбинации**Активная конфигурация решения** и **Активная платформа решения** можно задать способ использования каждого проекта. (Дополнительные сведения о платформах решений см. в разделе [Общие сведения о сборках платформ](../ide/understanding-build-platforms.md).)

> [!NOTE]
> При определении новой конфигурации решения и установке флажка **Создать новые конфигурации проектов**[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] автоматически назначает новую конфигурацию всем проектам. Аналогичным образом, при определении новой платформы решения и установке флажка **Создать новые платформы проектов**[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] автоматически назначает новую платформу всем проектам. Кроме того, если вы добавите проект, предназначенный для новой платформы, Visual Studio добавит эту платформу в список платформ решений и назначит ее всем проектам.
>
> Вы по-прежнему можете изменять параметры для каждого проекта.

 Активная конфигурация решения также предоставляет контекст для IDE. Например, если вы работаете над проектом и конфигурация указывает, что он будет создан для мобильного устройства, на **панели инструментов** отобразятся только элементы, которые можно использовать в проекте мобильного устройства.

## <a name="project-configurations"></a>Конфигурации проекта
 Целевые конфигурация и платформа проекта применяются совместно для указания свойств, используемых при сборке. Проект может иметь разный набор определений свойств для каждой комбинации конфигурации и платформы. Чтобы изменить свойства проекта, можно использовать страницы свойств. (В **Обозреватель решений**откройте контекстное меню проекта и выберите пункт **свойства**.)

 Для каждой конфигурации проекта можно при необходимости определить свойства, зависимые от конфигурации. Например, для определенной сборки можно задать элементы, которые будут включены в проект, а также выходные файлы, которые будут созданы, место их расположения и способ оптимизации.

 Конфигурации проектов могут значительно отличаться. Например, в свойствах одной конфигурации может быть указано, что выходной файл следует оптимизировать так, чтобы он занимал меньше всего места, тогда как в другой конфигурации может быть указано, что исполняемый файл выполняется на максимальной скорости.

 Конфигурации проектов хранятся решением, а не пользователем, чтобы группа могла получить к ним общий доступ.

 Хотя зависимости проекта не зависят от конфигурации, будет выполнена сборка только проектов, указанных в активной конфигурации решения.

## <a name="how-visual-studio-assigns-project-configurations"></a>Назначение конфигураций проектов Visual Studio
 Если вы определяете конфигурацию нового решения и не копируете параметры из существующего, Visual Studio использует следующие критерии для назначения конфигурации проектов по умолчанию. Критерии оцениваются в следующем порядке.

1. Если проект имеет имя конфигурации (* \<configuration name> \<platform name> *), которое точно соответствует имени новой конфигурации решения, эта конфигурация назначается. В именах конфигураций не учитывается регистр.

2. Если проект имеет имя конфигурации, в котором часть имени конфигурации совпадает с новой конфигурацией решения, назначается эта конфигурация (независимо от того, совпадает ли часть имени платформы или нет).

3. Если совпадений все равно нет, назначается первая конфигурация, указанная в проекте.

## <a name="how-visual-studio-assigns-solution-configurations"></a>Назначение конфигураций решений Visual Studio
 При создании конфигурации проекта (в **Configuration Manager** путем выбора пункта **Создать** в раскрывающемся меню столбца **Конфигурация** для этого проекта) и установке флажка **Создать новые конфигурации решений** Visual Studio ищет конфигурацию решения с таким же именем, чтобы создать проект на каждой поддерживаемой платформе. В некоторых случаях Visual Studio переименовывает существующие конфигурации решения или определяет новые.

 Visual Studio использует следующие критерии для назначения конфигураций решения.

- Если конфигурация проекта не указывает платформу или указывает только одну платформу, будет найдена или добавлена конфигурация решения, имя которой совпадает с именем новой конфигурации проекта. Имя по умолчанию для этой конфигурации решения не включает имя платформы. Он принимает форму *\<project configuration name>* .

- Если проект поддерживает несколько платформ, для каждой поддерживаемой платформы будет найдена или добавлена конфигурация решения. Имя каждой конфигурации решения включает имя конфигурации проекта и имя платформы, а также имеет форму * \<project configuration name> \<platform name> *.

## <a name="see-also"></a>См. также:
 [Пошаговое руководство. Создание приложения](../ide/walkthrough-building-an-application.md) [Компиляция и создание](../ide/compiling-and-building-in-visual-studio.md) [решений и проектов](../ide/solutions-and-projects-in-visual-studio.md) [C/C++ сборка справочника](https://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) по [параметрам командной строки](../ide/reference/devenv-command-line-switches.md)
