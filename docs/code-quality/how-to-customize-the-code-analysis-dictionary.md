---
title: Практическое руководство. Настройка словаря анализа кода
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1a50374a2603153cc7f4770a9aaf5ba72fbe007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "87453650"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Практическое руководство. Настройка словаря анализа кода

В анализе кода используется встроенный словарь для проверки идентификаторов в коде на наличие ошибок в написании, грамматическом случае и других соглашений об именовании руководств по проектированию .NET. Можно создать XML-файл пользовательского словаря для добавления, удаления или изменения терминов, сокращений и акронимов во встроенном словаре.

Например, предположим, что код содержал класс с именем **дуркноккер**. Анализ кода определяет имя как составное из двух слов: **двери** и **кноккер**. Затем он выдаст предупреждение о том, что **кноккер** не написан правильно. Чтобы принудительно выявить орфографию в анализе кода, можно добавить термин **кноккер** в пользовательский словарь.

## <a name="to-create-a-custom-dictionary"></a>Создание пользовательского словаря

Создайте файл с именем **CustomDictionary.xml**.

Определите пользовательские слова, используя следующую XML-структуру:

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Элементы пользовательского словаря

Поведение словаря анализа кода можно изменить, добавив термины в качестве внутреннего текста следующих элементов в пользовательском словаре:

