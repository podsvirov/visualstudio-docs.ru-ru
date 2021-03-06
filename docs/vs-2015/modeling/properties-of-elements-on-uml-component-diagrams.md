---
title: Свойства элементов на UML-схемах компонентов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671448"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Свойства элементов на схемах компонентов UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

На UML-схеме компонентов каждый элемент имеет свойства. Чтобы просмотреть свойства элемента, щелкните правой кнопкой мыши элемент на схеме или в **обозревателе моделей UML** и выберите пункт **свойства**. Свойства отображаются в окне **Свойства** .

> [!NOTE]
> В этом разделе описываются свойства элементов на UML-схемах компонентов. Дополнительные сведения о том, как читать UML-схемы компонентов, см. в разделе [UML-схемы компонентов: Справочник](../modeling/uml-component-diagrams-reference.md). Дополнительные сведения о способах рисования UML-схем компонентов см. в разделе [UML-схемы компонентов: рекомендации](../modeling/uml-component-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Свойства элементов

|Свойство|По умолчанию|Элемент|Описание|
|--------------|-------------|-------------|-----------------|
|**Имя**|Имя по умолчанию|Все|Идентифицирует элемент.|
|**Полное имя**|Имя пространства имен|Все|Уникально идентифицирует элемент.<br /><br /> Перед именем компонента или типа указывается полное имя пакета, содержащего этот элемент.<br /><br /> Перед именем части или порта указывается полное имя компонента, которому принадлежит этот элемент.|
|**Рабочие элементы**|0 связанных|Все|Число рабочих элементов, связанных с этим элементом. Сведения о связывании рабочих элементов см. в разделе [связывание элементов модели и рабочих элементов](../modeling/link-model-elements-and-work-items.md).|
|**Описание**|(нет)|Все|Здесь можно вести общие заметки об элементе.|
|**Цвет**|(по умолчанию для типа)|Компонент, часть, делегирование, часть сборки|Цвет фигуры. В отличие от других свойств представляет цвет фигуры, а не элемент модели, отображаемый фигурой.|
|**Является неявно создаваемым экземпляром**|Верно|Компонент|Компонент существует только как артефакт конструкции. Во время выполнения существуют только его части.|
|**Абстрактный**|Неверно|Компонент|Определение компонента может использоваться только в качестве обобщения, на основании которого конкретизируются другие компоненты.|
|**Видимость**|Общие|Компонент, часть, порт|**Открытый** — глобально видимый.<br /><br /> **Пакет** — видимый в пределах пакета.<br /><br /> **Частный** — видимый в пределах компонента-владельца.<br /><br /> **Защищенный** — видимый для компонентов, производных от владельца.|
|**Тип**|Тип при создании|Часть<br /><br /> Port|Тип части — компонент или класс.<br /><br /> Тип порта — интерфейс.|
|**Кратность**|1|Часть<br /><br /> Port|Указывает, сколько экземпляров указанного типа формируют часть родительского компонента:<br /><br /> `1` — ровно один.<br /><br /> `0..1` — один или нет.<br /><br /> `*` — Коллекция любого числа.<br /><br /> `n..m` — Коллекция от n до m экземпляров.|
|**Является поведением**|Неверно|Port|Если свойство имеет значение true, сообщения на этот порт обрабатываются действиями или операциями, описанными как часть компонента, а не его частями.|
|**Является службой**|Неверно|Port|Если свойство имеет значение true, этот порт является частью опубликованного интерфейса данного компонента.|
|**Связанный пакет**|Модель|Схема|Пространство имен по умолчанию для элементов, добавленных в эту схему.|

## <a name="see-also"></a>См. также:
 [UML-схемы вариантов использования: эталонные](../modeling/uml-use-case-diagrams-reference.md) [схемы вариантов использования UML: рекомендации](../modeling/uml-use-case-diagrams-guidelines.md)
