---
title: Определение пользовательского элемента панели элементов моделирования | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, customizing the toolbox
ms.assetid: a2463606-1100-40ac-97f3-5ba22ca47b7c
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0a038150519ea7a40a52fb1be16ed93045c09eed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851521"
---
# <a name="define-a-custom-modeling-toolbox-item"></a>Определение пользовательского элемента для панели элементов моделирования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Чтобы упростить создание элемента или группы элементов по часто используемому шаблону, можно добавить на панель элементов схем моделирования в Visual Studio новые инструменты. Можно распространить эти элементы панели элементов другим пользователям Visual Studio.

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Пользовательский инструмент создает один или несколько новых элементов в схеме. Например, можно создать пользовательский инструмент, позволяющий создавать следующие элементы:

- Пакет, связанный с профилем .NET, и класс со стереотипом .NET.

- Пара классов, связанная ассоциацией для представления шаблона наблюдателя.

> [!NOTE]
> Этот метод можно использовать для создания инструментов элемента. Таким образом, можно создать инструменты, которые можно перетаскивать из панели элементов на схему. Инструменты соединителя создавать нельзя.

## <a name="defining-a-custom-modeling-tool"></a><a name="DefineTool"></a> Определение пользовательского инструмента моделирования

#### <a name="to-define-a-custom-modeling-tool"></a>Порядок определения пользовательского инструмента моделирования

1. Создайте схему UML, которая содержит элемент или группу элементов.

    - Эти элементы могут иметь отношения между собой и дочерние элементы, например порты, атрибуты, операции или закрепления.

2. Сохраните схему, используя имя, которое хотите присвоить новому инструменту. В меню **файл** используйте команду **Сохранить... Как**.

3. С помощью проводника Windows скопируйте два файла схемы в следующую папку или любую вложенную папку:

     *YourDocuments* **Элементы панели элементов йоурдокументс \висуал студио\арчитектуре тулс\кустом**

    - Создайте эту папку, если она еще не существует. Может потребоваться создать как **инструменты архитектуры** , так и **настраиваемые элементы панели элементов**.

    - Скопируйте оба файла схемы с именем, которое оканчивается на "... **Диаграмма**", а другая с именем, которое оканчивается на"... **схема. макет**»

    - Можно создать столько пользовательских инструментов, сколько необходимо. Используйте одну схему для каждого инструмента.

