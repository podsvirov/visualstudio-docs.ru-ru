---
title: Добавление команд Visual Studio на начальную страницу | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a2042ef9a96eed99636ea0a2f5f09d99cd35ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699151"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Добавление команд Visual Studio на начальную страницу
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При создании настраиваемой начальной страницы к ней можно добавить команды Visual Studio. В этом документе рассматриваются различные способы привязки команд Visual Studio к объектам XAML на начальной странице.  
  
 Дополнительные сведения о командах в XAML см. в разделе [Общие сведения о командах](https://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81) .  
  
## <a name="adding-commands-from-the-command-well"></a>Добавление команд с помощью команды  
 Начальная страница, созданная при [создании настраиваемой начальной страницы](../extensibility/creating-a-custom-start-page.md) , добавила <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> пространства имен и, как показано ниже.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Добавьте еще одно пространство имен для Microsoft. VisualStudio. Shell из сборки Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (В проекте может потребоваться добавить ссылку на эту сборку.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Можно использовать `vscom:` псевдоним для привязки команд Visual Studio к элементам управления XAML на странице, присвоив <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> свойству элемента управления значение `vscom:VSCommands.ExecuteCommand` . Затем можно присвоить <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> свойству имя выполняемой команды, как показано в следующем примере.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
> `x:`Псевдоним, который ссылается на схему XAML, требуется в начале всех команд.  
  
 Можно задать `Command` для свойства значение любой команды, доступ к которой можно получить из **командного** окна. Список доступных команд см. в разделе [псевдонимы команд Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Если команда для добавления требует дополнительного параметра, ее можно добавить в значение `CommandParameter` Свойства. Отделяйте параметры от команд с помощью пробелов, как показано в следующем примере.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Вызов расширений из командной строки  
 Команды можно вызывать из зарегистрированных пакетов VSPackage с использованием того же синтаксиса, который используется для вызова других команд Visual Studio. Например, если установленный пакет VSPackage добавляет в меню **вид** команду **Домашняя страница** , можно вызвать эту команду, задав для значение `CommandParameter` `View.HomePage` .  
  
> [!NOTE]
> При вызове команды, связанной с VSPackage, пакет должен быть загружен при вызове команды.  
  
## <a name="adding-commands-from-assemblies"></a>Добавление команд из сборок  
 Чтобы вызвать команду из сборки или получить доступ к коду в VSPackage, не связанном с командой меню, необходимо создать псевдоним для сборки, а затем вызвать псевдоним.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Вызов команды из сборки  
  
1. В решении добавьте ссылку на сборку.  
  
2. В верхней части файла StartPage. XAML добавьте директиву пространства имен для сборки, как показано в следующем примере.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. Вызовите команду, задав `Command` свойство объекта XAML, как показано в следующем примере.  
  
     Кода  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> Необходимо скопировать сборку и вставить ее в.. \\ *Папку установки Visual Studio*\Common7\IDE\PrivateAssemblies\, чтобы убедиться, что она загружена перед вызовом.  
  
## <a name="adding-commands-with-the-dte-object"></a>Добавление команд с помощью объекта DTE  
 Доступ к объекту DTE можно получить с начальной страницы как в разметке, так и в коде.  
  
 В разметке доступ к нему можно получить с помощью синтаксиса [расширения разметки Binding](https://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) для вызова <xref:EnvDTE.DTE> объекта. Этот подход можно использовать для привязки к простым свойствам, таким как те, которые возвращают коллекции, но нельзя выполнить привязку к методам или службам. В следующем примере показан <xref:System.Windows.Controls.TextBlock> элемент управления, привязанный к <xref:EnvDTE._DTE.Name%2A> свойству, и <xref:System.Windows.Controls.ListBox> элемент управления, перечисляющий <xref:EnvDTE.Window.Caption%2A> свойства коллекции, возвращаемой <xref:EnvDTE._DTE.Windows%2A> свойством.  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Пример см. в разделе [Пошаговое руководство. Сохранение параметров пользователя на начальной странице](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>См. также:  
 [Добавление пользовательского элемента на начальную страницу](../extensibility/adding-user-control-to-the-start-page.md)
