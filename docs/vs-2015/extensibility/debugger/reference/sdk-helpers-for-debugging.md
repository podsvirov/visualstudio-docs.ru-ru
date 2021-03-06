---
title: Вспомогательные методы SDK для отладки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3296613ffbe3148caa04989dfc9d609334b4c200
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843400"
---
# <a name="sdk-helpers-for-debugging"></a>Вспомогательные пакеты SDK для отладки
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Эти функции и объявления являются глобальными вспомогательными функциями для реализации модулей отладки, средств оценки выражений и поставщиков символов в C++.  
  
> [!NOTE]
> В настоящее время нет управляемых версий этих функций и объявлений.  
  
## <a name="overview"></a>Overview  
 Для использования в Visual Studio средств отладки, средств оценки выражений и поставщиков символов они должны быть зарегистрированы. Для этого необходимо задать подразделы и записи реестра, в противном случае называемые метриками настройки. Следующие глобальные функции предназначены для упрощения процесса обновления этих метрик. Сведения о компоновке каждого подраздела реестра, обновляемого этими функциями, см. в разделе о расположениях в реестре.  
  
## <a name="general-metric-functions"></a>Общие функции метрик  
 Это общие функции, используемые механизмами отладки. Ниже приведены специализированные функции для средств оценки выражений и поставщиков символов.  
  
### <a name="getmetric-method"></a>Методических метрик  
 Извлекает значение метрики из реестра.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Параметр|Description|  
|---------------|-----------------|  
|псзмачине|окне Имя потенциального удаленного компьютера, регистр которого будет записан ( `NULL` то есть локальный компьютер).|  
|псзтипе|окне Один из типов метрик.|  
|гуидсектион|окне Идентификатор GUID определенного подсистемы, оценщика, исключения и т. д. Указывает подраздел под типом метрики для определенного элемента.|  
|псзметрик|окне Получаемая метрика. Соответствует конкретному имени значения.|  
|пдввалуе|окне Место хранения значения метрики. Существует несколько разновидностей параметра Metric, которые могут возвращать DWORD (как в этом примере), BSTR, GUID или массив идентификаторов GUID.|  
|псзалтрут|окне Альтернативный корень реестра для использования. Задайте значение, `NULL` чтобы использовать значение по умолчанию.|  
  
### <a name="setmetric-method"></a>Метод Сетметрик  
 Задает указанное значение метрики в реестре.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Параметр|Description|  
|---------------|-----------------|  
|псзтипе|окне Один из типов метрик.|  
|гуидсектион|окне Идентификатор GUID определенного подсистемы, оценщика, исключения и т. д. Указывает подраздел под типом метрики для определенного элемента.|  
|псзметрик|окне Получаемая метрика. Соответствует конкретному имени значения.|  
|дввалуе|окне Место хранения значения в метрике. Существует несколько разновидностей Сетметрик, которые могут хранить DWORD (в этом примере), BSTR, GUID или массив идентификаторов GUID.|  
|фусерспеЦифик|окне Значение TRUE, если метрика зависит от пользователя и должна быть записана в куст пользователя, а не в куст локального компьютера.|  
|псзалтрут|окне Альтернативный корень реестра для использования. Задайте значение, `NULL` чтобы использовать значение по умолчанию.|  
  
### <a name="removemetric-method"></a>Метод Ремовеметрик  
 Удаляет указанную метрику из реестра.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Параметр|Description|  
|---------------|-----------------|  
|псзтипе|окне Один из типов метрик.|  
|гуидсектион|окне Идентификатор GUID определенного подсистемы, оценщика, исключения и т. д. Указывает подраздел под типом метрики для определенного элемента.|  
|псзметрик|окне Удаляемая метрика. Соответствует конкретному имени значения.|  
|псзалтрут|окне Альтернативный корень реестра для использования. Задайте значение, `NULL` чтобы использовать значение по умолчанию.|  
  
### <a name="enummetricsections-method"></a>Метод Енумметриксектионс  
 Перечисляет различные разделы метрик в реестре.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Параметр|Description|  
|---------------|-----------------|  
|псзмачине|окне Имя потенциального удаленного компьютера, регистр которого будет записан ( `NULL` то есть локальный компьютер).|  
|псзтипе|окне Один из типов метрик.|  
|рггуидсектионс|[вход, выход] Предварительно выделенный массив идентификаторов GUID для заполнения.|  
|пдвсизе|окне Максимальное число идентификаторов GUID, которые могут храниться в `rgguidSections` массиве.|  
|псзалтрут|окне Альтернативный корень реестра для использования. Задайте значение, `NULL` чтобы использовать значение по умолчанию.|  
  