- [Словари, слова/распознанное слово](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Словари, слова, нераспознанные или слова](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Dictionary/Words/устарело/Term [ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Dictionary/слова/составные/термы [ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Dictionary/Words/Дискретиксцептионс/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Словарь, акронимы, Касинжексцептионси и акронимы](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a> Словари, слова/распознанное слово

Чтобы включить термин в список терминов, идентифицируемых при анализе кода, добавьте термин в качестве внутреннего текста словаря, слова/распознанного элемента или слова. Термины в словарях, словах, распознанных и словах не учитывают регистр.

**Пример**

```xml
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>
```

Термины в словаре, словах и распознаваемых узлах применяются к следующим правилам анализа кода:

- [CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса](../code-quality/ca1701.md)

- [CA1702. Для сложных слов следует использовать правильный регистр](../code-quality/ca1702.md)

- [CA1703. Строки ресурса должны иметь правильное правописание](../code-quality/ca1703.md)

- [CA1704. Идентификаторы должны иметь правильное правописание](../code-quality/ca1704.md)

- [CA1709. Идентификаторы должны иметь правильное сочетание прописных и строчных букв](../code-quality/ca1709.md)

- [CA1726. Используйте предпочтительные термины](../code-quality/ca1726.md)

- [CA2204. Литералы должны иметь правильное правописание](../code-quality/ca2204.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Словари, слова, нераспознанные или слова

Чтобы исключить термин из списка терминов, идентифицируемых при анализе кода, добавьте термин, который следует исключить, в качестве внутреннего текста словаря или слов/нераспознанного элемента или слова. Термины в словарях, словах, нераспознанных и словах не учитывают регистр.

**Пример**

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>
```

Термины в словаре/словах/нераспознанные узлы применяются к следующим правилам анализа кода:

- [CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса](../code-quality/ca1701.md)

- [CA1702. Для сложных слов следует использовать правильный регистр](../code-quality/ca1702.md)

- [CA1703. Строки ресурса должны иметь правильное правописание](../code-quality/ca1703.md)

- [CA1704. Идентификаторы должны иметь правильное правописание](../code-quality/ca1704.md)

- [CA1709. Идентификаторы должны иметь правильное сочетание прописных и строчных букв](../code-quality/ca1709.md)

- [CA1726. Используйте предпочтительные термины](../code-quality/ca1726.md)

- [CA2204. Литералы должны иметь правильное правописание](../code-quality/ca2204.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Dictionary/Words/устарело/Term [ @PreferredAlternate ]

Чтобы включить термин в список терминов, которые анализ кода определяет как устаревший, добавьте термин в качестве внутреннего текста словаря/слов/устаревшего элемента/Term. Нерекомендуемый термин — это слово, которое написано правильно, но не должно использоваться.

Чтобы включить в предупреждение предлагаемый альтернативный термин, укажите альтернативу в атрибуте Преферредалтернате элемента Term. Если вы не хотите предлагать альтернативный вариант, значение атрибута можно оставить пустым.

- Нерекомендуемый термин в словаре/словах/устаревшем элементе/TERM не учитывает регистр.

- В значении атрибута Преферредалтернате учитывается регистр. Используйте стиль Pascal для составных альтернативных вариантов.

**Пример**

```xml
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>
```

Термины в словаре/словах и устаревших узлах применяются к следующим правилам анализа кода:

- [CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса](../code-quality/ca1701.md)

- [CA1702. Для сложных слов следует использовать правильный регистр](../code-quality/ca1702.md)

- [CA1703. Строки ресурса должны иметь правильное правописание](../code-quality/ca1703.md)

- [CA1704. Идентификаторы должны иметь правильное правописание](../code-quality/ca1704.md)

- [CA1726. Используйте предпочтительные термины](../code-quality/ca1726.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Dictionary/слова/составные/термы [ @CompoundAlternate ]

Встроенный словарь определяет некоторые термины как отдельные дискретные термины, а не составной термин. Чтобы включить термин в список терминов, которые анализ кода определяет как составное слово, и указать правильный регистр термина, добавьте этот термин в качестве внутреннего текста словаря/слов/составного элемента. В атрибуте Компаундалтернате элемента Term укажите отдельные слова, составляющие составной термин, с помощью буквы первой буквы отдельных слов (в стиле Pascal). Обратите внимание, что термин, указанный во внутреннем тексте, автоматически добавляется в список словарь/слова/Дискретиксцептионс.

- В составном термине в словаре, словах, составном или условном элементе регистр не учитывается.

- В значении атрибута Компаундалтернате учитывается регистр. Используйте стиль Pascal для составных альтернативных вариантов.

**Пример**

```xml
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>
```

Термины в узле Dictionary/Words/составные узлы применяются к следующим правилам анализа кода:

- [CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса](../code-quality/ca1701.md)

- [CA1702. Для сложных слов следует использовать правильный регистр](../code-quality/ca1702.md)

- [CA1703. Строки ресурса должны иметь правильное правописание](../code-quality/ca1703.md)

- [CA1704. Идентификаторы должны иметь правильное правописание](../code-quality/ca1704.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Dictionary/Words/Дискретиксцептионс/Term

Чтобы исключить термин из списка терминов, которые анализ кода определяет как отдельное, отдельное слово, если термин проверяется правилами регистра для составных слов, добавьте этот термин в качестве внутреннего текста элемента Dictionary/Words/Дискретиксцептионс/Term. В элементе Dictionary/Words/Дискретиксцептионс/Term регистр не учитывается.

**Пример**

```xml
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>
```

Термины в узле Dictionary/Words/Дискретиксцептионс применяются к следующим правилам анализа кода:

- [CA1701. Правильно используйте прописные и строчные буквы в составных словах строк ресурса](../code-quality/ca1701.md)

- [CA1702. Для сложных слов следует использовать правильный регистр](../code-quality/ca1702.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Словарь, акронимы, Касинжексцептионси и акронимы

Чтобы включить акроним в список терминов, идентифицируемых при анализе кода, и указать, как акроним при проверке условий регистра для составных слов, добавьте этот термин в качестве внутреннего текста в элементе Dictionary/акронимы/Касинжексцептионс/акроним. Акроним в элементе Dictionary/акронимы/Касинжексцептионс/акроним учитывает регистр.

**Пример**

```xml
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>
```

Термины в узле Dictionary/акронимы/Касинжексцептионс применяются к следующим правилам анализа кода:

- [CA1709. Идентификаторы должны иметь правильное сочетание прописных и строчных букв](../code-quality/ca1709.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Применение пользовательского словаря к проекту

1. В **Обозреватель решений**используйте одну из следующих процедур.

    - Чтобы добавить словарь в отдельный проект, щелкните правой кнопкой мыши имя проекта и выберите команду **Добавить существующий элемент**. Укажите файл в диалоговом окне **Добавление существующего элемента** .
  
    - Чтобы добавить словарь, который является общим для двух или более проектов, найдите файл для совместного использования в диалоговом окне **Добавление существующего элемента** , нажмите кнопку со стрелкой вниз на кнопке **Добавить** , а затем выберите команду **Добавить как ссылку**.

2. В **Обозреватель решений**щелкните правой кнопкой мыши имя файла **CustomDictionary.xml** и выберите пункт **Свойства**.

3. В списке **действие сборки** выберите **CodeAnalysisDictionary**.

4. В списке **Копировать в выходной каталог** выберите не **Копировать**.
