---
title: Внутри редактора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 32
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8dfc751b040bd775c3f55ff7db804c2a16d45d5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843379"
---
# <a name="inside-the-editor"></a>Компоненты редактора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Редактор состоит из нескольких различных подсистем, которые предназначены для того, чтобы Текстовая модель редактора отличалась от представления текста и пользовательского интерфейса.  
  
 В следующих разделах описываются различные аспекты редактора:  
  
- [Общие сведения о подсистемах](../extensibility/inside-the-editor.md#overview)  
  
- [Текстовая модель](../extensibility/inside-the-editor.md#textmodel)  
  
- [Представление текста](../extensibility/inside-the-editor.md#textview)  
  
  В следующих разделах описываются функции редактора:  
  
- [Теги и классификаторы](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
- [Элементов оформления](../extensibility/inside-the-editor.md#adornments)  
  
- [Проекция](../extensibility/inside-the-editor.md#projection)  
  
- [Структура](../extensibility/inside-the-editor.md#outlining)  
  
- [Привязки мыши](../extensibility/inside-the-editor.md#mousebindings)  
  
- [Операции редактора](../extensibility/inside-the-editor.md#editoroperations)  
  
- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
## <a name="overview-of-the-subsystems"></a><a name="overview"></a> Общие сведения о подсистемах  
  
### <a name="text-model-subsystem"></a>Подсистема текстовых моделей  
 Подсистема текстовых моделей отвечает за представление текста и возможность его манипуляции. Подсистема текстовых моделей содержит <xref:Microsoft.VisualStudio.Text.ITextBuffer> интерфейс, который описывает последовательность символов, отображаемых редактором. Этот текст можно изменять, относить и иным образом манипулировать различными способами. В текстовой модели также представлены типы для следующих аспектов.  
  
- Служба, которая связывает текст с файлами и управляет чтением и записью в файловой системе.  
  
- Разностная служба, которая находит минимальные различия между двумя последовательностями объектов.  
  
- Система для описания текста в буфере с точки зрения подмножества текста в других буферах.  
  
  Подсистема текстовых моделей свободна от основных понятий пользовательского интерфейса. Например, он не несет ответственности за форматирование текста или макет текста и не имеет сведений о визуальных элементах оформления, которые могут быть связаны с текстом.  
  
  Открытые типы подсистемы текстовых моделей содержатся в Microsoft.VisualStudio.Text.Data.dll и Microsoft.VisualStudio.CoreUtilitiy.dll, которые зависят только от .NET Framework библиотеки базовых классов и Managed Extensibility Framework (MEF).  
  
### <a name="text-view-subsystem"></a>Подсистема представления текста  
 Подсистема представления текста отвечает за форматирование и отображение текста. Типы в этой подсистеме делятся на два уровня в зависимости от того, используют ли типы Windows Presentation Foundation (WPF). Наиболее важными типами являются <xref:Microsoft.VisualStudio.Text.Editor.ITextView> и <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> , которые управляют набором отображаемых текстовых строк, а также курсором, выделением и возможностями декоративного текста с помощью элементов ПОЛЬЗОВАТЕЛЬСКОГО интерфейса WPF. Эта подсистема также предоставляет поля вокруг области вывода текста. Эти поля могут быть расширены и могут содержать различные виды содержимого и визуальных эффектов. Примерами полей являются отображение номеров строк и полос прокрутки.  
  
 Открытые типы подсистемы представления текста содержатся в Microsoft.VisualStudio.Text.UI.dll и Microsoft.VisualStudio.Text.UI.Wpf.dll. Первая сборка содержит независимые от платформы элементы, а вторая содержит элементы, относящиеся к WPF.  
  
### <a name="classification-subsystem"></a>Подсистема классификации  
 Подсистема классификации отвечает за определение свойств шрифта для текста. Классификатор разбивает текст на разные классы, например "ключевое слово" или "Comment". Схема формата классификации связывает эти классы с фактическими свойствами шрифта, например "Blue consolas 10 pt". Эти сведения используются в текстовом представлении при форматировании и отрисовке текста. Теги, которые более подробно описаны далее в этом разделе, позволяют связывать данные с диапазонами текста.  
  
 Общедоступные типы подсистемы классификации содержатся в Microsoft.VisualStudio.Text.Logic.dll и взаимодействуют с визуальными аспектами классификации, которые содержатся в Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### <a name="operations-subsystem"></a>Подсистема операций  
 Подсистема операций определяет поведение редактора. Он обеспечивает реализацию команд редактора Visual Studio и системы отмены.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Более подробное рассмотрение текстовой модели и представления текста  
  
### <a name="the-text-model"></a><a name="textmodel"></a> Текстовая модель  
 Подсистема текстовых моделей состоит из различных групп текстовых типов. К ним относятся буфер текста, текстовые моментальные снимки и текстовые диапазоны.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Текстовые буферы и моментальные снимки текста  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer>Интерфейс представляет последовательность символов Юникода, закодированных с помощью UTF-16, который является кодировкой, используемой `String` типом в .NET Framework. Текстовый буфер можно сохранить как документ файловой системы, но это необязательно.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>Используется для создания пустого текстового буфера или текстового буфера, который инициализируется из строки или из <xref:System.IO.TextReader> . Текстовый буфер можно сохранить в файловой системе как <xref:Microsoft.VisualStudio.Text.ITextDocument> .  
  
 Текстовый буфер может быть изменен любым потоком до тех пор, пока поток не перенесет себя за владение текстовым буфером путем вызова <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . После этого только этот поток может выполнять изменения.  
  
 В течение времени существования текстовый буфер может проходить через несколько версий. Новая версия создается каждый раз при изменении буфера, а неизменяемое <xref:Microsoft.VisualStudio.Text.ITextSnapshot> — содержимое этой версии буфера. Поскольку моментальные снимки текста являются неизменяемыми, можно получить доступ к моментальному снимку текста в любом потоке без ограничений, даже если текстовый буфер, который он представляет, остается измененным.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Моментальные снимки текста и строки моментальных снимков текста  
 Содержимое текстового моментального снимка можно просмотреть как последовательность символов или как последовательность строк. Символы и строки индексируются, начиная с нуля. Пустой текстовый моментальный снимок содержит ноль символов и одну пустую строку. Строка отделяется любой допустимой последовательностью символов разрыва строки Юникода, а также началом или концом буфера. Символы разрыва строки явно представлены в текстовом снимке, а разрывы строк в снимке текста должны быть одинаковыми.  
  
> [!NOTE]
> Дополнительные сведения о символах разрыва строки в редакторе Visual Studio см. в разделе [кодировки и разрывы строк](../ide/encodings-and-line-breaks.md).  
  
 Строка текста представлена <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> объектом, который можно получить из текстового моментального снимка для конкретного номера строки или для определенной позиции символа.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Точки snapshotpoint относятся, Снапшотспанс и Нормализедснапшотспанколлектионс  
 <xref:Microsoft.VisualStudio.Text.SnapshotPoint>Представляет позиции символа в снимке. Гарантия должна лежать в пределах от нуля до длины моментального снимка. <xref:Microsoft.VisualStudio.Text.SnapshotSpan>Представляет охват текста в моментальном снимке. Конечное расположение гарантированно находится в диапазоне от нуля до длины моментального снимка. Объект <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> состоит из набора <xref:Microsoft.VisualStudio.Text.SnapshotSpan> объектов из одного и того же моментального снимка.  
  
#### <a name="spans-and-normalizedspancollections"></a>Охваты и Нормализедспанколлектионс  
 <xref:Microsoft.VisualStudio.Text.Span>Представляет интервал, который может быть применен к диапазону текста в моментальном снимке текста. Позиции моментальных снимков отсчитываются от нуля, поэтому диапазоны могут начинаться в любой позиции, включая ноль. `End`Свойство диапазона равно сумме его `Start` Свойства и его `Length` Свойства. В не `Span` входит символ, индексируемый `End` свойством. Например, диапазон с Start = 5 и length = 3 имеет End = 8 и содержит символы в позициях 5, 6 и 7. Для этого диапазона используется нотация 5.. 8).  
  
 Два диапазона пересекаются, если они имеют общие позиции, включая конечное положение. Таким образом, пересечение [3, 5) и [2, 7) имеет значение [3, 5), а пересечение [3, 5) и [5, 7) равно [5, 5). (Обратите внимание, что [5, 5) является пустым диапазоном.)  
  
 Два диапазона перекрываются, если они имеют общие позиции, за исключением конечной позиции. Пустой диапазон никогда не пересекается с любым другим диапазоном, а перекрытие двух диапазонов никогда не будет пустым.  
  
 <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection>Представляет собой список диапазонов в порядке начальных свойств диапазонов. В списке перекрывающиеся или смежные диапазоны объединяются. Например, при наличии набора диапазонов [5.. 9), [0.. 1), [3.. 6) и [9.. 10) нормализованный список диапазонов равен [0.. 1), [3.. 10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>Уведомления об изменении Итекстедит, TextVersion и текста  
 Содержимое текстового буфера можно изменить с помощью <xref:Microsoft.VisualStudio.Text.ITextEdit> объекта. Создание такого объекта (с помощью одного из `CreateEdit()` методов <xref:Microsoft.VisualStudio.Text.ITextBuffer> ) запускает текстовую транзакцию, которая состоит из редактирования текста. Каждое изменение — это замена некоторого фрагмента текста в буфере строкой. Координаты и содержимое каждого изменения выражаются относительно моментального снимка буфера при запуске транзакции. <xref:Microsoft.VisualStudio.Text.ITextEdit>Объект корректирует координаты изменений, затрагиваемых другими изменениями в той же транзакции.  
  
 Например, рассмотрим текстовый буфер, содержащий следующую строку:  
  
```  
abcdefghij  
```  
  
 Применить транзакцию, которая содержит два изменения, одно изменение, заменяющее диапазон в [2.. 4), с помощью символа `X` и второго изменения, заменяющего диапазон в [6.. 9), с помощью символа `Y` . Результат представляет собой следующий буфер:  
  
```  
abXefYj  
```  
  
 Координаты второго изменения были вычислены по отношению к содержимому буфера в начале транзакции до применения первого изменения.  
  
 Изменения в буфере вступают в силу при <xref:Microsoft.VisualStudio.Text.ITextEdit> фиксации объекта путем вызова его `Apply()` метода. Если было по крайней мере одно непустое изменение, <xref:Microsoft.VisualStudio.Text.ITextVersion> создается новое, <xref:Microsoft.VisualStudio.Text.ITextSnapshot> создается новое и создается одно `Changed` событие. Каждая версия текста имеет другой текстовый моментальный снимок. Текстовый снимок представляет полное состояние текстового буфера после транзакции изменения, но версия текста описывает только изменения одного моментального снимка на следующий. Как правило, текстовые моментальные снимки предназначены для однократного использования, а затем отбрасываются, в то время как версии текста должны оставаться в активном состоянии.  
  
 Версия текста содержит <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . В этой коллекции описаны изменения, которые при применении к моментальному снимку будут создавать последующий моментальный снимок. Каждая <xref:Microsoft.VisualStudio.Text.ITextChange> в коллекции содержит позиции символа изменения, замененной строки и строки замены. Замененная строка пуста для базовой вставки, а замещающая строка пуста для базового удаления. Нормализованная коллекция всегда используется `null` для последней версии текстового буфера.  
  
 <xref:Microsoft.VisualStudio.Text.ITextEdit>В любой момент времени для текстового буфера можно создать только один объект, и все изменения текста должны выполняться в потоке, владеющем текстовым буфером (если владение запросило). Изменение текста может быть отменено путем вызова его `Cancel` метода или `Dispose` метода.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> также предоставляет `Insert()` `Delete()` методы, и `Replace()` , которые похожи на интерфейсы, находящиеся в <xref:Microsoft.VisualStudio.Text.ITextEdit> интерфейсе. Вызов этих методов приведет к тому же результату, что <xref:Microsoft.VisualStudio.Text.ITextEdit> и создание объекта, выполнение аналогичного вызова, а затем применение изменения.  
  
#### <a name="tracking-points-and-tracking-spans"></a>Точки отслеживания и диапазоны отслеживания  
 Объект <xref:Microsoft.VisualStudio.Text.ITrackingPoint> представляет позиции символа в текстовом буфере. Если буфер редактируется способом, который приводит к сдвигу позиции символа, точка отслеживания перемещается вместе с ней. Например, если точка отслеживания ссылается на позицию 10 в буфере и в начало буфера вставляется пять символов, точка отслеживания затем ссылается на позицию 15. Если вставка выполняется точно в той позиции, которая обозначена точкой отслеживания, ее поведение определяется свойством <xref:Microsoft.VisualStudio.Text.PointTrackingMode> , которое может иметь значение `Positive` или `Negative` . Если режим отслеживания положительный, точка отслеживания ссылается на тот же символ, который теперь находится в конце вставки; Если режим отслеживания отрицательный, точка отслеживания ссылается на первый вставленный символ в исходной позиции. Если символ в позиции, представленной точкой отслеживания, удаляется, точка отслеживания переходит к первому символу, следующему за удаленным диапазоном. Например, если точка отслеживания ссылается на символ в позиции 5, а символы в позициях от 3 до 6 удаляются, точка отслеживания ссылается на символ в позиции 3.  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan>Представляет диапазон символов, а не только одну. Его поведение определяется свойством <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . Если задан режим отслеживания диапазонов <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> , размер области отслеживания увеличивается для включения текста, вставленного на его краях; если задан режим отслеживания Span <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> , то диапазон отслеживания не включает текст, вставленный на его краях. Однако если режим отслеживания диапазона равен, то при <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> вставке текущая позиция помещается к началу, а в режиме отслеживания диапазонов <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> Вставка помещается в конец.  
  
 Можно получить позицию точки отслеживания или интервала отслеживания для любого моментального снимка текстового буфера, к которому они принадлежат. На точки отслеживания и диапазоны отслеживания можно безопасно ссылаться из любого потока.  
  
#### <a name="content-types"></a>Типы содержимого  
 Типы содержимого — это механизм для определения различных типов содержимого. Типом содержимого может быть тип файла, например "Text", "Code" или "binary", или тип технологии, такой как "XML", "VB" или "c#". Например, слово «using» является ключевым словом в C# и Visual Basic, но не в других языках программирования. Таким образом, определение этого ключевого слова будет ограничено типами содержимого "c#" и "VB".  
  
 Типы содержимого используются в качестве фильтра для оформлений и других элементов редактора. Многие функции редактора и точки расширения определяются для каждого типа содержимого. Например, цвет текста отличается для обычных текстовых файлов, XML-файлов и Visual Basic файлов исходного кода. Для текстовых буферов обычно назначается тип содержимого при их создании, а тип содержимого текстового буфера может быть изменен.  
  
 Типы содержимого могут многократно наследовать от других типов содержимого. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>Позволяет указать несколько базовых типов в качестве родительских для заданного типа содержимого.  
  
 Разработчики могут определять собственные типы содержимого и регистрировать их с помощью <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . Многие функции редактора можно определить по отношению к конкретному типу содержимого с помощью <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . Например, можно определить поля редактора, декоративные элементы и обработчики мыши, чтобы они применялись только к редакторам, которые отображают определенные типы содержимого.  
  
### <a name="the-text-view"></a><a name="textview"></a> Представление текста  
 Часть представления в шаблоне контроллера представления модели (MVC) Определяет текстовое представление, форматирование представления, графические элементы, такие как полоса прокрутки, и курсор. Все элементы представления редактора Visual Studio основаны на WPF.  
  
#### <a name="text-views"></a>Текстовые представления  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView>Интерфейс представляет собой независимое от платформы представление текстового представления. Он используется в основном для вывода текстовых документов в окне, но его также можно использовать для других целей, например, в подсказке.  
  
 Текстовое представление ссылается на различные виды текстовых буферов. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>Свойство ссылается на <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> объект, который указывает на три разных текстовых буфера: буфер данных, который является верхним буфером уровня данных, буфером редактирования, в котором происходит редактирование, и визуальным буфером, который отображается в текстовом представлении.  
  
 Текст форматируется на основе классификаторов, присоединенных к базовому текстовому буферу, и декоративный с помощью поставщиков декоративных элементов, присоединенных к самому текстовому представлению.  
  
#### <a name="the-text-view-coordinate-system"></a>Система координат представления текста  
 Система координат текстового представления определяет позиции в текстовом представлении. В этой системе координат значение x 0,0 соответствует левому краю отображаемого текста, а значение y 0,0 соответствует верхнему краю отображаемого текста. Координата x увеличивается слева направо, а координата y увеличивается сверху вниз.  
  
 Окно просмотра (часть текста, видимое в текстовом окне) не может быть прокручено по горизонтали по вертикали. Окно просмотра прокручивается горизонтально, изменяя его левую координату таким образом, чтобы оно перемещалось по отношению к области рисования. Однако окно просмотра можно прокручивать по вертикали только путем изменения отображаемого текста, что приводит к <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> возникновению события.  
  
 Расстояния в системе координат соответствуют логическим пикселям. Если область отрисовки текста отображается без преобразования масштабирования, то одна единица в системе координат отрисовки текста соответствует одному пикселю на экране.  
  
#### <a name="margins"></a>Поля  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>Интерфейс представляет поле и позволяет контролировать видимость поля и его размер. Существует четыре заранее заданных поля, которые называются "верхним", "слева", "справа" и "снизу" и прикрепляются к верхнему, нижнему, левому или правому краю представления. Эти поля представляют собой контейнеры, в которых можно разместить другие поля. Интерфейс определяет методы, которые возвращают размер поля и видимость поля. Поля — это визуальные элементы, предоставляющие дополнительные сведения о представлении текста, к которому они присоединены. Например, поле номер строки отображает номера строк для текстового представления. Поле глифов отображает элементы пользовательского интерфейса.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>Интерфейс обрабатывает создание и размещение полей. Поля можно упорядочивать по отношению к другим полям. Поля с более высоким приоритетом располагаются ближе к представлению текста. Например, если имеется два левого поля, поля а и поля B, а поле B имеет более низкий приоритет, чем поле A, то слева от поля A отображается поле B.  
  
#### <a name="the-text-view-host"></a>Узел представления текста  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Интерфейс содержит текстовое представление и все смежные украшения, сопровождающие представление, например полосы прокрутки. Узел представления текста также содержит поля, присоединенные к границе представления.  
  
#### <a name="formatted-text"></a>Форматированный текст  
 Текст, отображаемый в текстовом представлении, состоит из <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> объектов. Каждая строка текстового представления соответствует одной строке текста в текстовом представлении. Длинные строки в базовом текстовом буфере могут быть либо частично скрыты (если перенос по словам не включены), либо разбиваются на несколько строк текстового представления. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>Интерфейс содержит методы и свойства для сопоставления координат и символов, а также для оформлений, которые могут быть связаны со строкой.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> объекты создаются с помощью <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> интерфейса. Если вы только беспокоите текст, который в настоящее время отображается в представлении, можно игнорировать источник форматирования. Если вы заинтересованы в формате текста, который не отображается в представлении (например, для поддержки форматированного текста и вставки), можно использовать <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> для форматирования текста в текстовом буфере.  
  
 Текстовое представление форматируется <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> по одному за раз.  
  
## <a name="editor-features"></a>Функции редактора  
 Функции редактора разработаны таким образом, чтобы определение функции было отделено от его реализации. Редактор включает следующие функции:  
  
- Теги и классификаторы  
  
- Элементов оформления  
  
- Проекция  
  
- Структуризация  
  
- Привязки мыши и клавиш  
  
- Операции и примитивы  
  
- IntelliSense  
  
### <a name="tags-and-classifiers"></a><a name="tagsandclassifiers"></a> Теги и классификаторы  
 Теги — это маркеры, связанные с диапазоном текста. Они могут быть представлены различными способами, например с помощью цветового выделения текста, подчеркивания, графики или всплывающих окон. Классификаторы являются одним из типов тегов.  
  
 Другие виды тегов предназначены <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> для выделения текста, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> для структурирования и <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> для ошибок компиляции.  
  
#### <a name="classification-types"></a>Типы классификации  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Интерфейс представляет класс эквивалентности, который является абстрактной категорией текста. Типы классификации могут многократно наследовать от других типов классификации. Например, классификация языка программирования может включать "ключевое слово", "Comment" и "identifier", которые являются производными от "Code". Типы классификации естественного языка могут включать "существительные", "глагол" и "прилагательное", которые являются производными от "естественного языка".  
  
#### <a name="classifications"></a>Классификация  
 Классификация — это экземпляр определенного типа классификации, который обычно находится над диапазоном текста. Объект <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> используется для представления классификации. Диапазон классификации можно рассматривать как метку, охватывающую определенный фрагмент текста, и сообщает системе, что этот фрагмент текста относится к определенному типу классификации.  
  
#### <a name="classifiers"></a>Классификаторов  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier>— Это механизм, который разбивает текст на набор классификаций. Классификаторы должны быть определены для конкретных типов содержимого и созданы для определенных текстовых буферов. Клиенты должны реализовать <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> для участия в классификации текста.  
  
#### <a name="classifier-aggregators"></a>Агрегаторы-классификаторы  
 Агрегатор-классификатор — это механизм, объединяющий все классификаторы одного текстового буфера в один набор классификаций. Например, классификатор C# и классификатор английского языка могут создавать классификации на основе комментария в файле C#. Рассмотрим этот комментарий:  
  
```  
// This method produces a classifier  
```  
  
 Классификатор C# может пометить весь диапазон как комментарий, а классификатор английского языка может классифицировать "формирование" как "глагол" и "метод" как "существительное". Агрегатор создает набор неперекрывающихся классификаций, а тип набора основан на всех вкладах.  
  
 Агрегатор-Классификатор также является классификатором, поскольку он разбивает текст на набор классификаций. Агрегатор-Классификатор также гарантирует, что нет перекрывающихся классификаций и что классификации сортируются. Отдельные классификаторы бесплатно возвращают любой набор классификаций в любом порядке и перекрываются любым способом.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Форматирование и цветность классификации  
 Форматирование текста — это пример функции, построенной на основе классификации текста. Он используется слоем представления текста для определения отображения текста в приложении. Область форматирования текста зависит от WPF, но логическое определение классификаций — нет.  
  
 Формат классификации — это набор свойств форматирования для определенного типа классификации. Эти форматы наследуются от формата родителя типа классификации.  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Представляет собой карту из типа классификации в набор свойств форматирования текста. Реализация формата Map в редакторе обрабатывает все экспорты форматов классификации.  
  
### <a name="adornments"></a><a name="adornments"></a> Элементов оформления  
 Декоративные элементы — это графические эффекты, которые не связаны непосредственно с шрифтом и цветом символов в представлении текста. Например, подчеркнутая красной волнистой линией, используемая для пометки некомпилируемого кода во многих языках программирования, — это внедренное Оформление, а всплывающие подсказки — это всплывающие элементы. Декоративные элементы являются производными от <xref:System.Windows.UIElement> и реализуют <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Два специализированных типа тега оформления — это <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , для оформлений, которые занимают то же пространство, что и текст в представлении, и <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> для подчеркивания волнистой линией.  
  
 Внедренные элементы оформления — это графические изображения, которые образуют часть представления форматированного текста. Они упорядочены по разным слоям Z-порядка. Существует три встроенных слоя: текст, курсор и выделенный фрагмент. Однако разработчики могут определить дополнительные уровни и разместить их в порядке друг с другом. Три вида внедренных оформлений — это относительные текстовые элементы (которые перемещаются при перемещении текста и удаляются при удалении текста), элементы, относительные для представления (которые должны делаться с нетекстовыми частями представления) и декоративные элементы, контролируемые владельцем (разработчик должен управлять их размещением).  
  
 Всплывающие украшения — это графические объекты, отображаемые в маленьком окне над текстовым представлением, например подсказки.  
  
### <a name="projection"></a><a name="projection"></a> Отображения  
 Проекция — это метод для создания другого типа текстового буфера, который фактически не сохраняет текст, а объединяет текст из других текстовых буферов. Например, буфер проекции можно использовать для сцепления текста из двух других буферов и представления результата так, как если бы он был в одном буфере, или для скрытия частей текста в одном буфере. Буфер проекции может служить исходным буфером для другого буфера проекции. Набор буферов, связанных проекцией, может быть создан для переупорядочения текста различными способами. (Такой набор также известен как *граф буфера*.) Функция структурирования текста в Visual Studio реализуется с помощью буфера проекции, чтобы скрыть свернутый текст, а редактор Visual Studio для ASP.NET Pages использует проекцию для поддержки встраиваемых языков, таких как Visual Basic и C#.  
  
 Объект <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> создается с помощью <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Буфер проекции представлен упорядоченной последовательностью <xref:Microsoft.VisualStudio.Text.ITrackingSpan> объектов, называемой *исходными диапазонами*. Содержимое этих диапазонов представлено в виде последовательности символов. Текстовые буферы, из которых рисуются исходные диапазоны, называются *исходными буферами*. Клиентам буфера проекции не нужно знать, что он отличается от обычного текстового буфера.  
  
 Буфер проекции прослушивает события изменения текста в исходных буферах. При изменении текста в исходном диапазоне буфер проекции сопоставляет измененные текстовые координаты с собственными координатами и создает соответствующие события изменения текста. Например, рассмотрим исходные буферы A и B с этими содержимым:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Если буфер проекции P формируется из двух текстовых диапазонов, один из которых имеет буфер A, а другой — все буфер б, то P имеет следующее содержимое:  
  
```  
P: ABCDEvwxyz  
```  
  
 Если подстрока `xy` удаляется из буфера B, то buffer P создает событие, указывающее, что символы в позициях 7 и 8 были удалены.  
  
 Кроме того, буфер проекции можно изменять напрямую. Он распространяет изменения в соответствующие исходные буферы. Например, если строка вставляется в буфер P в позиции 6 (исходная позиция символа "v"), вставка передается в буфер B в позиции 1.  
  
 Существуют ограничения на исходные диапазоны, которые вносят вклад в буфер проекции. Исходные диапазоны не могут перекрываться; расположение в буфере проекции не может сопоставляться с более чем одним расположением в любом исходном буфере, а расположение в исходном буфере не может сопоставляться с более чем одним расположением в буфере проекции. В связи исходного буфера не допускаются циклы.  
  
 События возникают при изменении набора исходных буферов для буфера проекции и при изменении набора исходных диапазонов.  
  
 Буфер элизии — это специальный тип буфера проекции. Он используется в основном для структурирования и для операций, которые расширяют и сворачиваются блоки текста. Буфер элизии основан только на одном исходном буфере, и диапазоны в буфере элизии должны быть упорядочены так же, как упорядочены в исходном буфере.  
  
##### <a name="the-buffer-graph"></a>Граф буфера  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Интерфейс обеспечивает сопоставление в графе буферов проекции. Все текстовые буферы и буферы проекции собираются на направленном ациклический графе, подобно абстрактному дереву синтаксиса, созданному компилятором языка. Граф определяется верхним буфером, который может быть любым текстовым буфером. Граф буфера может сопоставлять точки в верхнем буфере с точкой в исходном буфере или от диапазона в верхнем буфере до набора диапазонов в исходном буфере. Аналогичным образом он может сопоставлять точку или диапазон от исходного буфера к точке в верхнем буфере. Графы буферов создаются с помощью <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .  
  
##### <a name="events-and-projection-buffers"></a>События и буферы проекции  
 При изменении буфера проекции изменения отправляются из буфера проекции в буферы, которые зависят от него. После изменения всех буферов создаются события изменения буфера, начиная с самого глубокого буфера.  
  
### <a name="outlining"></a><a name="outlining"></a> Структурирования  
 Структурирование — это возможность разворачивать или сворачивать различные блоки текста в текстовом представлении. Структурирование определяется как разновидность <xref:Microsoft.VisualStudio.Text.Tagging.ITag> таким же образом, как и пользовательские оформления. <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>— Это тег, определяющий область текста, которую можно развернуть или свернуть. Чтобы использовать структуризацию, необходимо импортировать, <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> чтобы получить <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . Диспетчер структуры перечисляет, сворачивает и развертывает различные блоки, представленные в виде <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> объектов, и вызывает события соответствующим образом.  
  
### <a name="mouse-bindings"></a><a name="mousebindings"></a> Привязки мыши  
 Привязки мыши связывают перемещения мыши с различными командами. Привязки мыши определяются с помощью <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> , а сочетания клавиш определяются с помощью <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . Объект <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> автоматически создает экземпляры всех привязок и подключает их к событиям мыши в представлении.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>Интерфейс содержит обработчики событий, выполняемых до и после обработки, для различных событий мыши. Для решения одного из событий можно переопределить некоторые методы в <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .  
  
### <a name="editor-operations"></a><a name="editoroperations"></a> Операции редактора  
 Операции редактора можно использовать для автоматизации взаимодействия с редактором для сценариев или других целей. Можно импортировать в <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> операции доступа к заданному <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Затем эти объекты можно использовать для изменения выбора, прокрутки представления или перемещения курсора в различные части представления.  
  
### <a name="intellisense"></a><a name="intellisense"></a> IntelliSense  
 IntelliSense поддерживает завершение операторов, справку по сигнатурам (также называемую сведениями о параметрах), краткие сведения и лампочки.  
  
 Завершение операторов предоставляет всплывающие списки возможных завершений для имен методов, XML-элементов и других элементов кода или разметки. Как правило, пользовательский жест вызывает сеанс завершения. В сеансе отображается список возможных завершений, и пользователь может выбрать один или закрыть список. Объект <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> отвечает за создание и активацию <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . Выполняет <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Вычисление <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> элементов завершения для сеанса.  
  
## <a name="see-also"></a>См. также:  
 [Точки расширения языковой службы и редактора](../extensibility/language-service-and-editor-extension-points.md)   
 [Импорт в редакторе](../extensibility/editor-imports.md)