## <a name="expression-evaluator-functions"></a>Функции оценки выражений  
  
|Компонент|Description|  
|--------------|-----------------|  
|жетиметрик|Извлекает значение метрики из реестра.|  
|сетиметрик|Задает указанное значение метрики в реестре.|  
|ремовиеметрик|Удаляет указанную метрику из реестра.|  
|GetEEMetricFile|Возвращает имя файла из указанной метрики и загружает его, возвращая содержимое файла в виде строки.|  
  
## <a name="exception-functions"></a>Функции исключения  
  
|Компонент|Description|  
|--------------|-----------------|  
|жетексцептионметрик|Извлекает значение метрики из реестра.|  
|сетексцептионметрик|Задает указанное значение метрики в реестре.|  
|ремовиксцептионметрик|Удаляет указанную метрику из реестра.|  
|ремовеаллексцептионметрикс|Удаляет все метрики исключений из реестра.|  
  
## <a name="symbol-provider-functions"></a>Функции поставщика символов  
  
|Компонент|Description|  
|--------------|-----------------|  
|жетспметрик|Извлекает значение метрики из реестра.|  
|сетспметрик|Задает указанное значение метрики в реестре.|  
|ремовеспметрик|Удаляет указанную метрику из реестра.|  
  
## <a name="enumeration-functions"></a>Функции перечисления  
  
|Компонент|Description|  
|--------------|-----------------|  
|енумметриксектионс|Перечисляет все метрики для указанного типа метрики.|  
|енумдебуженгине|Перечисляет зарегистрированные модули отладки.|  
|EnumEEs|Перечисляет зарегистрированные вычислители выражений.|  
|енумексцептионметрикс|Перечисляет все метрики исключений.|  
  
## <a name="metric-definitions"></a>Определения метрик  
 Эти определения можно использовать для предопределенных имен метрик. Имена соответствуют различным разделам реестра и именам значений, и все они определены как строки расширенных символов: например, `extern LPCWSTR metrictypeEngine` .  
  
|Стандартные типы метрик|Описание: базовый ключ для....|  
|-----------------------------|---------------------------------------|  
|метриктипингине|Все метрики модуля отладки.|  
|метриктипепортсупплиер|Все метрики поставщика портов.|  
|метриктипиксцептион|Все метрики исключений.|  
|метрикттипиикстенсион|Все расширения средства оценки выражений.|  
  
