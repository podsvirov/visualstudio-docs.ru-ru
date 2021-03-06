---
title: Ribbon XML
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e9ce2388dbf61ef3af524f0debc776891dca004f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842553"
---
# <a name="ribbon-xml"></a>Ribbon XML
  Элемент Лента (XML) позволяет настраивать ленту с помощью XML. Используйте элемент Лента (XML), если требуется настроить ленту способом, который не поддерживается элементом Лента (визуальный конструктор). Сравнение того, что можно делать с каждым элементом, см. в разделе [лента Обзор ленты](../vsto/Ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

## <a name="add-a-ribbon-xml-item-to-a-project"></a>Добавление элемента ленты (XML) в проект
 Элемент **Лента (XML)** можно добавить в любой проект Office из диалогового окна **Добавить новый элемент** . Visual Studio автоматически добавляет в проект следующие файлы.

- XML-файл ленты. Этот файл определяет пользовательский интерфейс ленты. Данный файл можно использовать для добавления элементов пользовательского интерфейса — вкладок, групп и элементов управления. Дополнительные сведения см. Далее в разделе [Справочник по XML-файлу ленты](#RibbonDescriptorFile) .

- Файл кода ленты. Этот файл содержит *класс ленты*. Класс имеет имя, указанное для элемента **Лента (XML)** в диалоговом окне **Добавить новый элемент** . Microsoft Office приложения используют экземпляр этого класса для загрузки настраиваемой ленты. Дополнительные сведения см. в разделе [ссылка на класс ленты](#RibbonExtensionClass) далее в этой статье.

  По умолчанию эти файлы добавляют пользовательскую группу к вкладке **надстройки** на ленте.

## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Отображение настраиваемой ленты в приложении Microsoft Office
 После добавления элемента **ленты (XML)** в проект необходимо добавить код в класс **ThisAddIn**, **ThisWorkbook**или **ThisDocument** , который переопределяет `CreateRibbonExtensibilityObject` метод и возвращает класс XML ленты в приложение Office.

 В следующем примере кода переопределяется метод `CreateRibbonExtensibilityObject` и возвращается XML-класс ленты с именем MyRibbon.

 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

## <a name="define-the-behavior-of-the-custom-ribbon"></a>Определение поведения настраиваемой ленты
 Вы можете реагировать на действия пользователя, такие как нажатие кнопки на ленте, путем создания *методов обратного вызова*. Методы обратного вызова похожи на события в элементах управления Windows Forms, но они идентифицируются атрибутом в XML-коде элемента пользовательского интерфейса. Вы записываете методы в классе ленты, а элемент управления вызывает метод, который имеет то же имя, что и значение атрибута. Например, можно создать метод обратного вызова, который вызывается, когда пользователь нажимает кнопку на ленте. Для создания метода обратного вызова необходимо выполнить два действия.

- Назначьте атрибут элементу управления в XML-файле ленты, который идентифицирует метод обратного вызова в коде.

- Определите метод обратного вызова в классе ленты.

> [!NOTE]
> Для Outlook необходимо будет выполнить еще одно действие. Дополнительные сведения см. [в разделе Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md).

 Пошаговое руководство, в котором показано, как автоматизировать приложение на ленте, см. в разделе [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md).

### <a name="assign-callback-methods-to-controls"></a>Назначение методов обратного вызова элементам управления
 Для назначения метода обратного вызова элементу управления в XML-файле ленты добавьте атрибут, который указывает тип метода обратного вызова и имя данного метода. Например, следующий элемент определяет выключатель, который имеет метод обратного вызова **onAction** с именем `OnToggleButton1`.

```xml
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />
```

 **onAction** вызывается, когда пользователь выполняет основную задачу, связанную с конкретным элементом управления. Например, метод обратного вызова **onAction** выключателя вызывается, когда пользователь нажимает кнопку.

 Метод, указываемый в атрибуте, может иметь любое имя. Тем не менее данное имя должно соответствовать имени метода, который определяется в файле кода ленты.

 Элементам управления ленты можно назначать методы обратного вызова различного типа. Полный список методов обратного вызова, доступных для каждого элемента управления, см. в технической статье [Настройка пользовательского интерфейса ленты Office (2007) для разработчиков (часть 3 из 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)).

### <a name="define-callback-methods"></a><a name="CallBackMethods"></a> Определение методов обратного вызова
 Определите методы обратного вызова в классе ленты в файле кода ленты. Метод обратного вызова должен удовлетворять ряду требований.

- Он должен быть объявлен как открытый.

- Его имя должно соответствовать имени метода обратного вызова, которое назначено элементу управления в XML-файле ленты.

- Его сигнатура должна соответствовать сигнатуре метода обратного вызова, доступного для связанного элемента управления ленты.

  Полный список сигнатур методов обратного вызова для элементов управления ленты см. в технической статье [Настройка пользовательского интерфейса ленты Office (2007) для разработчиков (часть 3 из 3)](/previous-versions/office/developer/office-2007/aa722523(v=office.12)). Visual Studio не поддерживает IntelliSense для методов обратного вызова, которые создаются в файле кода ленты. Если создать метод обратного вызова, который не соответствует допустимой сигнатуре, код будет скомпилирован, но, когда пользователь щелкнет элемент управления, ничего не произойдет.

  Все методы обратного вызова имеют параметр <xref:Microsoft.Office.Core.IRibbonControl> , который представляет элемент управления, вызвавший метод. Этот параметр позволяет повторно использовать один и тот же метод обратного вызова для нескольких элементов управления. В следующем примере кода демонстрируется метод обратного вызова **onAction** , который выполняет различные задачи в зависимости от того, какой элемент управления щелкает пользователь.

  [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
  [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]

## <a name="ribbon-xml-file-reference"></a><a name="RibbonDescriptorFile"></a> Справочник по XML-файлу ленты
 Вы можете определить пользовательскую ленту, добавив элементы и атрибуты в XML-файл ленты. По умолчанию XML-файл ленты содержит следующий XML-код.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">
  <ribbon>
    <tabs>
      <tab idMso="TabAddIns">
        <group id="MyGroup"
               label="My Group">
        </group>
      </tab>
    </tabs>
  </ribbon>
</customUI>
```

 В следующей таблице указаны элементы по умолчанию в XML-файле ленты.

|Элемент|Description|
|-------------|-----------------|
|**customUI**|Представляет пользовательскую ленту в проекте надстройки VSTO.|
|**ленте**|Представляет ленту.|
|**соответствующую**|Представляет набор вкладок на ленте.|
|**вкладке**|Представляет одну вкладку на ленте.|
|**group**|Представляет группу элементов управления на вкладке ленты.|

 Эти элементы имеют атрибуты, определяющие внешний вид и поведение настраиваемой ленты. В следующей таблице указаны атрибуты по умолчанию в XML-файле ленты.

|Атрибут|Родительский элемент|Описание|
|---------------|--------------------|-----------------|
|**onLoad**|**customUI**|Определяет метод, который вызывается, когда приложение загружает ленту.|
|**idMso**|**вкладке**|Определяет встроенную вкладку, отображаемую на ленте.|
|**id**|**group**|Идентифицирует группу.|
|**label**|**group**|Указывает текст, отображаемый в группе.|

 Элементы и атрибуты по умолчанию в XML-файле ленты представляют собой небольшое подмножество доступных элементов и атрибутов. Полный список доступных элементов и атрибутов см. в технической статье [Настройка пользовательского интерфейса ленты Office (2007) для разработчиков (часть 2 из 3)](/previous-versions/office/developer/office-2007/aa338199(v=office.12)).

## <a name="ribbon-class-reference"></a><a name="RibbonExtensionClass"></a> Справочник по классам ленты
 Visual Studio создает класс ленты в файле кода ленты. Добавьте методы обратного вызова для элементов управления на ленте в этот класс. Этот класс реализует интерфейс <xref:Microsoft.Office.Core.IRibbonExtensibility>.

 В следующей таблице указаны методы по умолчанию в этом классе.

|Метод|Description|
|------------|-----------------|
|`GetCustomUI`|Возвращает содержимое XML-файла ленты. Microsoft Office приложения вызывают этот метод для получения XML-строки, определяющей пользовательский интерфейс настраиваемой ленты. Этот метод реализует метод <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> . **Примечание.** `GetCustomUI` должен быть реализован только для возврата содержимого XML-файла ленты; его не следует использовать для инициализации надстройки VSTO.   В частности, не пытайтесь отображать диалоговые или прочие окна в своей реализации `GetCustomUI` . В противном случае пользовательская лента может работать неправильно. Если необходимо запускать код, который инициализирует надстройку VSTO, добавьте этот код в обработчик событий `ThisAddIn_Startup` .|
|`OnLoad`|Назначает параметр <xref:Microsoft.Office.Core.IRibbonControl> полю `Ribbon` . Microsoft Office приложения вызывают этот метод при загрузке пользовательской ленты. Это поле можно использовать для динамического обновления настраиваемой ленты. Дополнительные сведения см. в технической статье [Настройка пользовательского интерфейса ленты Office (2007) для разработчиков (часть 1 из 3)](/previous-versions/office/developer/office-2007/aa338202(v=office.12)).|
|`GetResourceText`|Вызывается методом `GetCustomUI` для получения содержимого XML-файла ленты.|

## <a name="see-also"></a>См. также
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
