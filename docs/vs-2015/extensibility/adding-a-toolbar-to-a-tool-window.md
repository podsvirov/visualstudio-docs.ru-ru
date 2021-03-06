---
title: Добавление панели инструментов в окно инструментов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding toolbars
- toolbars [Visual Studio], adding to tool windows
ms.assetid: 172f64b3-87f8-4292-9c1c-65bffa2b0970
caps.latest.revision: 49
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c5df1ce1721c63b5c5cfc3c5b94929da088660f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184883"
---
# <a name="adding-a-toolbar-to-a-tool-window"></a>Добавление панели инструментов в окно инструментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как добавить панель инструментов в окно инструментов.  
  
 Панель инструментов представляет собой горизонтальную или вертикальную полосу, которая содержит кнопки, привязанные к командам. Длина панели инструментов в окне инструментов всегда совпадает с шириной или высотой окна инструментов в зависимости от того, где закреплена панель инструментов.  
  
 В отличие от панелей инструментов в интегрированной среде разработки, панель инструментов в окне инструментов должна быть закреплена и не может быть перемещена или настроена. Если пакет VSPackage написан в коде уманажед, панель инструментов можно закрепить на любом крае.  
  
 Дополнительные сведения о добавлении панели инструментов см. в разделе [Добавление панели инструментов](../extensibility/adding-a-toolbar.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-toolbar-for-a-tool-window"></a>Создание панели инструментов для окна инструментов  
  
1. Создайте проект VSIX с именем `TWToolbar` , который содержит как команду меню с именем **твтесткомманд** , так и окно инструментов с именем **тесттулвиндов**. Дополнительные сведения см. в статьях [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md) и [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md). Перед добавлением шаблона окна инструментов необходимо добавить шаблон элемента команды.  
  
2. В Твтесткоммандпаккаже. vsct найдите раздел Symbols. В узле GuidSymbol с именем Гуидтвтесткоммандпаккажекмдсет объявите панель инструментов и группу панелей инструментов, как показано ниже.  
  
    ```xml  
    <IDSymbol name="TWToolbar" value="0x1000" />  
    <IDSymbol name="TWToolbarGroup" value="0x1050" />  
    ```  
  
3. В верхней части `Commands` раздела создайте `Menus` раздел. Добавьте `Menu` элемент, чтобы определить панель инструментов.  
  
    ```xml  
    <Menus>  
        <Menu guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" type="ToolWindowToolbar">  
            <CommandFlag>DefaultDocked</CommandFlag>  
            <Strings>  
                <ButtonText>Test Toolbar</ButtonText>  
                <CommandName>Test Toolbar</CommandName>  
            </Strings>  
        </Menu>  
    </Menus>  
    ```  
  
     Панели инструментов не могут быть вложенными, как подменю. Поэтому нет необходимости назначать родительский объект. Кроме того, не нужно задавать приоритет, так как пользователь может перемещать панели инструментов. Как правило, начальное размещение панели инструментов определяется программным способом, но последующие изменения, внесенные пользователем, сохраняются.  
  
4. В разделе группы определите группу, содержащую команды для панели инструментов.  
  
    ```xml  
  
    <Group guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" priority="0x0000">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbar" />  
    </Group>  
    ```  
  
5. В разделе кнопки измените родителя существующего элемента кнопки на группу панелей инструментов, чтобы отображалась панель инструментов.  
  
    ```xml  
    <Button guid="guidTWTestCommandPackageCmdSet" id="TWTestCommandId" priority="0x0100" type="Button">  
        <Parent guid="guidTWTestCommandPackageCmdSet" id="TWToolbarGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>Invoke TWTestCommand</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
     По умолчанию, если на панели инструментов нет команд, она не отображается.  
  
     Так как новая панель инструментов не добавляется в окно инструментов автоматически, панель инструментов необходимо добавить явным образом. Этот метод будет рассмотрен в следующем разделе.  
  
## <a name="adding-the-toolbar-to-the-tool-window"></a>Добавление панели инструментов в окно инструментов  
  
1. В TWTestCommandPackageGuids.cs добавьте следующие строки.  
  
    ```csharp  
    public const string guidTWTestCommandPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const int TWToolbar = 0x1000;  
    ```  
  
2. В TestToolWindow.cs добавьте следующий оператор using.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    ```  
  
3. В конструкторе Тесттулвиндов добавьте следующую строку.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(TWTestCommandPackageGuids.guidTWTestCommandPackageCmdSet), TWTestCommandPackageGuids.TWToolbar);  
    ```  
  
## <a name="testing-the-toolbar-in-the-tool-window"></a>Тестирование панели инструментов в окне инструментов  
  
1. Выполните сборку решения и запустите отладку. Должен отобразиться экспериментальный экземпляр Visual Studio.  
  
2. В меню **вид/другие окна** выберите пункт окна **тестов** , чтобы открыть окно инструментов.  
  
     Вы увидите панель инструментов (она выглядит как значок по умолчанию) в верхнем левом углу окна инструментов под заголовком.  
  
3. На панели инструментов щелкните значок, чтобы отобразить сообщение **Твтесткоммандпаккаже внутри твтулбар. твтесткомманд. менуитемкаллбакк ()**.  
  
## <a name="see-also"></a>См. также:  
 [Добавление панели инструментов](../extensibility/adding-a-toolbar.md)
