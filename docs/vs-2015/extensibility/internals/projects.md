---
title: Проекты | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a251af12ccf4be5f0f48f789ac59fedaed3299b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183938"
---
# <a name="projects"></a>Проекты
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В Visual Studio проекты — это контейнеры, используемые разработчиками для организации файлов исходного кода и других ресурсов, которые отображаются в **Обозреватель решений**. Как правило, проекты — это файлы (например, CSPROJ-файл для проекта C#), которые хранят ссылки на файлы исходного кода и ресурсы, такие как растровые файлы. Проекты позволяют упорядочивать, собирать, отлаживать и развертывать исходный код, ссылки на веб-службы и базы данных, а также другие ресурсы. Пакеты VSPackage могут расширять систему проектов Visual Studio тремя основными способами: *типы проектов*, *подтипы проектов*и *пользовательские инструменты*.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 *Типы проектов* добавляют поддержку новых типов проектов, таких как языки программирования. Например, каждый язык, поддерживаемый Visual Studio, имеет собственный тип проекта, а пример интеграции IronPython включает тип проекта для языка IronPython. Необходимо создать тип проекта для языков, отличных от C# или Visual Basic, чтобы настроить построение, отладку, развертывание и отображение элементов в **Обозреватель решений**. Дополнительные сведения см. в разделе [типы проектов](../../extensibility/internals/project-types.md).  
  
 [Подтипы проектов](../../extensibility/internals/project-subtypes.md)  
 *Подтипы проектов* основываются на типах проектов и могут использоваться для настройки способа построения, отладки и развертывания проектов. Visual Studio использует подтипы проектов для проектов смарт-устройств; они настраивают развертывание путем копирования недавно созданной программы с компьютера разработчика на целевое устройство. Типы проектов C# и Visual Basic можно использовать в качестве базиса для подтипов проектов. Типы проектов C++ не могут. Собственные типы проектов также можно использовать в качестве базиса для подтипов проектов. Дополнительные сведения см. в разделе [Project подтипы](../../extensibility/internals/project-subtypes.md).  
  
 [Веб-проекты](../../extensibility/internals/web-projects.md)  
 Описывает веб-проект, который, в свою очередь, создает веб-приложения.  
  
 Создание [новых проектов.](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) в рамках этой части одна и [Новая версия проекта: внутри, часть 2](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Объясняет, что происходит при создании нового проекта.  
  
 [Примеры VSSDK](../../misc/vssdk-samples.md)  
 Описывает примеры в VSSDK, которые работают с проектами и решениями.  
  
## <a name="related-sections"></a>См. также  
 [Компоненты пакета SDK для Visual Studio](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Объясните различные аспекты расширения среды Visual Studio.
