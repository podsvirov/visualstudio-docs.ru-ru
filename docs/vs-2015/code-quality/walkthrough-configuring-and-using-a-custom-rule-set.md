---
title: Пошаговое руководство. Настройка и использование настраиваемого набора правил | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, walkthroughs
- code analysis, rule sets
ms.assetid: 7fe0a4e3-1ce0-4f38-a87a-7d81238ec7cd
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8239afd1cf4e8c0a5e702f2b0e4ed64408cada09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645743"
---
# <a name="walkthrough-configuring-and-using-a-custom-rule-set"></a>Пошаговое руководство. Настройка и использование набора настраиваемых правил
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом пошаговом руководстве показано, как использовать средства анализа кода, настроенные для использования настроенного *набора правил* в библиотеке классов. Можно выбрать набор правил, относящийся к типу проекта, указанному для решения, или выбрать альтернативные наборы правил для выполнения определенных задач, таких как проверка устаревшего кода на наличие проблем, которые могут быть устранены неразрывным способом. В любом случае наборы правил также можно настроить, чтобы настроить их в требованиях к проекту.

 В этом пошаговом руководстве будут рассмотрены следующие процессы.

- Создайте библиотеку классов.

- Выберите набор правил анализа кода " **базовые правила разработки Microsoft Basic** ".

- Добавьте в класс собственный код.

- Запустите анализ кода.

- Настройка набора правил.

- Запустите анализ кода и посмотрите, как работает поведение настройки набора правил.

## <a name="prerequisites"></a>Предварительные требования

- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]или [!INCLUDE[vsPro](../includes/vspro-md.md)]

## <a name="using-rule-sets-with-code-analysis"></a>Использование наборов правил с анализом кода
 Сначала создайте простую библиотеку классов.

#### <a name="create-a-class-library"></a>Создание библиотеки классов

1. В меню **Файл** выберите пункт **Создать**, а затем щелкните **Проект**.

2. В диалоговом окне **Новый проект** в разделе **типы проектов**выберите **Visual C#**.

3. В разделе **Visual C#** выберите **Библиотека классов**.

4. В текстовом поле **имя** введите **рулесетсампле** и нажмите кнопку **ОК**.

   Далее необходимо выбрать набор правил " **базовые правила для разработки Microsoft** " и сохранить его вместе с проектом.

#### <a name="select-a-code-analysis-rule-set"></a>Выберите набор правил анализа кода

1. В меню **анализ** выберите пункт **Настройка анализа кода для рулесетсампле**.

    Отобразятся параметры конфигурации для анализа кода.