|Свойства модуля отладки|Description|  
|-----------------------------|-----------------|  
|метрикаддрессбп|Задайте значение ненулевой, чтобы указать поддержку для точек останова адреса.|  
|метрикалвайслоадлокал|Задайте значение ненулевой, чтобы всегда загружать модуль отладки локально.|  
|метриклоадиндебугжеесессион|НЕ ИСПОЛЬЗУЕТСЯ|  
|метриклоадедбидебугжее|Задайте значение ненулевой, чтобы указать, что ядро отладки всегда будет загружаться вместе с или отлаживаемой программой.|  
|метрикаттач|Задайте значение ненулевой, чтобы указать поддержку вложения в существующие программы.|  
|метриккаллстаккбп|Задайте значение ненулевой, чтобы указать поддержку точек останова в стеке вызовов.|  
|метриккондитионалбп|Задайте значение ненулевой, чтобы указать поддержку для параметра условных точек останова.|  
|метрикдатабп|Задайте значение ненулевой, чтобы указать поддержку параметра точек останова при изменениях в данных.|  
|метрикдисассембли|Задайте значение ненулевой, чтобы указать поддержку для производства списка дизассемблированного кода.|  
|метрикдумпвритинг|Задайте значение ненулевой, чтобы указать поддержку записи дампа (дамп памяти на устройство вывода).|  
|метриценк|Задайте значение ненулевой, чтобы указать поддержку для параметра "изменить и продолжить". **Примечание.**  Настраиваемый модуль отладки никогда не должен задавать это значение или всегда должен иметь значение 0.|  
|метрицексцептионс|Задайте значение ненулевой, чтобы указать поддержку исключений.|  
|метрикфунктионбп|Задайте значение ненулевой, чтобы указать поддержку именованных точек останова (точки останова, которые прерывать при вызове определенного имени функции).|  
|метричиткаунтбп|Задайте значение ненулевой, чтобы указать поддержку для параметра точки останова точки попадания (точки останова, которые запускаются только после определенного числа раз).|  
|метрикжитдебуг|Задайте значение ненулевой, чтобы указать поддержку JIT-отладки (отладчик запускается при возникновении исключения в работающем процессе).|  
|метрикмемори|НЕ ИСПОЛЬЗУЕТСЯ|  
|метрикпортсупплиер|Присвойте этому идентификатору CLSID поставщика порта, если он реализован.|  
|метрикрегистерс|НЕ ИСПОЛЬЗУЕТСЯ|  
|метриксетнекстстатемент|Задайте значение ненулевой, чтобы указать поддержку для установки следующего оператора (который пропускает выполнение промежуточных инструкций).|  
|метриксуспендсреад|Задайте значение ненулевой, чтобы указать поддержку приостановки выполнения потока.|  
|метрикварнифносимболс|Задайте значение ненулевой, чтобы указать, что пользователь должен получать уведомления при отсутствии символов.|  
|метрикпрогрампровидер|Задайте значение идентификатора CLSID поставщика программы.|  
|метрикалвайслоадпрогрампровидерлокал|Задайте значение ненулевой, чтобы указать, что поставщик программы всегда должен загружаться локально.|  
|метриценгинеканватчпроцесс|Задайте значение ненулевой, чтобы указать, что модуль отладки будет отслеживать события процесса вместо поставщика программы.|  
|метрикремотедебуггинг|Задайте значение ненулевой, чтобы указать поддержку удаленной отладки.|  
|метриценкусенативебуилдер|Задайте значение ненулевой, чтобы указать, что диспетчеру "изменить и продолжить" следует использовать encbuild.dll модуля отладки для сборки для "изменить и продолжить". **Примечание.**  Настраиваемый модуль отладки никогда не должен задавать это значение или всегда должен иметь значение 0.|  
|metricLoadUnderWOW64|Задайте для этого параметра значение ненулевой, чтобы указать, что при отладке 64-разрядного процесса ядро отладки должно быть загружено в отлаживаемый процесс в режиме WOW. в противном случае ядро отладки будет загружено в процесс Visual Studio (который выполняется в эмуляторе WOW64).|  
|metricLoadProgramProviderUnderWOW64|Задайте значение ненулевой, чтобы указать, что поставщик программы должен быть загружен в отлаживаемый процесс при отладке 64-разрядного процесса в режиме WOW; в противном случае он будет загружен в процесс Visual Studio.|  
|метрикстопонексцептионкроссингманажедбаундари|Задайте для этого параметра значение ненулевой, чтобы указать, что процесс должен останавливаться при возникновении необработанного исключения на границах управляемого и неуправляемого кода.|  
|метрикаутоселектприорити|Задайте для этого параметра значение приоритет автоматического выбора модуля отладки (более высокие значения равны более высокому приоритету).|  
|метрикаутоселектинкомпатиблелист|Раздел реестра, содержащий записи, указывающие идентификаторы GUID для отладочных модулей, которые должны игнорироваться при автоматическом выборе. Эти записи представляют собой число (0, 1, 2 и т. д.) с идентификатором GUID, выраженным в виде строки.|  
|метриЦинкомпатиблелист|Раздел реестра, содержащий записи, которые указывают идентификаторы GUID для отладочных модулей, несовместимых с этим модулем отладки.|  
|метрикдисаблежитоптимизатион|Задайте для этого параметра значение ненулевой, чтобы указать, что JIT-оптимизация (для управляемого кода) должна быть отключена во время отладки.|  
  
|Свойства средства оценки выражений|Description|  
|-------------------------------------|-----------------|  
|метриценгине|Он содержит количество модулей отладки, которые поддерживают указанный средство оценки выражений.|  
|метрикпрелоадмодулес|Задайте значение ненулевой, чтобы указать, что модули должны быть предварительно загружены при запуске средства оценки выражений для программы.|  
|метриксисобжектнаме|Присвойте ему имя объекта "this".|  
  
|Свойства расширения средства оценки выражений|Description|  
|-----------------------------------------------|-----------------|  
|метрицекстенсиондлл|Имя библиотеки DLL, которая поддерживает это расширение.|  
|метрицекстенсионрегистерссуппортед|Список поддерживаемых регистров.|  
|метрицекстенсионрегистерсентрипоинт|Точка входа для доступа к регистрам.|  
|метрицекстенсионтипессуппортед|Список поддерживаемых типов.|  
|метрицекстенсионтипесентрипоинт|Точка входа для доступа к типам.|  
  
