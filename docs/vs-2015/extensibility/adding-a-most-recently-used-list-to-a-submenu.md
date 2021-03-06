---
title: Добавление списка недавно использовавшихся в подменю | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- MRU lists
- menus, creating MRU list
- most recently used
ms.assetid: 27d4bbcf-99b1-498f-8b66-40002e3db0f8
caps.latest.revision: 47
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caccf8923a8614ceedb7198e218ca2bb14bb7ec0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842597"
---
# <a name="adding-a-most-recently-used-list-to-a-submenu"></a>Добавление недавно используемого списка в подменю
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это пошаговое руководство посвящено созданию демонстраций при [добавлении подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md)и показывает, как добавить динамический список в подменю. Динамический список образует базу для создания списка недавно использованных (MRU) списков.  
  
 Динамический список меню начинается с заполнителя в меню. При каждом отображении меню в интегрированной среде разработки (IDE) Visual Studio запрашивается пакет VSPackage для всех команд, которые должны отображаться в заполнителе. Динамический список может находиться в любом месте меню. Однако динамические списки обычно хранятся и отображаются сами по себе в подменю или в нижней части меню. Используя эти конструктивные шаблоны, вы включаете динамический список команд для расширения и контракта, не влияя на расположение других команд в меню. В этом пошаговом руководстве список динамического MRU отображается в нижней части существующего подменю, отделенного от остальной части подменю на строку.  
  
 Технически динамический список можно также применить к панели инструментов. Однако мы не рекомендуем использовать эту возможность, так как панель инструментов должна остаться неизменной, если только пользователь не выберет определенные действия для ее изменения.  
  
 В этом пошаговом руководстве создается список MRU с четырьмя элементами, которые изменяют свой порядок при каждом выборе одного из них (выбранный элемент перемещается в начало списка).  
  
 Дополнительные сведения о меню и файлах vsct см. в разделе [команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-an-extension"></a>Создание расширения  
  
- Выполните процедуры, описанные в [пункте Добавление подменю в меню](../extensibility/adding-a-submenu-to-a-menu.md) , чтобы создать подменю, которое изменяется в следующих процедурах.  
  
  Процедуры в этом пошаговом руководстве предполагают, что имя VSPackage — это `TopLevelMenu` имя, которое используется при [добавлении меню в строку меню Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md).  
  
## <a name="creating-a-dynamic-item-list-command"></a>Создание команды динамического списка элементов  
  
1. Откройте Тесткоммандпаккаже. vsct.  
  
2. В `Symbols` разделе в `GuidSymbol` узле с именем гуидтесткоммандпаккажекмдсет добавьте символ для `MRUListGroup` группы и `cmdidMRUList` команды, как показано ниже.  
  
    ```csharp  
    <IDSymbol name="MRUListGroup" value="0x1200"/>  
    <IDSymbol name="cmdidMRUList" value="0x0200"/>  
    ```  
  
3. В `Groups` разделе добавьте объявленную группу после существующих записей группы.  
  
    ```cpp  
    <Group guid="guidTestCommandPackageCmdSet" id="MRUListGroup"   
           priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
  
    ```  
  
4. В `Buttons` разделе добавьте узел для представления вновь объявленной команды после существующих записей кнопки.  
  
    ```csharp  
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidMRUList"  
        type="Button" priority="0x0100">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MRUListGroup" />  
        <CommandFlag>DynamicItemStart</CommandFlag>  
        <Strings>  
            <CommandName>cmdidMRUList</CommandName>  
            <ButtonText>MRU Placeholder</ButtonText>  
                </Strings>  
    </Button>  
    ```  
  
     `DynamicItemStart`Флаг позволяет динамически создавать команду.  
  
5. Постройте проект и начните отладку, чтобы проверить отображение новой команды.  
  
     В меню **тестмену** щелкните **подменю**создать, чтобы отобразить новую команду, **заполнитель MRU**. После того как в следующей процедуре будет реализован динамический список MRU-команд, эта метка команды будет заменена этим списком при каждом открытии этого подменю.  
  
## <a name="filling-the-mru-list"></a>Заполнение списка MRU  
  
1. В TestCommandPackageGuids.cs добавьте следующие строки после существующих идентификаторов команд в `TestCommandPackageGuids` определении класса.  
  
    ```csharp  
    public const string guidTestCommandPackageCmdSet = "00000000-0000-0000-0000-00000000"; // get the GUID from the .vsct file  
    public const uint cmdidMRUList = 0x200;  
    ```  
  
2. В TestCommand.cs добавьте следующий оператор using.  
  
    ```csharp  
    using System.Collections;  
    ```  
  
3. Добавьте следующий код в конструктор Тесткомманд после последнего вызова AddCommand. `InitMRUMenu`Будет определен позже  
  
    ```csharp  
    this.InitMRUMenu(commandService);  
    ```  
  
4. Добавьте следующий код в класс Тесткомманд. Этот код инициализирует список строк, представляющих элементы, которые должны отображаться в списке MRU.  
  
    ```csharp  
    private int numMRUItems = 4;  
    private int baseMRUID = (int)TestCommandPackageGuids.cmdidMRUList;  
    private ArrayList mruList;  
  
    private void InitializeMRUList()  
    {  
        if (null == this.mruList)  
        {  
            this.mruList = new ArrayList();  
            if (null != this.mruList)  
            {  
                for (int i = 0; i < this.numMRUItems; i++)  
                {  
                    this.mruList.Add(string.Format(CultureInfo.CurrentCulture,  
                        "Item {0}", i + 1));  
                }  
            }  
        }  
    }  
    ```  
  
5. После `InitializeMRUList` метода добавьте `InitMRUMenu` метод. При этом инициализируются команды меню списка MRU.  
  
    ```csharp  
    private void InitMRUMenu(OleMenuCommandService mcs)  
    {  
        InitializeMRUList();  
        for (int i = 0; i < this.numMRUItems; i++)  
        {  
            var cmdID = new CommandID(  
                new Guid(TestCommandPackageGuids.guidTestCommandPackageCmdSet), this.baseMRUID + i);  
            var mc = new OleMenuCommand(  
                new EventHandler(OnMRUExec), cmdID);  
            mc.BeforeQueryStatus += new EventHandler(OnMRUQueryStatus);  
            mcs.AddCommand(mc);  
        }  
    }  
    ```  
  
     Для каждого возможного элемента в списке MRU необходимо создать объект команды меню. Интегрированная среда разработки вызывает `OnMRUQueryStatus` метод для каждого элемента в списке MRU, пока больше нет элементов. В управляемом коде единственным способом, которым интегрированная среда разработки знает, что больше нет элементов, — сначала создать все возможные элементы. При необходимости можно пометить дополнительные элементы как невидимые с помощью `mc.Visible = false;` после создания команды меню. Эти элементы затем можно сделать видимыми позже с помощью `mc.Visible = true;` метода в `OnMRUQueryStatus` методе.  
  
6. После `InitMRUMenu` метода добавьте следующий `OnMRUQueryStatus` метод. Это обработчик, который задает текст для каждого MRU-элемента.  
  
    ```csharp  
    private void OnMRUQueryStatus(object sender, EventArgs e)  
    {  
        OleMenuCommand menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                menuCommand.Text = this.mruList[MRUItemIndex] as string;  
            }  
        }  
    }  
    ```  
  
7. После `OnMRUQueryStatus` метода добавьте следующий `OnMRUExec` метод. Это обработчик для выбора элемента MRU. Этот метод перемещает выбранный элемент в верхнюю часть списка, а затем отображает выбранный элемент в окне сообщения.  
  
    ```csharp  
    private void OnMRUExec(object sender, EventArgs e)  
    {  
        var menuCommand = sender as OleMenuCommand;  
        if (null != menuCommand)  
        {  
            int MRUItemIndex = menuCommand.CommandID.ID - this.baseMRUID;  
            if (MRUItemIndex >= 0 && MRUItemIndex < this.mruList.Count)  
            {  
                string selection = this.mruList[MRUItemIndex] as string;  
                for (int i = MRUItemIndex; i > 0; i--)  
                {  
                    this.mruList[i] = this.mruList[i - 1];  
                }  
                this.mruList[0] = selection;  
                System.Windows.Forms.MessageBox.Show(  
                    string.Format(CultureInfo.CurrentCulture,  
                                  "Selected {0}", selection));  
            }  
        }  
    }  
  
    ```  
  
## <a name="testing-the-mru-list"></a>Тестирование списка MRU  
  
#### <a name="to-test-the-mru-menu-list"></a>Проверка списка MRU-меню  
  
1. Построение проекта и запуск отладки  
  
2. В меню **тестмену** выберите команду **вызвать тесткомманд**. При этом отобразится окно сообщения, показывающее, что команда была выбрана.  
  
    > [!NOTE]
    > Этот шаг необходим для принудительной загрузки VSPackage и правильного вывода списка MRU. Если пропустить этот шаг, список MRU не отобразится.  
  
3. В меню **тест** выберите пункт **подменю**. Список из четырех элементов отображается в конце подменю под разделителем. Если щелкнуть **элемент 3**, появится окно сообщения с текстом "выбранный элемент 3". (Если список четырех элементов не отображается, убедитесь, что выполнены инструкции, приведенные на предыдущем шаге.)  
  
4. Снова откройте подменю. Обратите внимание, что **элемент 3** теперь находится в верхней части списка, а остальные элементы были помещены на одну позицию вниз. Щелкните **элемент 3** еще раз и обратите внимание, что в окне сообщения по-прежнему отображается "выбранный элемент 3", что означает, что текст правильно переместился в новую позицию вместе с меткой команды.  
  
## <a name="see-also"></a>См. также:  
 [Динамическое добавление элементов меню](../extensibility/dynamically-adding-menu-items.md)
