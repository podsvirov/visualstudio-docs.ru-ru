---
title: Добавление подменю в меню | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f458d46395c3a902e62ba5dd4ac7d624c326700c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184887"
---
# <a name="adding-a-submenu-to-a-menu"></a>Добавление подменю в меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это пошаговое руководство посвящено [добавлению меню в строку меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , в котором показано, как добавить подменю в меню **тестмену** .  
  
 Подменю — это дополнительное меню, которое отображается в другом меню. Подменю можно определить с помощью стрелки, следующей за именем. Если щелкнуть имя, Откроется подменю и его команды.  
  
 Это пошаговое руководство создает подменю в меню в строке меню Visual Studio и помещает в подменю новую команду. В этом пошаговом руководстве также реализована новая команда.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Добавление подменю в меню  
  
1. Выполните действия, описанные в разделе [Добавление меню в строку меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) , чтобы создать проект и пункт меню. В этом пошаговом руководстве предполагается, что имя проекта VSIX имеет значение `TopLevelMenu` .  
  
2. Откройте Тесткоммандпаккаже. vsct. В `<Symbols>` разделе добавьте `<IDSymbol>` элемент для подменю, один для группы подменю, а второй для команды — все в `<GuidSymbol>` узле с именем "гуидтоплевелменукмдсет". Это тот же узел, который содержит `<IDSymbol>` элемент для меню верхнего уровня.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3. Добавьте только что созданное подменю в `<Menus>` раздел.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Пара идентификаторов GUID/ID родительского элемента определяет группу меню, созданную при [добавлении меню в строку меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), и является дочерним элементом меню верхнего уровня.  
  
4. Добавьте группу меню, определенную на шаге 2, в `<Groups>` раздел и сделайте его дочерним элементом подменю.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5. Добавьте новый `<Button>` элемент в раздел, `<Buttons>` чтобы определить команду, созданную на шаге 2, в качестве элемента в подменю.  
  
    ```xml  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic2" />  
        <Strings>  
           <CommandName>cmdidTestSubCommand</CommandName>  
           <ButtonText>Test Sub Command</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
6. Постройте решение и запустите отладку. Вы должны увидеть экспериментальный экземпляр.  
  
7. Щелкните **тестмену** , чтобы открыть новое вложенное **меню**. Щелкните **подменю, чтобы открыть подпрограмму** , и просмотрите новую команду **Test подзадач**. Обратите внимание, что при нажатии кнопки **Test подзадач** ничего не происходит.  
  
## <a name="adding-a-command"></a>Добавление команды  
  
1. Откройте TestCommand.cs и добавьте следующий идентификатор команды после существующего идентификатора команды.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2. Добавьте подкоманду. Найдите конструктор команд. Добавьте следующие строки сразу после вызова `AddCommand` метода.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback`Обработчик команд будет определен позже. Теперь конструктор должен выглядеть следующим образом:  
  
    ```csharp  
    private TestCommand(Package package)  
            {  
                if (package == null)  
                {  
                    throw new ArgumentNullException("package");  
                }  
  
                this.package = package;  
  
                OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
                if (commandService != null)  
                {  
                    var menuCommandID = new CommandID(CommandSet, CommandId);  
                    var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);  
                    commandService.AddCommand(menuItem);  
                    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);  
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3. Добавьте Субитемкаллбакк (). Это метод, который вызывается при нажатии новой команды в подменю.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
        Guid clsid = Guid.Empty;  
        int result;  
        uiShell.ShowMessageBox(  
            0,  
            ref clsid,  
            "TestCommand",  
            string.Format(CultureInfo.CurrentCulture,  
            "Inside TestCommand.SubItemCallback()",  
            this.ToString()),  
            string.Empty,  
            0,  
            OLEMSGBUTTON.OLEMSGBUTTON_OK,  
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,  
            OLEMSGICON.OLEMSGICON_INFO,  
            0,  
            out result);  
    }  
    ```  
  
4. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр.  
  
5. В меню **тестмену** щелкните **подменю** , а затем выберите команду **Test подзадач**. Появится окно сообщения, в котором отобразится текст "команда теста внутри Тесткомманд. Субитемкаллбакк ()".  
  
## <a name="see-also"></a>См. также:  
 [Добавление меню в строку меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
