---
title: Интеграция XML-литералов с помощью обозревателя XML-схем | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 57a29998-c6e8-48ac-bdb0-5788e73f9164
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a15767454c83604de2844e4c0a9f2e121a9a1a4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "75846125"
---
# <a name="integration-of-xml-literals-with-xml-schema-explorer"></a>Интеграция XML-литералов с обозревателем XML-схем
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Basic поддерживает XML-литералы, что означает возможность включать XML-фрагменты непосредственно в код Visual Basic. Дополнительные сведения см. в разделе [Общие сведения о литералах XML](https://msdn.microsoft.com/library/bb384629.aspx).

 Если XSD-файл в проекте Visual Basic содержит XML-литерал, то набор XML-схем можно просматривать в обозревателе XML-схем. Для просмотра набора схем, связанного с XML-литералом, щелкните правой кнопкой мыши узел XML в XML-литерале или импорте пространства имен XML, и выберите команду **Показать в обозревателе схем**.

 ![XML-литералы Visual Basic; обозреватель схемы XML](../xml-tools/media/vbxmlliteralswithxmlschemaexplorer1.gif "VBXMLLiteralsWithXMLSchemaExplorer1")

 Это действие откроет обозреватель XML-схем параллельно файлу Visual Basic.

 ![XML-литералы Visual Basic; обозреватель схемы XML](../xml-tools/media/vbxmlliteralswithxmlschemaexplorer2.gif "VBXMLLiteralsWithXMLSchemaExplorer2")

 Данная возможность впервые появилась в Visual Studio 2008 SP1. Чтобы просмотреть собеседование, в котором подробно описывается этот компонент, см. раздел [Channel 9 интервью: Обозреватель XML-схем в Visual Studio 2008 с пакетом обновления 1 (SP1)](https://channel9.msdn.com/Blogs/funkyonex/XML-Schema-Explorer-in-Visual-Studio-2008-SP1).

## <a name="see-also"></a>См. также:
 [Как использовать конструктор XML-схем с XML-литералами](../xml-tools/how-to-use-the-xml-schema-designer-with-xml-literals.md)
