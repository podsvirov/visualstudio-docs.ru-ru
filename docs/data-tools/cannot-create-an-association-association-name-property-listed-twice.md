---
title: Перечисление двух свойств
description: Не удалось создать ассоциацию — одно и то же свойство перечислено дважды
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d0e3475896c937f247fc64a0750da25c2d6edac9
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036487"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Не удалось создать ассоциацию &lt;имя ассоциации&gt; — одно и то же свойство перечислено дважды

Не удается создать ассоциацию \<association name> . Одно и то же свойство перечислено несколько раз: \<property name> .

Ассоциации определяются выбранными **свойствами ассоциации** в диалоговом окне **Редактор ассоциаций**. Свойства могут быть перечислены только один раз для каждого класса в ассоциации.

Свойство в сообщении появляется более чем один раз в любом родительском или дочернем окне **Свойства ассоциации**.

## <a name="to-resolve-this-condition"></a>Чтобы устранить эту проблему,

- Проверьте сообщение и отметьте свойство, указанное в сообщении.

- Нажмите кнопку **ОК**, чтобы закрыть окно сообщения.

- Проверьте **Свойства ассоциации** и удалите дублированные записи.

- Нажмите кнопку **ОК**.

## <a name="see-also"></a>См. также

- [Инструменты LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Как создать ассоциацию между классами LINQ to SQL (реляционный конструктор R)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)