---
title: Управление видимостью значка или декоратора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49cecff999e0155209ba58c20c0d623b15d63698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667826"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Управление видимостью значка или декоратора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Декоратор* — это значок или строка текста, отображаемая на фигуре в доменном языке (DSL). Вы можете сделать декоратор отображаемым и исчезать в зависимости от состояния свойств в модели. Например, для фигуры, представляющей человека, могут отображаться различные значки в зависимости от пола, числа детей и т. д.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Управление видимостью значка или декоратора
 В следующей процедуре предполагается, что вы уже определили фигуру и ее сопоставление с классом домена. Дополнительные сведения см. [в разделе Определение доменного языка](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Управление видимостью значка или текстового декоратора

1. На схеме определения DSL Добавьте к классу Shape значки или текстовые декораторы, которые должны отображаться.

   1. Щелкните правой кнопкой мыши класс Shape, наведите указатель на пункт **Добавить**и выберите нужный тип декоратора.

   2. Задайте свойство **расположения** декоратора. Одно и то же расположение может быть больше одного декоратора. Например, у вас могут быть значки с одним и тем же положением для пола и женщина.

   3. Задание свойства **значка по умолчанию** декоратора значка.

2. Выберите карту элементов схемы, которая является серой линией между классом Shape и классом домена на схеме определения DSL.

3. В окне "сведения о DSL" на вкладке " **карты декоратора** " выберите декоратор. Например, Маледекоратор.

4. Установите флажок **область фильтра видимость** .

5. Если свойство предметной области, которое должно управлять видимостью, находится в классе немедленного домена, оставьте **путь к свойству фильтра** пустым.

    В противном случае щелкните раскрывающееся меню и перейдите к связи или классу, где находится свойство.

   - Чтобы избежать отчета об ошибках, не следует перемещаться по связям, помеченным "*", в инструменте навигации.

6. Задайте **свойство Filter** для свойства предметной области. Например, пол.

7. В списке **записи видимости** добавьте значения этого свойства домена, для которых должен быть видим декоратор. Например, «папа».

8. Повторите шаги для каждого значка.

9. **Преобразуйте все шаблоны**, выполните сборку и запуск и откройте диаграмму тестирования.

10. При изменении значения управляющего свойства декораторы должны отображаться и исчезнуть.

    Часто требуется, чтобы видимость управлялась более сложной формулой, чем простой набор значений. Например, для того, чтобы значок зависел от числа ссылок определенного типа или для того, чтобы он зависел от того, находится ли число в определенном диапазоне. В этом случае используйте следующую процедуру.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Управление видимостью декоратора на основе формулы

1. Добавьте вычисляемое свойство домена в доменный класс. В окне **Свойства** задайте следующие значения:

     **Отображаемый =** `False` **— скрывает свойство от пользователя** .    

     **Тип =** `Calculated` **— это означает, что вы будете предоставлять код, который вычисляет свое значение** .    

     **Имя** , например **декораторконтрол**

     **Тип** = `Boolean`

     Дополнительные сведения см. в разделе [вычисляемые и настраиваемые свойства хранилища](../modeling/calculated-and-custom-storage-properties.md).

2. Сделайте новое свойство элементом управления видимость декоратора.

    1. Выберите карту элементов схемы, которая является серой линией из доменного класса на фигуру. В окне **сведения о DSL** откройте вкладку **декоратормап** .

    2. Установите флажок **область фильтра видимость** .

    3. В поле **Свойства фильтра**выберите свойство элемента управления **декораторконтрол**.

    4. В разделе **записи видимости**введите `True` .

3. Щелкните **преобразовать все шаблоны** на панели инструментов Обозреватель решений.

4. В меню **Сборка** выберите пункт **построить решение** .

5. Дважды щелкните отчет об ошибке "*йоуркласс* не содержит определение для жетдекораторконтролвалуе...".

     Редактор текста откроется в Дсл\женератедкоде\домаинклассес.КС. Над выделенной ошибкой находится комментарий, который запрашивает Добавление метода.

6. Обратите внимание на отсутствующие пространство имен, класс и метод.  Например, Company. FamilyTree. Person. Жетдекораторконтролвалуе ().

7. В отдельном файле кода напишите определение разделяемого класса, содержащего отсутствующий метод. Пример:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Дополнительные сведения о настройке модели с помощью программного кода см. [в разделе Навигация и обновление модели в программном коде](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Перестройте и запустите решение.

## <a name="see-also"></a>См. также:
 [Определение фигур и соединителей](../modeling/defining-shapes-and-connectors.md) [Установка фонового изображения на схеме](../modeling/setting-a-background-image-on-a-diagram.md) [Навигация и обновление модели в коде программного кода](../modeling/navigating-and-updating-a-model-in-program-code.md) [Создание кода для настройки предметно-ориентированного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)
