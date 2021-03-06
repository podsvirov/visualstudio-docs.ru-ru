---
title: Параметры контекста | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 679bf567d2f44564d31d70b62c8663e665e1ea65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697288"
---
# <a name="context-parameters"></a>Параметры контекста
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среде разработки (IDE) можно добавлять мастера в диалоговые окна **Новый проект**, **Добавить новый элемент**или **Добавить подпроект** . Добавленные мастера можно найти в меню **файл** или щелкнув правой кнопкой мыши проект в **Обозреватель решений**. Интегрированная среда разработки передает параметры контекста в реализацию мастера. Параметры контекста определяют состояние проекта, когда интегрированная среда разработки вызывает мастер.  
  
 Интегрированная среда разработки запускает мастера, устанавливая <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> флаг в вызове метода для проекта в интегрированной среде разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> . Если этот параметр задан, проект должен вызывать `IVsExtensibility::RunWizardFile` выполнение метода с помощью зарегистрированного имени мастера или GUID и других параметров контекста, которые среда IDE передает в нее.  
  
## <a name="context-parameters-for-new-project"></a>Параметры контекста для нового проекта  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера ( <xref:EnvDTE.Constants.vsWizardNewProject> ) или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] реализации для мастера используется идентификатор GUID {0F90E1D0-4999-11D1-b6d1-00A0C90F2744}.|  
|`ProjectName`|Строка, которая является уникальным [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] именем проекта.|  
|`LocalDirectory`|Локальное расположение рабочих файлов проекта.|  
|`InstallationDirectory`|Путь к каталогу для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] установки.|  
|`FExclusive`|Логический флаг, указывающий, что проект должен закрыть открытые решения.|  
|`SolutionName`|Имя файла решения без части каталога или расширения SLN. Имя файла SUO также создается с помощью `SolutionName` . Если этот аргумент не является пустой строкой, мастер использует <xref:EnvDTE._Solution.Create%2A> перед добавлением проекта с <xref:EnvDTE._Solution.AddFromTemplate%2A> . Если это имя является пустой строкой, используйте <xref:EnvDTE._Solution.AddFromTemplate%2A> без вызова <xref:EnvDTE._Solution.Create%2A> .|  
|`Silent`|Логическое значение, указывающее, должен ли мастер выполняться автоматически, как если бы было нажато кнопку **Готово** ( `TRUE` ).|  
  
## <a name="context-parameters-for-add-new-item"></a>Параметры контекста для добавления нового элемента  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера ( <xref:EnvDTE.Constants.vsWizardAddItem> ) или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] реализации для мастера используется идентификатор GUID {0F90E1D1-4999-11D1-b6d1-00A0C90F2744}.|  
|`ProjectName`|Строка, которая является уникальным [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] именем проекта.|  
|`ProjectItems`|Локальное расположение, содержащее рабочие файлы проекта.|  
|`ItemName`|Имя добавляемого элемента. Это имя является либо именем файла по умолчанию, либо именем файла, которое пользователь вводит в диалоговом окне **Добавление элементов** . Имя основано на флагах, заданных в файле VSDir. Имя может иметь значение null.|  
|`InstallationDirectory`|Путь к каталогу для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] установки.|  
|`Silent`|Логическое значение, указывающее, должен ли мастер выполняться автоматически, как если бы было нажато кнопку **Готово** ( `TRUE` ).|  
  
## <a name="context-parameters-for-add-sub-project"></a>Параметры контекста для добавления подпроекта  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`WizardType`|Зарегистрированный тип мастера ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) или GUID, указывающий тип мастера. В [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] реализации для мастера используется идентификатор GUID {0F90E1D2-4999-11D1-b6d1-00A0C90F2744}.|  
|`ProjectName`|Строка, которая является уникальным [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] именем проекта.|  
|`ProjectItems`|Указатель на `ProjectItems` коллекцию, в которой работает мастер. Этот указатель передается мастеру на основе выбора иерархии проекта. Пользователь обычно выбирает папку, в которую следует поместить элемент, а затем вызывает диалоговое окно **Добавление элемента** проекта.|  
|`LocalDirectory`|Локальное расположение рабочих файлов проекта.|  
|`ItemName`|Имя добавляемого элемента. Это имя является либо именем файла по умолчанию, либо именем файла, которое пользователь вводит в диалоговом окне **Добавление элементов** . Имя основано на флагах, заданных в файле VSDir. Имя может иметь значение null.|  
|`InstallationDirectory`|Путь к каталогу для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] установки.|  
|`Silent`|Логическое значение, указывающее, должен ли мастер выполняться автоматически, как если бы было нажато кнопку **Готово** ( `TRUE` ).|  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Пользовательские параметры](../../extensibility/internals/custom-parameters.md)   
 [Мастера](../../extensibility/internals/wizards.md)   
 [Мастер (. VSZ)-файл](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Контекстные параметры для запуска мастеров](https://msdn.microsoft.com/library/051a10f4-9e45-4604-b344-123044f33a24)