2. В раскрывающемся списке **выполнить этот набор правил** выберите параметр **Майкрософт все правила**.

    Дополнительные сведения о доступных наборах правил см. в разделе [Справочник по набору правил анализа кода](../code-quality/code-analysis-rule-set-reference.md).

    В меню Файл выберите команду **Сохранить выбранные элементы** , чтобы обновить файл проекта, указав сведения о выбранном наборе правил и его параметрах.

   > [!TIP]
   > В реальной ситуации рекомендуется использовать для определения приоритетов, какие проблемы следует ориентировать в анализе кода, — начать с **минимального набора правил рекомендуемых правил** и исправить нужные проблемы, а затем последовательно добавить дополнительные правила или наборы правил, чтобы найти и устранить дополнительные проблемы.

   Далее вы добавите в библиотеку классов код, который будет использоваться для демонстрации нарушений CA1704 "идентификаторы должны быть правильно написаны" правил анализа кода. Дополнительные сведения см. в разделе [CA1704: идентификаторы должны быть написаны правильно](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

#### <a name="add-your-own-code"></a>Добавление собственного кода

- В обозреватель решений откройте файл Class1.cs и замените существующий код следующим:

  ```
  using System;
  using System.Collections.Generic;
  using System.Text;

  namespace RuleSetSample
  {
      public class Class1
      {
          //The variable parameter names "a" and "b" will cause
          //the warning CA 1704 Microsoft.Naming "Consider
          //providing a more meaningful name" to fire
          public int AddIntegers(int a, int b)
          {

              int sum = a + b;

              return (sum);
          }
      }
  }

  ```

  Теперь можно запустить анализ кода в проекте Рулесетсампле и найти ошибки и предупреждения, созданные в окне Список ошибок.

#### <a name="run-code-analysis-on-the-rulesetsample-project"></a>Выполнение анализа кода в проекте Рулесетсампле

1. В меню **анализ** выберите пункт **запустить анализ кода для рулесетсампле**.

2. В окне Список ошибок щелкните **предупреждения** , а затем щелкните заголовок столбца **Описание** , чтобы отсортировать предупреждения в алфавитном порядке.

    В реальном приложении вы исследуете все нарушения правил, которые следует исправить на этом этапе, или при необходимости отключить или отключить правило, если вы определили, что оно не было исправлено. Дополнительные сведения см. в разделе [Подавление предупреждений при помощи атрибута SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

3. Обратите внимание на предупреждения CA1704. Эти нарушения в этом правиле указывают на то, что следует "рассмотреть возможность предоставления более значимого имени для параметров". Можно исправить ошибку в коде или отключить правило, как описано в следующей процедуре.

   Далее предстоит настроить набор правил, чтобы исключить предупреждение CA1704, "идентификаторы должны быть правильно написаны".

#### <a name="customize-the-rule-set-for-your-project-to-disable-a-specific-rule"></a>Настройка набора правил для проекта для отключения определенного правила

1. В меню **анализ** выберите пункт **Настройка анализа кода для рулесетсампле**.

2. В раскрывающемся списке **выполнить этот набор** правил убедитесь, что набор правил **Microsoft все правила** все еще выделен, а затем нажмите кнопку **Открыть**. Отобразится страница набора правил.

3. Разверните узел Категория Microsoft. Naming, а затем выберите предупреждение CA1704.

4. В столбце **действие** выберите **нет.** Это предотвращает отображение CA1704 в виде предупреждения или ошибки в окне Список ошибок.

    Теперь пора поэкспериментировать с различными кнопками панели инструментов и параметрами фильтрации, чтобы ознакомиться с ними. Например, можно использовать раскрывающийся список **Группировать по** , чтобы найти конкретное правило или категорию правил. Другим примером может быть использование кнопки **Скрыть отключенные правила** на панели инструментов страницы набора правил для скрытия или отображения всех правил, для которых в столбце **действие** задано значение **нет**. Это может быть полезно, если вы хотите проверить все правила, которые были отключены, чтобы убедиться, что они по-прежнему отключены.

5. В меню Вид выберите пункт Окно свойств. Введите **набор настраиваемых правил** в поле Имя окна инструментов Свойства. Это приведет к изменению отображаемого имени нового набора правил в [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] интегрированной среде разработки.

6. Чтобы сохранить настроенный набор правил, в меню **файл** выберите команду **сохранить Microsoft все правила. RuleSet** . Перейдите к корневой папке проекта. В текстовом поле **имя файла** введите **микустомрулесет**. Теперь можно выбрать настраиваемый набор правил для использования с проектом.

   Теперь, когда создан новый набор правил, необходимо настроить параметры проекта, чтобы указать, что вы хотите использовать новый набор правил.

#### <a name="specify-the-new-rule-set-for-use-with-your-project"></a>Укажите новый набор правил для использования с проектом

1. В обозреватель решений щелкните правой кнопкой мыши проект и выберите пункт **Свойства**.

2. На вкладке **Свойства** щелкните **анализ кода**.

    В раскрывающемся списке **выполнить этот набор правил** нажмите кнопку **\<Browse..>** . Перейдите в корневую папку проекта кода и выберите **микустомрулесет. RuleSet**. Это новый набор правил, созданный в предыдущей процедуре.

3. В меню **файл** выберите команду **сохранить** , чтобы сохранить конфигурацию проекта. Теперь настраиваемый набор правил можно использовать в проекте.

   Наконец, вы снова запустите анализ кода с помощью набора правил Микустомрулесет. Обратите внимание, что в окне Список ошибок не отображается нарушение правила производительности CA1704.

#### <a name="run-code-analysis-on-the-rulesetsample-project-for-the-second-time"></a>Запустить анализ кода для проекта Рулесетсампле во второй раз

1. В меню **анализ** выберите пункт **запустить анализ кода для рулесетсампле**.

2. В окне Список ошибок обратите внимание, что при нажатии кнопки **предупреждения**больше не отображаются нарушения предупреждений CA1704 для правил "идентификаторы должны быть правильно написаны".

## <a name="see-also"></a>См. также:
 [Руководство. Настройка анализа кода для](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md) [справочника по набору правил анализа кода](../code-quality/code-analysis-rule-set-reference.md) проекта управляемого кода
