---
title: Обновление проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- upgrading VSPackages
- upgrading applications, strategies
- VSPackages, upgrade support
ms.assetid: e01cb44a-8105-4cf4-8223-dfae65f8597a
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e838cb02aa1a620356f96d9e77f1752797ac409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842468"
---
# <a name="upgrading-projects"></a>Обновление проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Изменения модели проекта с одной версии [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] на следующую могут потребовать обновления проектов и решений, чтобы они могли работать в более новой версии. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)]Предоставляет интерфейсы, которые можно использовать для реализации поддержки обновления в собственных проектах.  
  
## <a name="upgrade-strategies"></a>Стратегии обновления  
 Для поддержки обновления в реализации системы проектов должна быть определена и реализована стратегия обновления. При определении стратегии можно выбрать поддержку параллельного резервного копирования (SxS), резервного копирования или и того и другого.  
  
- Резервное копирование SxS означает, что проект копирует только те файлы, которые требуют обновления на месте, добавляя подходящий суффикс имени файла, например ". old".  
  
- Копирование резервной копии означает, что проект копирует все элементы проекта в указанное пользователем расположение резервной копии. После этого обновляются соответствующие файлы в исходном расположении проекта.  
  
## <a name="how-upgrade-works"></a>Принцип работы обновления  
 Если решение, созданное в более ранней версии [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , открывается в более новой версии, интегрированная среда разработки проверяет файл решения, чтобы определить, нужно ли его обновить. Если требуется обновление, то **Мастер обновления** запускается автоматически, чтобы проанализировать пользователя с помощью процесса обновления.  
  
 Когда решение нуждается в обновлении, оно запрашивает стратегию обновления для каждой фабрики проектов. Стратегия определяет, поддерживает ли фабрика проектов резервное копирование и архивацию SxS. Эти сведения отправляются в **Мастер обновления**, который собирает сведения, необходимые для резервного копирования, и предоставляет пользователю соответствующие параметры.  
  
### <a name="multi-project-solutions"></a>Решения для нескольких проектов  
 Если решение содержит несколько проектов и стратегии обновления различаются, например, если проект C++ поддерживает только резервное копирование SxS и веб-проект, поддерживающий только резервное копирование, фабрики проектов должны согласовать стратегию обновления.  
  
 Решение запрашивает каждую фабрику проектов для <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory> . Затем он вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly%2A> , чтобы узнать, требуется ли обновление глобальных файлов проекта и определить поддерживаемые стратегии обновления. Затем вызывается **Мастер обновления** .  
  
 После завершения работы мастера пользователь <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> вызывается в каждой фабрике проектов для выполнения фактического обновления. Чтобы упростить резервное копирование, методы Ивспрожектупградевиафактори предоставляют <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> службе возможность регистрировать сведения о процессе обновления. Эта служба не может быть кэширована.  
  
 После обновления всех соответствующих глобальных файлов каждая фабрика проектов может выбрать экземпляр проекта. Реализация проекта должна поддерживать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgrade.UpgradeProject%2A>Затем вызывается метод для обновления всех релевантных элементов проекта.  
  
> [!NOTE]
> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A>Метод не предоставляет службу свсупграделогжер. Эту службу можно получить, вызвав <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> .  
  
## <a name="best-practices"></a>Рекомендации  
 Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> службу, чтобы проверить, можно ли изменить файл перед его редактированием, а также сохранить его перед сохранением. Это поможет вашим реализациям резервного копирования и обновления управлять файлами проекта в системе управления версиями, файлами с недостаточными разрешениями и т. д.  
  
 Используйте <xref:Microsoft.VisualStudio.Shell.Interop.SVsUpgradeLogger> службу на всех этапах резервного копирования и обновления, чтобы предоставить сведения об успешном или неуспешном завершении процесса обновления.  
  
 Дополнительные сведения о резервном копировании и обновлении проектов см. в комментариях к IVsProjectUpgrade в vsshell2. idl.  
  
## <a name="see-also"></a>См. также:  
 [Макропроекты](../../extensibility/internals/projects.md)   
 [Обновление пользовательских проектов](../../misc/upgrading-custom-projects.md)   
 [Обновление элементов проекта](../../misc/upgrading-project-items.md)
