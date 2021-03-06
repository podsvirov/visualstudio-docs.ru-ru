---
title: Руководство. Миграция проекта языкового Domain-Specific
description: Содержит сведения о том, как перенести проект доменного языка в более новую версию Visual Studio.
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: dacb13ef14768f4f59a414f6159bbea8d24c4de8
ms.sourcegitcommit: a18c7e9b367c2f92f6e54c3eaef442775d457667
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/15/2020
ms.locfileid: "92298415"
---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>Практическое руководство. Перенос доменного языка в новую версию
Проекты, которые определяют и используют доменный язык, можно перенести [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] из версии [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , которая была распространена с помощью [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] .

 Средство миграции предоставляется в составе [!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)] . Средство преобразует проекты и решения Visual Studio, использующие или определяющие средства DSL.

 Средство миграции необходимо запускать явным образом: оно не запускается автоматически при открытии решения в Visual Studio. Этот инструмент и подробные рекомендации можно найти по следующим адресам:

 **% Program Files%\Microsoft SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exeVisual Studio 2010 **

## <a name="before-you-migrate-your-dsl-projects"></a>Перед миграцией проектов DSL
 Средство миграции изменяет файлы проекта Visual Studio (**. csproj**) и файлы решения (**SLN**).

#### <a name="to-prepare-projects-for-migration"></a>Подготовка проектов к миграции.

- Убедитесь, что файлы **CSPROJ** и **SLN** могут быть записаны. Если они находятся в системе управления версиями, убедитесь, что они извлечены.

- Создайте копию папок, которые планируется перенести.

## <a name="migrating-a-collection-of-projects"></a>Перенос коллекции проектов

#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>Перенос проектов и решений DSL в Visual Studio 2010

1. Запустите средство миграции DSL.

   - Можно дважды щелкнуть инструмент в проводнике (или проводнике) или запустить средство из командной строки. Средство находится в этом расположении:

        **%ProgramFiles%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**

2. Выберите папку, содержащую решения и проекты, которые необходимо преобразовать.

   - Введите путь в поле в верхней части средства или нажмите кнопку **Обзор**.

     Средство миграции отображает дерево проектов, определяющих или использующих домен DSL. Дерево содержит все проекты, использующие сборки **Microsoft. VisualStudio. моделирования. SDK** или **TextTemplating** .

3. Просмотрите дерево проектов и снимите флажки проектов, которые не нужно преобразовывать.

   - Выберите проект или решение, чтобы просмотреть список изменений, которые будут внесены средством.

       > [!NOTE]
       > Флажки, отображаемые рядом с именами папок, не действуют. Для проверки проектов и решений необходимо развернуть папки.

4. Преобразуйте проекты.

   1. Нажмите кнопку **преобразовать**.

        Перед преобразованием каждого файла проекта копия _Project_**. csproj** сохраняется как _Project_**. VS2008. csproj.**

        Копия каждого _решения_**. sln** сохраняется как _Solution_**. VS2008. sln**

   2. Исследовать все неудачные преобразования, о которых сообщается.

        Ошибки выводятся в текстовом окне. Кроме того, представление в виде дерева отображает красный флаг на каждом узле, который не удалось преобразовать. Можно щелкнуть узел, чтобы получить дополнительные сведения об этом сбое.

5. **Преобразование всех шаблонов** в решениях, содержащих успешно преобразованные проекты.

   1. Откройте решение.

   2. Нажмите кнопку **преобразовать все шаблоны** в заголовке Обозреватель решений.

       > [!NOTE]
       > Этот шаг можно сделать ненужным. Дополнительные сведения см. [в разделе Автоматизация преобразования всех шаблонов](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

6. Обновите пользовательский код в преобразованных проектах.

   - Попытка выполнить сборку проектов и исследовать все сбои.

   - Протестируйте конструктор.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>См. также раздел

- [Связанные записи в блогах](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)