|Свойства поставщика порта|Description|  
|------------------------------|-----------------|  
|метрикпортпиккерклсид|Идентификатор CLSID средства выбора порта (диалоговое окно, которое пользователь может использовать для выбора портов и добавления портов для использования при отладке).|  
|метрикдисалловусерентередпортс|Ненулевое значение, если порты, введенные пользователем, не могут быть добавлены к поставщику порта (это делает диалоговое окно "Выбор порта" в основном только для чтения).|  
|метрикпидбасе|Базовый идентификатор процесса, используемый поставщиком порта при выделении идентификаторов процессов.|  
  
|Предопределенные типы хранилищ SP|Description|  
|-------------------------------|-----------------|  
|сторетипефиле|Символы хранятся в отдельном файле.|  
|сторетипеметадата|Символы хранятся в виде метаданных в сборке.|  
  
|Прочие свойства|Description|  
|------------------------------|-----------------|  
|метрикшовнонусеркоде|Задайте для этого параметра значение ненулевой, чтобы отобразить непользовательский код.|  
|метрикжустмикодестеппинг|Задайте для этого параметра значение ненулевой, чтобы указать, что пошаговое выполнение может происходить только в пользовательском коде.|  
|метрикклсид|CLSID для объекта определенного типа метрики.|  
|metricName|Понятное имя для объекта определенного типа метрики.|  
|метриклангуаже|Имя языка.|  
  
## <a name="registry-locations"></a>Расположения реестра  
 Метрики считываются из реестра и записываются в реестр, в частности в `VisualStudio` подразделе.  
  
> [!NOTE]
> В большинстве случаев метрики будут записываться в ключ HKEY_LOCAL_MACHINE. Однако иногда HKEY_CURRENT_USER будет ключом назначения. Дбгметрик. LIB обрабатывает оба ключа. При получении метрики сначала выполняется поиск HKEY_CURRENT_USER, затем HKEY_LOCAL_MACHINE. При установке метрики параметр указывает, какой ключ верхнего уровня следует использовать.  
  
 *[раздел реестра]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[корень версии]*\  
  
 *[корень метрики]*\  
  
 *[тип метрики]*\  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[раздел реестра]*|`HKEY_CURRENT_USER` или `HKEY_LOCAL_MACHINE`.|  
|*[корень версии]*|Версия Visual Studio (например,, `7.0` `7.1` или `8.0` ). Однако этот корень можно также изменить с помощью параметра **/рутсуффикс** , чтобы **devenv.exe**. Для VSIP этот модификатор обычно является **exp**, поэтому корень версии будет иметь вид, например, 8.0 exp.|  
|*[корень метрики]*|Это может быть `AD7Metrics` или `AD7Metrics(Debug)` , в зависимости от того, используется ли отладочная версия дбгметрик. lib. **Примечание.**  Независимо от того, используется ли дбгметрик. lib, это соглашение об именовании следует соблюдать, если имеются различия между версиями отладки и выпуска, которые должны быть отражены в реестре.|  
|*[тип метрики]*|Тип записываемой метрики: `Engine` , `ExpressionEvaluator` , `SymbolProvider` и т. д. Все они определяются как в дбгметрик. h как `metricTypeXXXX` , где `XXXX` — это имя конкретного типа.|  
|*шкал*|Имя записи, которой должно быть присвоено значение, чтобы задать метрику. Фактическая организация метрик зависит от типа метрики.|  
|*[значение метрики]*|Значение, присваиваемое метрике. Тип, который должен иметь значение (строка, число и т. д.), зависит от метрики.|  
  
