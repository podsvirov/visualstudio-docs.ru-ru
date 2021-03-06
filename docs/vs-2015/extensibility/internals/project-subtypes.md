---
title: Подтипы проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], subtypes
- project subtypes [Visual Studio SDK]
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ad1e105d43c40782b13d8799b20626e57363c2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842393"
---
# <a name="project-subtypes"></a>Подтипы проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Подтипы проектов позволяют настраивать или изменять поведение систем проектов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Настройки включают сохранение дополнительных данных в файле проекта, добавление или фильтрацию элементов в диалоговом окне **Добавление нового элемента** , управление отладкой и развертыванием сборок, а также расширение диалогового окна « **страницы свойств** проекта». Пакеты VSPackage реализуют подтипы проектов с помощью агрегирования COM.  
  
> [!NOTE]
> Система проектов Visual C++ не поддерживает подтипы проектов. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] сам по себе использует подтипы проектов для реализации SQL Server и проектов смарт-устройств.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Разработка подтипов проекта](../../extensibility/internals/project-subtypes-design.md)  
 Описывает концепцию подтипов проектов.  
  
 [Инициализация последовательности подтипов проекта](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 Описывает последовательность инициализации подтипов программного проекта в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среде.  
  
 [Свойства и методы, расширенные подтипами проектов](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 Содержит подробное описание функций и методов, которые чаще всего расширяются с помощью подтипов проекта.  
  
 [Сохранение данных в файле проекта MSBuild](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 Описывает сохранение данных в файле проекта и использование <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> для сохранения данных в файле проекта через уровни статистической обработки подтипа проекта.  
  
 [Пользовательский интерфейс свойств проекта](../../extensibility/internals/project-property-user-interface.md)  
 Описывает, как подтипы проекта могут изменять диалоговое окно **страницы свойств** проекта.  
  
 [Расширение модели объекта базового проекта](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 Содержит сведения о том, как подтипы проектов могут использовать расширители автоматизации для расширения модели объектов автоматизации.  
  
 [Добавление элементов в диалоговое окно "Добавить новый элемент"](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 Описание процесса добавления элементов в диалоговое окно **Добавление нового элемента** .  
  
 [Сохранение данных в файлах проектов](../../extensibility/saving-data-in-project-files.md)  
 Объясняется, как подтип проекта может сохранять и извлекать данные конкретного типа в файле проекта с помощью платформы Managed Package Framework (MPF).  
  
 [Обработка специализированного развертывания](../../extensibility/internals/handling-specialized-deployment.md)  
 Объясняет, как подтипы проекта могут предоставлять специализированное поведение развертывания путем реализации <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> интерфейса.  
  
 [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)  
 Описывает добавление и удаление страниц свойств в конструкторе проектов.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Содержит ссылки на разделы с подробными сведениями о [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проектах.
