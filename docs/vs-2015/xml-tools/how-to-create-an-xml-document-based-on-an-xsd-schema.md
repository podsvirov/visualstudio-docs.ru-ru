---
title: Как создать XML-документ на основе схемы XSD | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9e48c48d6711a1eb21157122d13790e22688855
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670948"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>Практическое руководство. Создание XML-документа на основе схемы XSD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функция **Создание образца XML** создает образец XML-файла на основании файла XML-схемы (XSD).

 Этот пункт можно использовать в следующих случаях.

- Чтобы понять, как использовать различные конструкции в данной схеме.

- Чтобы убедиться в том, что схема функционирует должным образом.

  Функция **Создание образца XML** доступна только для глобальных элементов и требует, чтобы набор схем XML был допустимым.

  С помощью этой функции обычно создаются допустимые XML-документы. Однако, если схема содержит одно или несколько из следующих ограничений, образец может быть недопустимым.

- Ограничения удостоверения `xs:key`, `xs:keyref` и `xs:unique`.

- Аспекты `xs:pattern`.

- Перечисления типа `xs:QName`.

- Типы `xs:ENTITY`, `xs:ENTITIES` и `xs:NOTATION`.

  Также заметьте, что содержимое `xs:base64Binary` будет создано, только если в схеме есть перечисления для этого типа.

### <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>Создание экземпляра XML-документа на основе XSD-файла.

1. Выполните действия, описанные в разделе [Создание и изменение файла XSD-схемы](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md).

2. В [обозревателе XML-схем](../xml-tools/xml-schema-explorer.md) щелкните правой кнопкой мыши глобальный элемент `PurchaseOrder`. Выберите **Создание образца XML**.

     Если выбран данный параметр, файл PurchaseOrder.xml со следующим образцом XML-содержимого будет создан и открыт в редакторе XML:

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```

## <a name="see-also"></a>См. также:
 [Работа с XML-данными](../xml-tools/working-with-xml-data.md)
