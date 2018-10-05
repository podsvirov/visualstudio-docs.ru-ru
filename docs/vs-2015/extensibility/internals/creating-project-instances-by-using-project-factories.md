---
title: Создание экземпляров проекта с помощью фабрик проектов | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ae36269de9d9911092bedb87f18f9aff3ca76a2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570007"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Создание экземпляров проекта с помощью фабрик проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [создание экземпляров с помощью проекта фабрик проектов](https://docs.microsoft.com/visualstudio/extensibility/internals/creating-project-instances-by-using-project-factories).  
  
Типы проектов в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] использовать *фабрики проектов* для создания экземпляров объектов проекта. Фабрику проекта похоже на стандартный класс фабрики для создаваемых посредством функции CoCreateInstance COM-объектов. Тем не менее, объекты проекта не создаваемых посредством функции CoCreateInstance: они могут создаваться только с помощью фабрики проектов.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE вызывает фабрики проектов, которые реализованы в пакете VSPackage, когда пользователь загружает существующий проект или создает новый проект в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Новый объект проекта предоставляет интегрированную среду разработки достаточно сведений для заполнения в обозревателе решений. Новый объект проекта также обеспечивает необходимые интерфейсы для поддержки всех соответствующих действий пользовательского интерфейса, инициированные интегрированной среды разработки.  
  
 Вы можете реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> интерфейса в класс в проекте. Как правило он располагается в свой собственный модуль.  
  
 Пример реализации `IVsProjectFactory` интерфейсом, см. в разделе PrjFac.cpp, содержащийся в [базовый проект](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) каталог образцов.  
  
 Проекты, поддерживающие статистически владелец должен сохранять ключ владельца в своем файле проекта. При <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> был вызван над проектом с помощью ключа владельца, принадлежащий проект преобразует его владелец ключа в фабрику проекта, затем вызывает GUID `CreateProject` метод данной фабрикой проекта, чтобы сделать фактическое создание.  
  
## <a name="creating-an-owned-project"></a>Создание собственных проекта  
 Владелец создает принадлежащий проект состоит из двух этапов:  
  
1.  Путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> метод. Это дает возможность создать общий объект проекта зависимости от ввода, контролирующего принадлежащий проект `IUnknown`. Принадлежащий проект передает внутреннего `IUnknown` и сводный объект в проект владельца. Это дает возможность хранить внутреннего принадлежащий проект `IUnknown`.  
  
2.  Путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> метод. Принадлежащий проект делает создать его экземпляр, при вызове этого метода вместо вызова метода `IVsProjectFactory::CreateProject` как если бы в случае с проектами, которые не принадлежат. Входные данные `VSOWNEDPROJECTOBJECT` перечисления обычно является агрегированные принадлежащий проект. Принадлежащий проект можно использовать эту переменную для определения, был ли уже создан свой объект проекта (файл cookie не равно NULL) или должен быть создан (файл cookie равно NULL).  
  
 Типы проектов идентифицируются по проект уникальный идентификатор GUID, аналогичную CLSID создаваемых посредством функции CoCreateInstance COM-объекта. Как правило дескрипторы фабрики один проект, создание экземпляров единый тип проекта, несмотря на то, что можно иметь один проект фабрики обработки более чем один идентификатор GUID типа проекта.  
  
 Типы проектов связаны с расширением имени определенного файла. Когда пользователь пытается открыть существующий файл проекта или пытается создать новый проект путем клонирования шаблона, интегрированной среды разработки использует расширение файла для определения соответствующего GUID проекта.  
  
 Как только среда интегрированной разработки определяет, необходимо создать новый проект или откройте существующий проект определенного типа, интегрированная среда разработки использует информацию в системном реестре в разделе [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] чтобы узнать, какие VSPackage реализует фабрики требуется проектов. Интегрированная среда разработки загружает этот пакет VSPackage. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> метод VSPackage необходимо зарегистрировать его фабрики проектов в интегрированной среде разработки путем вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> метод.  
  
 Основной способ `IVsProjectFactory` интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> которого должен обрабатывать два сценария: открытие существующего проекта и создание нового проекта. Большинство проектов хранить их состояния проекта в файле проекта. Как правило, новые проекты создаются за счет передается копия файла шаблона `CreateProject` метод и открытия этой копии. Существующие проекты создаются путем напрямую, открыв файл проекта, передаваемый `CreateProject` метод. `CreateProject` Метод может отображать дополнительные возможности пользовательского интерфейса для пользователя при необходимости.  
  
 Проект можно также использовать файлы не и, вместо этого хранения данных о состоянии проекта в механизм хранения, отличные от файловой системы, например базы данных или веб-сервера. В этом случае параметр имени файла, передаваемый `CreateProject` метод не является фактически путь файловой системы, но уникальная строка — URL-адрес — для идентификации данных проекта. Необходимо скопировать файлы шаблонов, которые передаются `CreateProject` для активации последовательности соответствующих конструкции для выполнения.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Контрольный список. Создание типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)
