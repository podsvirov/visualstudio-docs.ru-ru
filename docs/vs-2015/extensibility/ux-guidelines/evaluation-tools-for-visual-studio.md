---
title: Средства для оценки
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24ea04e59178248c7a9795a2f928c311ba83db2e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824074"
---
# <a name="evaluation-tools-for-visual-studio"></a>Средства оценки для Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="craftsmanship-checklist-for-visual-studio"></a>Контрольный список ремесленника для Visual Studio
 Используйте этот контрольный список, чтобы оценить качество взаимодействия с пользователем для визуальных элементов и сведений о взаимодействии.

### <a name="overview"></a>Обзор

- Убедитесь, что все команды приводят к обратным результатам, которые сообщают пользователям о том, что их команды выполнены.

- Убедитесь, что все элементы пользовательского интерфейса и элементы управления видимы во всех темах и в режиме высокая контрастность.

- Убедитесь, что неактивные и активные выделения всегда различаются как в стандартном, так и в режиме высокая контрастность.

- Убедитесь, что фокус всегда виден и видим.

### <a name="performance"></a>Производительность

- Убедитесь, что отображается индикатор "занято", если выполнение команды занимает более одной секунды.

- Убедитесь, что если для завершения выполнения команды требуется более 10 секунд, отображается явный индикатор выполнения, который либо находится в состоянии "не завершено" (предпочтительно), либо не определен.

### <a name="ui-text"></a>Текст пользовательского интерфейса

- Убедитесь, что все метки являются предложением или заголовком, а текст не является полностью строчным.

    ||Правильно|Неправильно|
    |-|-------------|---------------|
    |**Текст команды (все)**|Регистр предложений:<br /><br /> **Имя каталога:**|Имя каталога:|
    |**Текст кнопки (клиент)**|Регистр заголовка:<br /><br /> **[По умолчанию]**|УСТАНОВИТЬ ПО УМОЛЧАНИЮ|
    |**Текст кнопки (в сети)**|Регистр предложений:<br /><br /> **[По умолчанию]**||

- Убедитесь, что все метки, за исключением заголовков и кнопок групп, заканчиваются двоеточием и предшествуют элементу управления, с которым они связаны.

- Убедитесь в том, что кнопки, команды и ссылки на команды, которые запускают пользовательский интерфейс для захвата входных данных пользователя, находятся в многоточии **[...]**.

  Примеры:

  - Кнопка **[дополнительно...]** в диалоговом окне.

  - Параметры команды в меню Сервис (**сервис > параметры**) не должны возобновлять многоточие, так как запуск диалогового окна является задачей команды.

- Убедитесь, что пользовательский интерфейс не содержит сокращений, за исключением стандартных отраслевых терминов. Например, не нужно указывать ни HTML, ни TCP/IP, несмотря на то, что не хватает памяти, а персональные данные (личные сведения).

### <a name="keyboard-access"></a>Доступ с клавиатуры

- Убедитесь, что существует способ выполнения каждой задачи с помощью клавиатуры. Как правило, это осуществляется через клавиатурный доступ для каждого элемента управления, но для некоторых очень удобных областей решения, таких как переход в представление кода, приемлемо.

- Убедитесь, что элементы управления можно перебрать в логическом порядке (слева направо и сверху вниз). Хотя это и рекомендуется для большинства элементов управления, этот подход требуется не для всех элементов управления. Например, убедитесь, что элементы управления "переключатель" находятся в группе с одной остановкой табуляции.

- Убедитесь, что все элементы управления имеют метки и что каждая метка имеет назначенную клавишу (исключения включают некоторые элементы управления, не помеченные метками, которые могут следовать за помеченным элементом управления на вкладке).

- Убедитесь в отсутствии назначенных конфликтов.

### <a name="fonts"></a>Шрифты

- Убедитесь, что все шрифты (начертание, размер, цвет) используются согласованно и поддерживают иерархию.

- Убедитесь, что все элементы пользовательского интерфейса используют службу шрифтов среды. (См. раздел [шрифты и форматирование для Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))

     Чтобы проверить, используется ли служба, перейдите в **меню сервис > параметры > шрифты и цвета**. В раскрывающемся списке Параметры выберите пункт Шрифт среды и измените начертание шрифта на что-то другое (например, Хэррингтон или Comic Sans) и задайте размер равным 12 пт. Затем нажмите кнопку ОК. Может потребоваться перезапустить интегрированную среду разработки, но большая часть пользовательского интерфейса будет изменена немедленно. Области, не изменяющие изменение шрифта даже при перезапуске, не используют шрифт среды.

