---
title: Как присоединить представления к данным документа | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bc1b57e189902624c13149d0264142ff66af050
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842657"
---
# <a name="how-to-attach-views-to-document-data"></a>Практическое руководство. Вложение представлений в данные документа
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если у вас есть новое представление документа, вы можете присоединить его к существующему объекту данных документа.  
  
### <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>Определение возможности присоединения представления к существующему объекту данных документа  
  
1. Реализуйте расширение <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>.  
  
2. В реализации `IVsEditorFactory::CreateEditorInstance` метод вызывается `QueryInterface` для существующего объекта данных документа, когда интегрированная среда разработки вызывает вашу `CreateEditorInstance` реализацию.  
  
     Вызов `QueryInterface` позволяет исследовать существующий объект данных документа, указанный в `punkDocDataExisting` параметре.  
  
     Однако конкретные интерфейсы, которые необходимо запросить, зависят от редактора, открывающего документ, как описано в шаге 4.  
  
3. Если не найти соответствующие интерфейсы для существующего объекта данных документа, то необходимо вернуть код ошибки в редактор, указывающий, что объект данных документа несовместим с вашим редактором.  
  
     В реализации интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> диалоговое окно сообщения уведомляет о том, что документ открыт в другом редакторе, и спрашивает, нужно ли его закрыть.  
  
4. Если закрыть этот документ, Visual Studio вызовет фабрику редактора еще раз. При этом вызове `DocDataExisting` параметр РАВЕН null. После этого реализация фабрики редактора может открыть объект данных документа в собственном редакторе.  
  
    > [!NOTE]
    > Чтобы определить, можно ли работать с существующим объектом данных документа, можно также использовать закрытые знания реализации интерфейса путем приведения указателя к фактическому [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] классу реализации закрытой. Например, все стандартные редакторы реализуют `IVsPersistFileFormat` , которые наследуют от <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> . Таким же, можно вызвать метод `QueryInterface` для <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> , и если идентификатор класса для существующего объекта данных документа соответствует идентификатору класса вашей реализации, то можно работать с объектом данных документа.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Когда Visual Studio вызывает реализацию <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> метода, он передает указатель на существующий объект данных документа в `punkDocDataExisting` параметре, если он существует. Изучите объект данных документа, возвращенный в `punkDocDataExisting` , чтобы определить, подходит ли объект данных документа для редактора, как описано в шаге 4 процедуры, описанной в этом разделе. Если это уместно, Фабрика редактора должна предоставить второе представление для данных, как описано в статье [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md). В противном случае он должен отобразить соответствующее сообщение об ошибке.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка нескольких представлений документов](../extensibility/supporting-multiple-document-views.md)   
 [Данные документа и представление документа в специализированных редакторах](../extensibility/document-data-and-document-view-in-custom-editors.md)