4. Используемых Создайте **tbxinfo** -файл, как описано в разделе [Определение свойств пользовательских средств](#tbxinfo)и добавление его в тот же каталог. Это позволяет определить значок панели элементов, подсказку и т. п.

    - Для определения нескольких средств можно использовать один **tbxinfo** -файл. Он может ссылаться на файлы схемы, расположенные во вложенных папках.

5. Перезапустите Visual Studio. Дополнительные инструменты будут отображаться на панели элементов для соответствующего типа схемы.

### <a name="what-the-custom-tool-will-replicate"></a>Что именно реплицирует пользовательский инструмент
 Пользовательский инструмент реплицирует большинство функций исходной схемы:

- Имена При создании элемента с панели элементов в конец имени добавляется число, если требуется избежать дублирования имен в рамках одного пространства имен.

- Цвета, размеры и фигуры

- Стереотипы и профили пакета

- Значения свойств, таких как "Является абстрактным"

- Связанные рабочие элементы

- Кратности и другие свойства отношений

- Относительное положение фигур.

  Следующие функции не будут сохраняться в пользовательском инструменте:

- Простые фигуры Это фигуры, не связанные с элементами модели, которые можно рисовать на некоторых типах схем.

- Маршрутизация соединителей Если маршрутизация соединителей осуществляется вручную, она не сохраняется при использовании инструмента. Положения некоторых вложенных фигур, таких как порты, не сохраняется относительно своих владельцев.

## <a name="how-to-define-the-properties-of-custom-tools"></a><a name="tbxinfo"></a> Определение свойств пользовательских средств
 Файл сведений панели элементов (**. tbxinfo**) позволяет указать имя панели элементов, значок, подсказку, вкладку и ключевое слово справки для одного или нескольких настраиваемых инструментов. Присвойте ему любое имя, например **митулс. tbxinfo**.

 Общий вид файла выглядит следующим образом:

```
<?xml version="1.0" encoding="utf-8" ?>
<customToolboxItems xmlns="http://schemas.microsoft.com/visualstudio/[version]/ArchitectureTools/CustomToolboxItems">
  <customToolboxItem fileName="MyObserverTool.classdiagram">
    <displayName>
       <value>Observer Pattern</value>
    </displayName>
    <tabName>
       <value>UML Class Diagram</value>
    </tabName>
    <image><bmp fileName="ObserverPatternIcon.bmp"/></image>
    <f1Keyword>
      <value>ObserverPatternHelp</value>
    </f1Keyword>
    <tooltip>
       <value>Create a pair of classes</value>
    </tooltip>
  </customToolboxItem>
</customToolboxItems>
```

 Значение каждого элемента может быть любым из следующих:

- Как показано в примере, `<bmp fileName="…"/>` для значка панели элементов и `<value>string</value>` для других элементов.

  \- или -

- `<resource fileName="Resources.dll"`

   `baseName="Observer.resources" id="Observer.tabname" />`

   В этом случае вы предоставляете скомпилированную сборку, в которой строковые значения были скомпилированы в качестве ресурсов.

  Добавьте узел `<customToolboxItem>` для каждого элемента панели элементов, который необходимо определить.

  Ниже приведены узлы в файле **tbxinfo** . Для каждого узла имеется значение по умолчанию.

|имя узла|Определяет следующее|
|---------------|-------------|
|displayName|Имя элемента панели элементов.|
|tabName|Вкладка панели элементов, на которой должен отображаться элемент. Можно указать либо имя обычной вкладки для этого типа схемы, либо отдельное имя.|
|Изображение|Расположение файла точечного рисунка (**BMP**), ширина которого должна быть равна 16, и глубина цвета — 24 бита.|
|f1Keyword|Ключевое слово, осуществляющее поиск раздела справки.|
|подсказка|Подсказка для этого инструмента.|

 Можно изменить файл точечного рисунка в Visual Studio и задать его высоту и ширину равными 16 в окне "Свойства".

> [!NOTE]
> Если начать использовать файл TBXINFO после проведения экспериментов по использованию отдельных файлов схем, может оказаться, что панель элементов содержит старые и новые версии элемента панели элементов. Это также может произойти, если имя файла схемы было неправильно указано в файле TBXINFO. Если это происходит, в контекстном меню панели элементов выберите **Сброс панели элементов**. Настраиваемые элементы панели элементов исчезают. Перезапустите Visual Studio, после чего отображаются правильные пользовательские элементы.

## <a name="how-to-distribute-toolbox-items-in-a-visual-studio-extension"></a><a name="Extension"></a> Как распределять элементы панели элементов в расширении Visual Studio
 Вы можете распределить элементы панели элементов другим [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] пользователям, упаковывая их в расширение Visual Studio (VSIX). Команды, профили и другие расширения можно упаковать в один файл VSIX. Дополнительные сведения см. в разделе [развертывание расширений Visual Studio](https://msdn.microsoft.com/library/dd393694(VS.100).aspx).

 Для создания расширения Visual Studio обычно используется шаблон проекта VSIX. Чтобы воспользоваться им, необходимо установить [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-add-a-toolbox-item-to-a-visual-studio-extension"></a>Добавление элемента панели элементов в расширение Visual Studio

1. [Создание и тестирование одного или нескольких пользовательских инструментов](#DefineTool).

2. [Создайте tbxinfo-файл](#tbxinfo) , который ссылается на средства.

3. Создайте проект расширения Visual Studio.

     \- или -

     Определите новый проект расширения Visual Studio.

    1. В меню **Файл** последовательно выберите пункты **Создать**, **Проект**.

    2. В диалоговом окне **Новый проект** в разделе **Установленные шаблоны**выберите **Visual C#**, **расширяемость**, **проект VSIX**.

4. Добавьте в проект определения панели элементов. Включите файл **. tbxinfo** , файлы схем, файлы точечных рисунков и все файлы ресурсов, а также убедитесь, что они включены в VSIX.

    - В обозреватель решений в контекстном меню проекта VSIX выберите **Добавить**, **существующий элемент**. В диалоговом окне задайте **объекты типа: все файлы**. Найдите файлы, выберите их все и нажмите кнопку **Добавить**.

        > [!NOTE]
        > В этом проекте нельзя открыть файлы схемы в редакторе моделей.

5. Задайте следующие свойства всех недавно добавленных файлов. В то же время можно задавать их свойства, выбрав всех их в обозревателе решений. Не следует изменять свойства других файлов в проекте.

     **Копировать в выходной каталог**  =  **Всегда копировать**

     **Действие сборки**  =  **Содержимое**

     **Включить в VSIX**  =  **значение true**

6. Откройте **source.extension.vsixmanifest**. Открывается в редакторе манифеста расширения.

7. В разделе **метаданные**добавьте описание пользовательских инструментов.

     В разделе **активы**выберите **создать** , а затем задайте поля в диалоговом окне следующим образом:

    - **Тип**  =  **Пользовательский тип расширения**

    - Тип = `Microsoft.VisualStudio.ArchitectureTools.CustomToolboxItems`

        > [!NOTE]
        > Это значение не указано в раскрывающемся списке. Его необходимо ввести с помощью клавиатуры.

    - **Исходный код**  =  **Файл в файловой системе**.

    - **Path** = ваш **tbxinfo** файл, например **митулс. tbxinfo**

8. Выполните построение проекта.

9. **Чтобы убедиться, что расширение работает**, нажмите клавишу F5. Откроется экспериментальный экземпляр Visual Studio.

     В экспериментальном экземпляре создайте или откройте схему UML соответствующего типа. Убедитесь, что новый инструмент отображается на панели элементов и что он правильно создает элементы.

10. **Чтобы получить VSIX-файл для развертывания, выполните следующие действия.** В проводнике Windows откройте папку **.\бин\дебуг** или **.\бин\релеасе** , чтобы найти **VSIX** файл. Это файл расширения [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Его можно установить на своем компьютере и отправить другим пользователям Visual Studio.

#### <a name="to-install-custom-tools-from-a-visual-studio-extension"></a>Установка пользовательских инструментов из расширения Visual Studio

1. Откройте файл `.vsix` в проводнике Windows или в Visual Studio.

2. В появившемся диалоговом окне нажмите кнопку **установить** .

3. Чтобы удалить или временно отключить расширение, откройте меню **Сервис** и выберите пункт **расширения и обновления** .

## <a name="localization"></a>Локализация
 Можно создать расширение, которое при установке на другом компьютере отображает имена и подсказки для инструмента на языке целевого компьютера.

#### <a name="to-provide-versions-of-the-tool-in-more-than-one-language"></a>Предоставление версий инструмента на нескольких языках

1. Создайте проект расширения Visual Studio, который содержит один или несколько пользовательских инструментов.

    В **tbxinfo** файле используйте метод файла ресурсов, чтобы определить средство `displayName` , панель элементов `tabName` и подсказку. Создайте файл ресурсов, в котором определяются эти строки, скомпилируйте его в сборку, а затем сошлитесь на него из файла TBXINFO.

2. Создайте дополнительные сборки, содержащие файлы ресурсов со строками на других языках.

3. Поместите каждую дополнительную сборку в папку, имя которой является идентификатором соответствующего языка и региональных параметров. Например, поместите французскую версию сборки в папку с именем **fr**.

4. Следует использовать нейтральный идентификатор языка и региональных параметров (как правило, состоящий из двух букв), а не указывать конкретные язык и региональные параметры, например `fr-CA`. Дополнительные сведения о кодах языка и региональных параметрах см. в разделе [метод CultureInfo. DataCulture](https://msdn.microsoft.com/library/system.globalization.cultureinfo.getcultures(VS.100).aspx), который предоставляет полный список кодов языка и региональных параметров.

5. Выполните сборку расширения Visual Studio и распределите его.

6. Когда расширение установлено на другом компьютере, будет автоматически загружается версия файла ресурсов для языка и региональных параметров локального пользователя. Если вы не указали версию для языка и региональных параметров пользователя, будут использоваться ресурсы по умолчанию.

   Этот метод нельзя использовать для установки разных версий схемы прототипа. Имена элементов и соединителей будут одинаковыми во всех установках.

## <a name="other-toolbox-operations"></a>Другие операции панели элементов
 Обычно в [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] панель элементов можно персонализировать, переименовывая инструменты, перемещая их на другие вкладки и удаляя их. Однако эти изменения не сохраняются для пользовательских инструментов моделирования, которые созданы с использованием процедур, описанных в этом разделе. При перезапуске [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] пользовательские инструменты отображаются с заданными для них именами и расположениями на панели элементов.

 Кроме того, при выполнении команды **Сбросить Панель элементов** будут отображаться пользовательские средства. Однако после перезапуска [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] они снова появляются.

## <a name="see-also"></a>См. также:
 [Расширение моделей и схем UML](../modeling/extend-uml-models-and-diagrams.md) [Определение профиля для расширения UML](../modeling/define-a-profile-to-extend-uml.md) [Определение команды меню на схеме моделирования](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [Определение ограничений проверки для моделей UML](../modeling/define-validation-constraints-for-uml-models.md)
