---
title: Руководство. определение символов в библиотеке | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f154c63940189f1a6035246fb7f72ec27be677f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191871"
---
# <a name="how-to-identify-symbols-in-a-library"></a>Практическое руководство. Определение символов в библиотеке
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Средства просмотра символов отображают иерархические представления символов. Символы представляют собой пространства имен, объекты, классы, члены классов и другие элементы языка.  
  
 Каждый символ в иерархии может быть идентифицирован данными навигации, передаваемыми библиотекой символов [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] диспетчеру объектов через следующие интерфейсы:  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.  
  
 Расположение символа в иерархии различает символ. Это позволяет средствам просмотра символов переходить к конкретному символу. Расположение определяет уникальный полный путь к символу. Каждый элемент в пути является узлом. Путь начинается с узла верхнего уровня и заканчивается указанным символом. Например, если метод M1 является членом класса C1, а C1 — в пространстве имен N1, полный путь к методу M1 — N1. Тогда. M1. Этот путь содержит три узла: N1, C1 и M1.  
  
 Данные навигации позволяют [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] диспетчеру объектов наыскать, выбирать и оставаться выбранными в иерархии символов. Это позволяет переходить от одного средства просмотра к другому. При использовании **обозревателя объектов** для просмотра символов в [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] проекте можно щелкнуть метод правой кнопкой мыши и запустить средство **Обозреватель вызовов** , чтобы отобразить метод в графе вызовов.  
  
 Расположение символов описывается в двух формах. Каноническая форма основана на полном пути к символу. Он представляет собой уникальную точку символа в иерархии. Он не зависит от средства обзора символов. Чтобы получить каноническую информацию о форме, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Диспетчер объектов вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> метод. В форме представления описывается расположение символа в конкретном инструменте для обзора символов. Расположение символа задается относительно положения других символов в хиерарчици. Заданный символ может иметь несколько путей представления, но только один канонический путь. Например, если класс C1 унаследован от класса C2 и оба класса находятся в пространстве имен N1, **Обозреватель объектов** отображает следующее иерархическое дерево:  
  
```  
N1  
    C1  
        Bases and Interfaces  
            C2  
    C2  
        Bases and Interfaces  
. . . . . . . . . . .  
  
```  
  
 Каноническим путем к классу C2 в этом примере является N1 + C2. Путь к презентации C2 включает узлы C1 и "bases and interfaces": N1 + C1 + "bases and interfaces" + C2.  
  
 Чтобы получить сведения о форме представления, вызывается метод диспетчера объектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> .  
  
## <a name="identifying-a-symbol-in-the-hierarchy"></a>Определение символа в иерархии  
  
#### <a name="to-obtain-canonical-and-presentation-forms-information"></a>Получение сведений о канонических данных и формах представления  
  
1. Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A>.  
  
     Диспетчер объектов вызывает этот метод для получения списка узлов, содержащихся в каноническом пути к символу.  
  
    ```vb  
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer  
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)  
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)  
        Return 0  
    End Function  
    ```  
  
    ```csharp  
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)  
    {  
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =  
            new CallBrowserEnumNavInfoNodes(m_strMethod);  
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);  
        return 0;  
    }  
  
    ```  
  
2. Выполните метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>.  
  
     Диспетчер объектов вызывает этот метод для получения списка узлов, содержащихся в пути представления символа.  
  
## <a name="see-also"></a>См. также:  
 [Поддержка средств обзора символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)   
 [Как зарегистрировать библиотеку с помощью диспетчера объектов](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Практическое руководство. Предоставление списка символов, переданных из библиотеки в диспетчер объектов](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
