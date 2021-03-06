---
title: Модель языковой службы прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, model
ms.assetid: d8ae1c0c-ee3d-4937-a581-ee78d0499793
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27d51df6dd11509b86e6648d59978b87d9cd8a02
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157654"
---
# <a name="model-of-a-legacy-language-service"></a>Модель языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Языковая служба определяет элементы и функции для конкретного языка и используется для предоставления редактора со сведениями, характерными для этого языка. Например, редактору необходимо получить сведения об элементах и ключевых словах языка для поддержки цветов синтаксиса.  
  
 Языковая служба тесно взаимодействует с текстовым буфером, который управляется редактором, и представлением, содержащим редактор. Параметр **краткие сведения** Microsoft IntelliSense — это пример функции, предоставляемой языковой службой.  
  
## <a name="a-minimal-language-service"></a>Минимальная языковая служба  
 Самая базовая языковая служба содержит два следующих объекта:  
  
- *Языковая служба* реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс. Языковая служба содержит сведения о языке, включая его имя, расширения имен файлов, диспетчер окон кода и тонированный цвет.  
  
- Он *реализует* <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс.  
  
  На следующем концептуальном рисунке показана модель базовой языковой службы.  
  
  ![График языка модели службы](../../extensibility/media/vslanguageservicemodel.gif "вслангуажесервицемодел")  
  Модель языковой службы Basic  
  
  В окне документа размещается *представление документа* редактора, в данном случае это [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] основной редактор. Представление документа и текстовый буфер принадлежат редактору. Эти объекты работают с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] помощью специализированного окна документа, называемого *окном кода*. Окно кода содержится в <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> объекте, который создается и управляется интегрированной средой разработки.  
  
  При загрузке файла с заданным расширением редактор находит языковую службу, связанную с этим расширением, и передает ее в окно кода, вызывая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод. Языковая служба возвращает *Диспетчер окон кода*, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс.  
  
  В следующей таблице приведены общие сведения об объектах в модели.  
  
|Компонент|Объект|Компонент|  
|---------------|------------|--------------|  
|Текстовый буфер|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>|Поток текста для чтения и записи в Юникоде. В тексте можно использовать другие кодировки.|  
|Окно кода|<xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>|Окно документа, содержащее одно или несколько текстовых представлений. Если [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] находится в режиме многодокументного интерфейса (MDI), окно кода является дочерним ЭЛЕМЕНТОМ MDI.|  
|Текстовое представление|<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>|Окно, позволяющее пользователю перемещаться по тексту и просматривать его с помощью клавиатуры и мыши. Текстовое представление отображается для пользователя в виде редактора. Текстовые представления можно использовать в обычных окнах редактора, в окне вывода и в окне интерпретации. Кроме того, можно настроить одно или несколько текстовых представлений в окне кода.|  
|Диспетчер текста|Управляется <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> службой, с которой вы получаете <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager> указатель|Компонент, который поддерживает общие сведения, общие для всех описанных выше компонентов.|  
|Языковая служба|Зависит от реализации; внедрен <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>|Объект, предоставляющий редактору сведения о конкретном языке, такие как выделение синтаксиса, завершение операторов и сопоставление фигурных скобок.|  
  
## <a name="see-also"></a>См. также:  
 [Данные документа и представление документа в специализированных редакторах](../../extensibility/document-data-and-document-view-in-custom-editors.md)
