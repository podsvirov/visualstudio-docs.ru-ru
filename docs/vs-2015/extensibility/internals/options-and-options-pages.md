---
title: Страницы параметров и параметров | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], managed package framework support
- managed package framework, Tools Options pages support
- support, Tools Options pages
- Tools Options pages [Visual Studio SDK], layouts
- Tools Options pages [Visual Studio SDK], attributes
ms.assetid: e6c0e636-5ec3-450e-b395-fc4bb9d75918
caps.latest.revision: 35
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4512867f636e2362aa28d52c5af28bf8eb9697f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851152"
---
# <a name="options-and-options-pages"></a>Параметры и страницы параметров
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При выборе пункта **Параметры** в меню **Сервис** открывается диалоговое окно **Параметры** . Параметры в этом диалоговом окне в совокупности называются страницами параметров. Элемент управления "дерево" в области навигации включает категории "Параметры", и каждая категория содержит страницы параметров. При выборе страницы ее параметры отображаются на правой панели. Эти страницы позволяют изменить значения параметров, определяющих состояние VSPackage.  
  
## <a name="support-for-options-pages"></a>Поддержка страниц параметров  
 <xref:Microsoft.VisualStudio.Shell.Package>Класс обеспечивает поддержку для создания параметров страницы и категории параметров. <xref:Microsoft.VisualStudio.Shell.DialogPage>Класс реализует страницу параметров.  
  
 Реализация по умолчанию <xref:Microsoft.VisualStudio.Shell.DialogPage> предлагает своим открытым свойствам пользователя в универсальной сетке свойств. Это поведение можно настроить, переопределив различные методы на странице, чтобы создать страницу настраиваемых параметров, имеющую собственный пользовательский интерфейс. Дополнительные сведения см. в разделе [Создание страницы параметров](../../extensibility/creating-an-options-page.md).  
  
 <xref:Microsoft.VisualStudio.Shell.DialogPage>Класс реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager> , который обеспечивает сохраняемость для страниц параметров, а также для параметров пользователя. Реализации по умолчанию <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToStorage%2A> методов и сохраняют изменения свойств в пользовательском разделе реестра, если это свойство можно преобразовать в строку и из нее.  
  
## <a name="options-page-registry-path"></a>Путь к реестру страницы параметров  
 По умолчанию путь реестра для свойств, управляемых страницей параметров, определяется сочетанием <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , словом DialogPage и именем типа для класса страницы Options. Например, класс страницы Options можно определить следующим образом.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#1)]
 [!code-vb[VSSDKSupportForOptionsPages#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#1)]  
  
 Если <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp, то пары имен и значений свойств являются подразделами HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp\dialogpage\company.OptionsPage.optionspagegeneral.  
  
 Путь реестра страницы параметров определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , слова, тулсоптионспажес, а также категории и имени страницы параметров. Например, если на странице «настраиваемые параметры» есть страница «Категория», страницы «Мои параметры» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp, то на странице «Параметры» будет раздел реестра HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio\8.0exp\toolsoptionspages\my пажес\кустом.  
  
## <a name="toolsoptions-page-attributes-and-layout"></a>Атрибуты и макет страницы "Сервис/Параметры"  
 <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Атрибут определяет группировку страниц настраиваемых параметров по категориям в дереве переходов диалогового окна " **Параметры** ". <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>Атрибут связывает страницу параметров с пакетом VSPackage, предоставляющим интерфейс. Рассмотрим следующий фрагмент кода:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#2)]
 [!code-vb[VSSDKSupportForOptionsPages#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#2)]  
  
 Это объявляет, что MyPackage предоставляет две страницы параметров: Оптионспажеженерал и Оптионспажекустом. В диалоговом окне **Параметры** обе страницы параметров отображаются в категории **Мои страницы** параметров как **Общие** и **Настраиваемые**соответственно.  
  
## <a name="option-attributes-and-layout"></a>Атрибуты и макет параметров  
 Пользовательский интерфейс, предоставляемый страницей, определяет внешний вид параметров на странице настраиваемых параметров. Макет, метки и описание параметров на странице универсальные параметры определяются следующими атрибутами.  
  
- <xref:System.ComponentModel.CategoryAttribute> Определяет категорию параметра.  
  
- <xref:System.ComponentModel.DisplayNameAttribute> Определяет отображаемое имя параметра.  
  
- <xref:System.ComponentModel.DescriptionAttribute> Определяет описание параметра.  
  
  > [!NOTE]
  > Эквивалентные атрибуты, Сркатегори, Локдисплайнаме и Срдескриптион, используют строковые ресурсы для локализации и определяются в [примере управляемого проекта](https://msdn.com/vsx).  
  
  Рассмотрим следующий фрагмент кода:  
  
  [!code-csharp[VSSDKSupportForOptionsPages#3](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/optionspagecustom.cs#3)]
  [!code-vb[VSSDKSupportForOptionsPages#3](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/optionspagegeneral.vb#3)]  
  
  Параметр Оптионинтежер отображается на странице Параметры в виде **целочисленного параметра** в категории **Мои параметры** . Если этот параметр выбран, в поле Описание отображается **параметр Description (мое целое число**).  
  
## <a name="accessing-options-pages-from-another-vspackage"></a>Доступ к страницам параметров из другого пакета VSPackage  
 Пакет VSPackage, на котором размещается страница параметров и управляет им, может быть программно доступен из другого пакета VSPackage с помощью модели автоматизации. Например, в следующем коде пакет VSPackage регистрируется как размещенная страница параметров.  
  
 [!code-csharp[VSSDKSupportForOptionsPages#4](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#4)]
 [!code-vb[VSSDKSupportForOptionsPages#4](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#4)]  
  
 Следующий фрагмент кода получает значение Оптионинтежер из Мйоптионпаже:  
  
 [!code-csharp[VSSDKSupportForOptionsPages#5](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportforoptionspages/cs/vssdksupportforoptionspagespackage.cs#5)]
 [!code-vb[VSSDKSupportForOptionsPages#5](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportforoptionspages/vb/vssdksupportforoptionspagespackage.vb#5)]  
  
 Когда <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> атрибут регистрирует страницу параметров, эта страница регистрируется в ключе AutomationProperties, если `SupportsAutomation` аргумент атрибута имеет значение `true` . Автоматизация проверяет эту запись реестра, чтобы найти соответствующий пакет VSPackage, а затем автоматизирует доступ к свойству на странице "размещенные параметры", в данном случае на странице "Сетка".  
  
 Путь реестра для свойства службы автоматизации определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> , слова, AutomationProperties, а также категории и имени страницы параметров. Например, если на странице «Параметры» имеется категория «моя Категория», имя страницы «Моя сетка» и <xref:Microsoft.VisualStudio.Shell.Package.ApplicationRegistryRoot%2A> HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0exp, то свойство автоматизации содержит раздел реестра HKEY_LOCAL_MACHINE \Software\microsoft\visualstudio\8.0exp\automationproperties\my Категори\ми Page (сетка).  
  
> [!NOTE]
> Каноническое имя, страница Category.My Grid, является значением подраздела имени этого раздела.