- Убедитесь, что шрифты, производные от службы (например, полужирный или увеличенный текст), сохраняют свой размер и форматирование по отношению к «нормальному» тексту при изменении размера шрифта среды.

- Убедитесь, что ошибки обрезки отсутствуют из-за увеличенных шрифтов. Шрифты, получающие обрезанные элементы, скорее всего, являются результатом элементов управления фиксированной высоты или контейнеров фиксированной высоты.

### <a name="dialogs"></a>Диалоговые окна

- Убедитесь, что заголовок диалогового окна совпадает с командой, которая его запустила.

- Убедитесь, что все стандартные элементы управления соответствуют операционной системе: цвет фона — стандартный, и ни один из элементов управления не должен иметь специальный шаблон повторного шаблона, который делает их отличными от стандартных элементов управления.

- Убедитесь, что размер полей в пределах формы должен составлять 12 пикселей и должен быть единообразным и согласованным.

- Убедитесь, что диалоговые окна отображаются по центру в оболочке IDE или в окне, в котором они порождены.

- При необходимости размер диалоговых окон должен быть изменяемым. Для изменяемых диалоговых окон убедитесь, что после изменения размера размеры соответствующих элементов управления должны измениться, а другие части диалогового окна остаются постоянными.

- Убедитесь, что в диалоговых окнах с изменяемым размером сохраняется любой настраиваемый пользователем размер (размер, расположение, расширение элементов управления диалогового окна и т. д.).

- Убедитесь, что в заголовке окна нет значка.

- Убедитесь, что в строке заголовка отсутствуют кнопки сворачивания и развернуть.

#### <a name="dialog-operation-buttons-vs-client-only"></a>Кнопки операций диалогового окна (только для клиента VS)

- Убедитесь, что кнопки операции расположены в следующем порядке: **ОК**, **Отмена**, **Применить**.

- Убедитесь, что кнопки **ОК** и **Отмена** имеют стандартный размер: 75x23 пикселей.

- Убедитесь, что кнопки **ОК** и **Отмена** имеют одинаковый размер, независимо от длины строки.

- Если для кнопки метка на кнопке операции требуется, чтобы кнопка была шире стандартной, убедитесь, что соответствующая кнопка **отмены** имеет равный размер.

- Убедитесь, что между кнопками и связанными элементами управления имеется 6-пиксельное заполнение.

- Убедитесь, что кнопки **ОК** и **Отмена** не имеют назначенных клавиш (клавиши доступа, определенные подчеркнутой буквой).

- Убедитесь, что на одной кнопке (обычно **ОК**) фокус установлен по умолчанию.

- Убедитесь, что **ESC** отменяет диалоговое окно

- Убедитесь, что клавиша **Ввод** выполняет кнопку по умолчанию, если фокус не находится в элементе управления, обрабатывающем ввод.

- Убедитесь, что кнопки **ОК** и **Отмена** расположены в правом нижнем углу диалогового окна. В редких исключениях их можно разложить по вертикали в правом верхнем углу.

- Убедитесь, что вертикальная конфигурация используется только в том случае, если другие кнопки расположены по горизонтали в диалоговом окне.

### <a name="control-standards"></a>Стандарты управления

#### <a name="general"></a>Общие сведения

- Убедитесь, что, по возможности, существуют хорошие значения по умолчанию для ускорения взаимодействия с пользователем и направления пользователей к надежному или общему результату.

- Убедитесь, что стандартные элементы управления ведут себя одинаково, чтобы пользователи знали, что произойдет на основе более раннего опыта.

#### <a name="label-controls"></a>Элементы управления Label

- Убедитесь, что каждый элемент управления имеет метку и что каждая метка визуально связана с элементом управления (обычно в пределах диапазона 4-6 пикселей) и ближе к соответствующему элементу управления, чем к другим элементам управления.

- Убедитесь, что метки расположены слева от левого края элемента управления, если они расположены сверху и центрированы по горизонтали, так что базовый план метки выровнен с базовой линией входного текста, если располагается слева.

- Убедитесь, что если несколько элементов управления с накоплением и ввода расположены слева от элемента управления, метки остаются слева и равны от края диалогового окна, никогда не записываются вправо и равные расстояния от элементов управления. Пары должны быть распределены равномерно, если для них не требуется дополнительное пространство для группирования.

