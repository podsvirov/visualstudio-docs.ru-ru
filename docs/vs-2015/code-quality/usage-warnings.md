---
title: Предупреждения об использовании | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bd1e993723d3ef1779eb3a23e19fedd081b6a6d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603512"
---
# <a name="usage-warnings"></a>предупреждения использования
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предупреждения об использовании поддерживают правильное использование .NET Framework.

## <a name="in-this-section"></a>в этом разделе

|Правило|Описание|
|----------|-----------------|
|[CA1801. Проверьте неиспользуемые параметры](../code-quality/ca1801-review-unused-parameters.md)|Сигнатура метода включает параметр, не использующийся в основной части метода.|
|[CA1806. Не игнорируйте результаты метода](../code-quality/ca1806-do-not-ignore-method-results.md)|Создается, но никогда не используется новый объект, либо вызывается метод, который создает и возвращает новую строку, и такая новая строка никогда не используется, либо метод COM или P/Invoke возвращает HRESULT или код ошибки, который никогда не используется.|
|[CA1816. Вызов GC.SuppressFinalize должен осуществляться правильно](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Метод, являющийся реализацией Dispose, не вызывает GC.SuppressFinalize, либо метод, не являющийся реализацией Dispose, вызывает GC.SuppressFinalize, либо метод вызывает GC.SuppressFinalize и передает что-либо другое (Me в Visual Basic).|
|[CA2200. Повторно порождайте исключения для сохранения сведений стека](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Создается повторное исключение, и в инструкции Throw явно указывается исключение. Если исключение создается повторно путем указания исключения в инструкции Throw, то список вызовов методов между исходным методом, вызвавшим исключение, и текущим методом будет потерян.|
|[CA2201. Не порождайте исключения зарезервированных типов](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Это делает исходную ошибку трудной для обнаружения и отладки.|
|[CA2202. Не ликвидируйте объекты несколько раз](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Реализация метода содержит пути кода, которые могли стать причиной многократного вызова метода System.IDisposable.Dispose или эквивалентного метода Dispose (например, метода Close() для некоторых типов) для одного и того же объекта.|
|[CA2204. Литералы должны иметь правильное правописание](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Литеральная строка в теле метода содержит одно или несколько слов, не распознаваемых библиотекой системы проверки орфографии Майкрософт.|
|[CA2205. Используйте управляемые эквиваленты Win32 API](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Определен метод вызова неуправляемого кода, и в библиотеке классов .NET Framework существует метод с аналогичной функциональностью.|
|[CA2207. Используйте встроенную инициализацию статических полей типов значений](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Тип значения объявляет явный статический конструктор. Чтобы устранить нарушение данного правила, выполните инициализацию всех статических данных при их объявлении и удалите статический конструктор.|
|[CA2208. Правильно создавайте экземпляры исключений аргументов](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Вызывается конструктор по умолчанию (без параметров), принадлежащий к типу исключения ArgumentException или унаследованный от него, или неправильный аргумент строки передается параметризованному конструктору, принадлежащему к типу исключения ArgumentException или унаследованному от него.|
|[CA2211. Поля, не являющиеся константами, не должны быть видимыми](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Для статических полей, которые не являются константными и доступными только для чтения, невозможно обеспечить потокобезопасность. Доступ к такому полю должен быть тщательно контролируемым и требует расширенных методов программирования для синхронизации доступа к объекту класса.|
|[CA2212. Не помечайте обслуживаемые компоненты с помощью WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Метод в типе, который наследует от System. EnterpriseServices. ServicedComponent, отмечается атрибутом System. Web. Services. WebMethodAttribute. Так как атрибут WebMethodAttribute и метод ServicedComponent имеют разное поведение и предъявляют конфликтующие требования к контексту и потоку транзакций, в некоторых сценариях поведение метода будет неправильным.|
|[CA2213. Следует высвобождать высвобождаемые поля](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Тип, реализующий System.IDisposable, объявляет поля, принадлежащие к типам, которые также реализуют IDisposable. Метод Dispose поля не вызывается методом Dispose объявляющего типа.|
|[CA2214. Не вызывайте переопределяемые методы в конструкторах](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Если конструктор вызывает виртуальный метод, возможно, конструктор для экземпляра, который вызывает метод, не выполнялся.|
|[CA2215. Метод Dispose должен вызывать базовый класс Dispose](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Если тип наследуется от удаляемого типа, он должен вызвать метод Dispose базового типа из собственного метода Dispose.|
|[CA2216. Высвобождаемые типы должны объявлять методы завершения](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Тип, реализующий System. IDisposable и имеющий поля, предлагающие использование неуправляемых ресурсов, не реализует метод завершения, как описано в Object. Finalize.|
|[CA2217. Не помечайте перечисляемые типы с помощью FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Перечисление, видимое извне, помечается атрибутом FlagsAttribute и имеет одно или несколько значений, не являющихся степенями двух, или сочетанием других определенных значений в перечислении.|
|[CA2218. Переопределяйте GetHashCode при переопределении Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode возвращает значение на основе текущего экземпляра, используемое для алгоритмов хэширования и структур данных, таких как хэш-таблица. Два равных объекта, принадлежащие к одному и тому же типу, должны возвращать один и тот же хэш-код.|
|[CA2219. В предложениях с исключениями не должны порождаться исключения](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Если исключение создается в предложении finally или fault, новое исключение скрывает активное исключение. Если исключение создается в предложении filter, среда выполнения перехватывает исключение без оповещения. Это делает исходную ошибку трудной для обнаружения и отладки.|
|[CA2220. Методы завершения должны вызывать метод завершения базового класса](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Финализация должна распространятся посредством иерархии наследования. Для этого типы должны вызывать свой метод Finalize базового класса из собственного метода Finalize.|
|[CA2221. Методы завершения должны быть защищенными](../code-quality/ca2221-finalizers-should-be-protected.md)|В методах завершения должен использоваться модификатор доступа из семейства.|
|[CA2222. Не уменьшайте видимость наследуемого члена](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Не следует изменять модификатор доступа для унаследованных членов. Если сделать унаследованный член закрытым, то доступ вызывающих объектов к реализации метода базового класса все равно не будет запрещен.|
|[CA2223. Члены должны различаться не только возвращаемым типом](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Среда CLR позволяет использовать возвращаемые типы для различения совпадающих в остальном членов, однако эта функция не входит в спецификацию CLS и поддерживается не всеми языками программирования .NET.|
|[CA2224. Переопределяйте Equals при перегрузке оператора равенства](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Открытый тип реализует оператор равенства, но не переопределяет Object. Equals.|
|[CA2225. Для перегрузок операторов существуют варианты с именами](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Обнаружена перегрузка оператора, однако не найден ожидаемый именованный альтернативный метод. Именованный альтернативный элемент предоставляет доступ к тем же функциональным возможностям, что и оператор, и предоставляется разработчикам, которые запрограммированы на языках, не поддерживающих перегруженные операторы.|
|[CA2226. Перегрузки операторов должны быть симметричными](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Тип реализует оператор равенства или неравенства и не реализует противоположный оператор.|
|[CA2227. Свойства, возвращающие коллекции, должны быть доступными только для чтения](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Свойство коллекции, допускающее запись, позволяет пользователю заменять одну коллекцию другой. Свойство только для чтения предотвращает замену коллекции, но по-прежнему допускает установку, настройку отдельных членов.|
|[CA2228. Не поставляйте предварительные форматы ресурсов](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Файлы ресурсов, созданные с помощью предварительных версий .NET Framework, могут не использоваться поддерживаемыми версиями .NET Framework.|
|[CA2229. Реализуйте конструкторы сериализации](../code-quality/ca2229-implement-serialization-constructors.md)|Чтобы устранить нарушение этого правила, реализуйте конструктор сериализации. Для запечатанного класса конструктор должен быть закрытым, а в иных случаях — защищенным.|
|[CA2230. Используйте параметры для аргументов переменной](../code-quality/ca2230-use-params-for-variable-arguments.md)|Открытый или защищенный тип содержит открытый или защищенный метод, который использует соглашение о вызовах VarArgs вместо ключевого слова params.|
|[CA2231. Перегрузите оператор равенства на переопределяющем типе ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Тип значения переопределяет Object.Equals, но не реализует оператор равенства.|
|[CA2232. Отметьте точки входа Windows Forms меткой STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Атрибут STAThreadAttribute указывает, что потоковой моделью COM для приложения является однопотоковое подразделение. Данный атрибут должен находиться в точке входа любого приложения, использующего Windows Forms; если он отсутствует, компоненты Windows могут работать неправильно.|
|[CA2233. В операциях не должно быть переполнений](../code-quality/ca2233-operations-should-not-overflow.md)|Арифметические операции не следует выполнять без предварительной проверки операндов, чтобы убедиться, что результат операции выходит за пределы диапазона возможных значений для используемых типов данных.|
|[CA2234. Передавайте объекты System.Uri вместо строк](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Вызывается метод, имеющий параметр строки, имя которого содержит uri, URI, urn, URN, url или URL.  Объявляющий тип метода содержит соответствующую перегрузку метода, которая имеет параметр System.Uri.|
|[CA2235. Пометьте все несериализуемые поля](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Экземпляр поля несериализуемого типа объявлен в сериализуемом типе.|
|[CA2236. Вызывайте методы базового класса для типов ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Чтобы устранить нарушение этого правила, вызовите метод базового типа GetObjectData или конструктор сериализации из соответствующего метода производного типа или конструктора.|
|[CA2237. Пометьте типы ISerializable атрибутом SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Для распознавания общеязыковой средой выполнения в качестве сериализуемых типы должны быть помечены атрибутом SerializableAttribute, даже если тип использует пользовательскую подпрограммы сериализации посредством реализации интерфейса ISerializable.|
|[CA2238. Правильно реализуйте методы сериализации](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Метод, обрабатывающий событие сериализации, не имеет правильной сигнатуры, типа возвращаемого значения или отображения.|
|[CA2239. Обеспечьте наличие методов десериализации в необязательных полях](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Тип имеет поле, помеченное атрибутом System. Runtime. Serialization. OptionalFieldAttribute, а тип не предоставляет методы обработки событий отмены сериализации.|
|[CA2240. Правильно реализуйте ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)|Чтобы устранить нарушение этого правила, сделайте метод GetObjectData видимым и переопределяемым и убедитесь, что все поля экземпляра включены в процесс сериализации или явно помечены атрибутом NonSerializedAttribute.|
|[CA2241. Задайте правильные аргументы для методов форматирования](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Аргумент формата, переданный в System. String. Format, не содержит элемент форматирования, соответствующий аргументу объекта, или наоборот.|
|[CA2242. Правильно выполняйте проверку NaN](../code-quality/ca2242-test-for-nan-correctly.md)|Это выражение проверяет значение на соответствие Single.Nan или Double.Nan. Используйте Single.IsNan(Single) или Double.IsNan(Double) для проверки значения.|
|[CA2243. Синтаксический разбор строковых литералов должен осуществляться правильно](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Параметр строкового литерала атрибута не анализируется правильно для URL-адреса, идентификатора GUID или версии.|
