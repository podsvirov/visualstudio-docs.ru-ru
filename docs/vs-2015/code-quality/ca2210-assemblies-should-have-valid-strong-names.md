---
title: 'CA2210: сборки должны иметь допустимые строгие имена | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8f800a550717abfabdfb9296fc8f6de49d127d73
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548204"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210. Сборки должны иметь допустимые строгие имена
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Категория|Microsoft. Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка не подписана строгим именем, не удалось проверить строгое имя, или строгое имя будет недействительным без текущих параметров реестра компьютера.

## <a name="rule-description"></a>Описание правила
 Это правило извлекает и проверяет строгое имя сборки. Нарушение возникает, если выполняется одно из следующих условий.

- Сборка не имеет строгого имени.

- Сборка была изменена после подписания.

- Сборка имеет отложенную подпись.

- Сборка была неправильно подписана, или произошел сбой при подписании.

- Сборка требует, чтобы параметры реестра прошли проверку. Например, средство строгих имен (Sn.exe) использовалось для пропуска проверки сборки.

  Строгое имя защищает клиентов от случайной загрузки сборки, которая была подменена. Сборки без строгих имен следует развертывать лишь в крайне небольшом числе случаев. При обмене или распространении сборок без правильной подписи сборки могут быть подменены, среда CLR может не загрузить сборку или пользователь может быть вынужден отключить проверку на своем компьютере. Сборка без строгого имени имеет следующие недостатки:

- Его источники не могут быть проверены.

- Среда CLR не может предупредить пользователей, если содержимое сборки было изменено.

- Он не может быть загружен в глобальный кэш сборок.

  Обратите внимание, что для загрузки и анализа сборки с отложенной подписью необходимо отключить проверку сборки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 **Создание файла ключа**

 Используйте одну из следующих процедур.

- Используйте средство компоновщика сборок (Al.exe), предоставляемое [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] пакетом SDK.

- Для [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] версии 1.0 или 1.1 используйте либо атрибут, либо <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> .

- Для [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] используйте либо `/keyfile` `/keycontainer` параметр компилятора [/keyfile (укажите ключ или пару ключей для подписи сборки)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) , либо параметр [/keycontainer (укажите контейнер ключей для подписания сборки)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) в C++.

  **Подпись сборки строгим именем в Visual Studio**

1. В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] откройте решение.

2. В **Обозреватель решений**щелкните правой кнопкой мыши проект и выберите пункт **Свойства.**

3. Перейдите на вкладку **Подписывание** и установите флажок **подписать сборку** .

4. В **разделе Выберите файл ключа строгого имени**выберите **создать**.

    Отобразится окно **Создание ключа строгого имени** .

5. В разделе **имя файла ключа**введите имя для ключа строгого имени.

6. Укажите, следует ли защищать ключ паролем, а затем нажмите кнопку **ОК**.

7. В **Обозреватель решений**щелкните правой кнопкой мыши проект и выберите пункт **Сборка**.

   **Подпись сборки строгим именем за пределами Visual Studio**

- Используйте средство строгих имен (Sn.exe), предоставляемое [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] пакетом SDK. Дополнительные сведения см. в разделе [Sn.exe (средство строгих имен)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключать предупреждение из этого правила следует только в том случае, если сборка используется в среде, в которой искажение содержимого не является важным.

## <a name="see-also"></a>См. также:
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [Как подписать сборку строгим именем](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (средство строгих имен)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