> [!NOTE]
> Все идентификаторы GUID хранятся в формате `{GUID}` . Например, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Отладчики  
 Ниже приведена организация метрик модулей отладки в реестре. `Engine` — Это имя типа метрики для модуля отладки и соответствующее *[тип метрики]* в приведенном выше поддереве реестра.  
  
 `Engine`\  
  
 *[идентификатор GUID обработчика]*\  
  
 `CLSID` = *[GUID класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 `PortSupplier`\  
  
 `0` = *[GUID поставщика портов]*  
  
 `1` = *[GUID поставщика портов]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[идентификатор GUID обработчика]*|Идентификатор GUID модуля отладки.|  
|*[GUID класса]*|Идентификатор GUID класса, реализующего этот модуль отладки.|  
|*[GUID поставщика портов]*|Идентификатор GUID поставщика порта, если он есть. Многие модули отладки используют поставщика портов по умолчанию, поэтому не указывайте собственного поставщика. В этом случае подраздел `PortSupplier` будет отсутствовать.|  
  
### <a name="port-suppliers"></a>Поставщики портов  
 Ниже приведена организация метрик поставщика портов в реестре. `PortSupplier` — Это имя типа метрики для поставщика порта и соответствует *[типу метрики]*.  
  
 `PortSupplier`\  
  
 *[GUID поставщика портов]*\  
  
 `CLSID` = *[GUID класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[GUID поставщика портов]*|Идентификатор GUID поставщика порта|  
|*[GUID класса]*|Идентификатор GUID класса, реализующего этот поставщик порта|  
  
### <a name="symbol-providers"></a>Поставщики символов  
 Ниже приведена организация метрик поставщиков символов в реестре. `SymbolProvider` имя типа метрики для поставщика символов и соответствует *[типу метрики]*.  
  
 `SymbolProvider`\  
  
 *[GUID поставщика символов]*\  
  
 `file`\  
  
 `CLSID` = *[GUID класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 `metadata`\  
  
 `CLSID` = *[GUID класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[GUID поставщика символов]*|Идентификатор GUID поставщика символов|  
|*[GUID класса]*|Идентификатор GUID класса, реализующего этот поставщик символов|  
  
### <a name="expression-evaluators"></a>Вычислители выражений  
 Ниже приведена организация метрик оценки выражений в реестре. `ExpressionEvaluator` имя типа метрики для средства оценки выражений и соответствует *[типу метрики]*.  
  
> [!NOTE]
> Тип метрики для `ExpressionEvaluator` не определен в дбгметрик. h, так как предполагается, что все изменения метрики для оценивающих выражений будут проходить через соответствующие функции метрик средства оценки выражений (макет `ExpressionEvaluator` подраздела довольно сложен, поэтому подробности скрыты в дбгметрик. lib).  
  
 `ExpressionEvaluator`\  
  
 *[GUID языка]*\  
  
 *[идентификатор GUID поставщика]*\  
  
 `CLSID` = *[GUID класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 `Engine`\  
  
 `0` = *[GUID модуля отладки]*  
  
 `1` = *[GUID модуля отладки]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[GUID языка]*|Идентификатор GUID языка|  
|*[идентификатор GUID поставщика]*|Идентификатор GUID поставщика|  
|*[GUID класса]*|Идентификатор GUID класса, реализующего этот оценщик выражений|  
|*[GUID модуля отладки]*|Идентификатор GUID модуля отладки, с которым работает средство оценки выражений|  
  
### <a name="expression-evaluator-extensions"></a>Расширения средства оценки выражений  
 Ниже приведена организация метрик расширения средства оценки выражений в реестре. `EEExtensions` имя типа метрики для расширений средства оценки выражений и соответствует *[типу метрики]*.  
  
 `EEExtensions`\  
  
 *[GUID расширения]*\  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[GUID расширения]*|Идентификатор GUID расширения средства оценки выражений|  
  
### <a name="exceptions"></a>Исключения  
 Ниже приведена организация метрик исключений в реестре. `Exception` имя типа метрики для исключений и соответствует *[типу метрики]*.  
  
 `Exception`\  
  
 *[GUID модуля отладки]*\  
  
 *[типы исключений]*\  
  
 *об*\  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 *об*\  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[GUID модуля отладки]*|Идентификатор GUID модуля отладки, который поддерживает исключения.|  
|*[типы исключений]*|Общий заголовок для подраздела, определяющего класс исключений, которые могут быть обработаны. Типичными именами являются **исключения C++**, **исключения Win32**, **исключения среды**CLR и **встроенные проверки времени выполнения**. Эти имена также используются для обнаружения определенного класса исключений для пользователя.|  
|*об*|Имя исключения: например, **_com_error** или **break-Control**. Эти имена также используются для распознавания определенного исключения для пользователя.|  
  
## <a name="requirements"></a>Требования  
 Эти файлы находятся в [!INCLUDE[vs_dev10_ext](../../../includes/vs-dev10-ext-md.md)] каталоге установки SDK (по умолчанию *[диск]* \Program Files\Microsoft Visual Studio 2010 SDK \\ ).  
  
 Заголовок: инклудес\дбгметрик.х  
  
 Библиотека: libs\ad2de.lib, либс\дбгметрик.либ  
  
## <a name="see-also"></a>См. также:  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
