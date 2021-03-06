---
title: Выбранный класс не может быть удален, так как он используется как тип возвращаемого значения для одного или нескольких методов DataContext | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d68254a0-f3a1-47e2-aed3-a83471e1d711
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf16fe7453388e19308ed603ee9dbbac207cec41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667257"
---
# <a name="the-selected-class-cannot-be-deleted-because-it-is-used-as-a-return-type-for-one-or-more-datacontext-methods"></a>Выбранный класс невозможно удалить, потому что он используется как возвращаемый тип одного или нескольких методов DataContext
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Тип возвращаемого значения одного или нескольких методов <xref:System.Data.Linq.DataContext> это выбранный класс сущностей. Удаление класса сущностей, который используется в качестве типа возврата для метода <xref:System.Data.Linq.DataContext>, вызовет ошибку компиляции проекта. Чтобы удалить выбранный класс сущностей, Идентифицируйте методы <xref:System.Data.Linq.DataContext>, которые его используют, и задайте их типам возврата другой класс сущностей.

 Чтобы вернуть типы возвращаемых <xref:System.Data.Linq.DataContext> методов к исходным автоматически сформированным типам, сначала удалите <xref:System.Data.Linq.DataContext> метод с панели методы, а затем перетащите объект из **Обозреватель сервера** / **Обозреватель базы данных** в конструктор O/R.

### <a name="to-correct-this-error"></a>Исправление ошибки

1. Определите <xref:System.Data.Linq.DataContext> методы, использующие класс сущностей в качестве возвращаемого типа, выбрав <xref:System.Data.Linq.DataContext> метод на панели методы и проверив свойство **тип возвращаемого** значения в окне **Свойства** .

2. Установите **Тип возврата<xref:System.Data.Linq.DataContext> на другой класс сущностей или удалите метод ** из области методов.

## <a name="see-also"></a>См. также:
 Пошаговое руководство [по LINQ to SQL инструментов в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [. Создание классов LINQ to SQL (конструктор o-r Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [методы DataContext (реляционный конструктор r)](../data-tools/datacontext-methods-o-r-designer.md) [Практическое руководство. изменение типа возвращаемого значения метода DataContext (реляционный конструктор r)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)