#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Элементы управления вводом (текстовые поля и поля со списком)

- Убедитесь, что при использовании шрифта среды по умолчанию высота отображаемых текстовых полей, полей со списком и кнопок составляет 23 пикселя.

- Если используется текст подсказки, убедитесь, что для цвета задано `Environment.ControlEditHintText` Использование службы цветов.

- Если поле является обязательным полем, которое должно быть идентифицировано таким образом, проверьте следующее:

  - что фон имеет значение `Environment.ControlEditRequiredBackground` , а для переднего плана — значение `Environment.ControlEditRequiredHintText`

  - наличие текста подсказки в элементе управления, который отображается как **" \<Required> "**

#### <a name="button-controls"></a>Элементы управления "Кнопка"

- Убедитесь, что кнопки имеют минимальный размер в 75x23 пикселях, если не используется более длинный текст.

- Убедитесь, что кнопки имеют левое и правое поля 3-5 пикселей, а также заполнение для содержимого.

- Можно использовать маленькую квадратную кнопку с многоточием **[...]** вместо кнопки **[Browse...]** (или аналогичной функциональности). Если используется, убедитесь, что кнопка имеет размер 23x23.

- Если в диалоговом окне имеется несколько кнопок **[Browse...]** , убедитесь, что для всех используется сокращенная версия (только многоточие **[...]**).

- Убедитесь, что кнопки с многоточием **[...]** не имеют назначенных клавиш. Когда фокус находится рядом с элементом управления вводом, одна вкладка должна переместить фокус на кнопку с многоточием.

- Убедитесь, что кнопки, команды и ссылки на команды, которые запускают дополнительный пользовательский интерфейс, который захватывает больше вводимых пользователем данных, должны заканчиваться многоточием **[...]**.

#### <a name="hyperlinks"></a>Гиперссылки

- Убедитесь, что элемент управления "гиперссылка" не мигает красным цветом в активном состоянии. Это признак того, что служба цветов не используется

- Убедитесь, что используются следующие цвета VS:

  - `Environment.ControlLinkText`

  - `Environment.ControlLinkTextHover`

  - `Environment.ControlLinkTextPressed`

- Убедитесь, что гиперссылки отображаются синим цветом без подчеркивания, если они не внедрены в абзац.

#### <a name="check-boxes"></a>Флажки

- Если флажок имеет многострочный текст, убедитесь, что поле выровнено с первой строкой текста, не выровненной по вертикали по всем строкам.

- Убедитесь, что флажки всегда указывают на двоичный вариант и не находят пользователь или не открывали новые окна или страницы.

- Если флажок представляет параметр, связанный с элементом управления вводом, убедитесь, что он расположен слева, и очень близко под этим элементом управления, чтобы указать его связь.

- Убедитесь, что флажок **никогда** не используется в качестве средства для включения всего содержимого диалогового окна или страницы.

#### <a name="group-boxes"></a>Поля группы

- Убедитесь, что в диалоговом окне не содержится одно поле группы, содержащее все содержимое диалогового окна.

- Убедитесь, что в каждом поле группы есть по крайней мере два элемента управления.

- В диалоговом окне редко должно быть больше двух полей группы.

- Убедитесь в отсутствии вложенных полей группы.

### <a name="icons"></a>Значки

- Убедитесь, что значки отображаются правильно, когда в темной теме.

- Убедитесь, что все значки основаны на основных понятиях.

- Убедитесь, что каждый значок является отдельным, простым в распознавании и не содержит более двух концепций (без модификатора состояния или языка).

- Убедитесь, что базовый значок отображается по центру в пределах пространства.

- Убедитесь, что все значки отображаются в режиме высокая контрастность.

- Убедитесь, что любой используемый цвет соответствует стандартам использования цвета.

- Убедитесь в отсутствии ореолов (границ) вокруг значков. (Если он есть, Halo должен соответствовать цвету фона соседнего пользовательского интерфейса).

### <a name="touch-enabled-ui"></a>Пользовательский интерфейс с поддержкой сенсорного ввода

- Убедитесь, что интерактивные элементы управления достаточно велики, чтобы их можно было легко изменить — минимальный размер **23x23 пикселей** .

- Убедитесь, что наиболее часто используемые элементы управления имеют размер не менее **40x40 пикселей** .

- Убедитесь, что в интерактивных элементах управления есть по крайней мере **5 пикселей интервала** между ними.
