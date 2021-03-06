---
title: Представление процессов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.processesview
helpviewer_keywords:
- Processes view
ms.assetid: e144e70e-eef2-45a7-a562-a177f177d9a1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d8b9c04d1cabd44418c70725ef331c9c4b5ec67e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580515"
---
# <a name="processes-view"></a>Представление процессов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В представлении процессов отображается дерево всех активных процессов в системе. Здесь указаны идентификаторы процессов и имена модулей. Используйте представление процессов, если вы намерены изучить определенный системный процесс, который обычно соответствует выполняемой программе. Процессы идентифицируются по именам модулей или обозначаются как "системные процессы".  
  
 Microsoft Windows поддерживает выполнение нескольких процессов. Каждый процесс может иметь один или несколько потоков, а с каждым потоком могут быть связаны одно или несколько окон верхнего уровня. Каждое окно верхнего уровня может иметь несколько дочерних окон. Символ "+" (плюс) указывает, что этот уровень свернут. В свернутом представлении каждому процессу соответствует одна строка. Щелкните символ "+", чтобы развернуть такой уровень.  
  
 Используйте представление процессов, если вы намерены изучить определенный системный процесс, который обычно соответствует выполняемой программе. Процессы идентифицируются по именам модулей или обозначаются как "системные процессы". Чтобы найти процесс, сверните дерево и выполните поиск по списку.  
  
## <a name="procedures"></a>Процедуры  
  
#### <a name="to-open-the-processes-view"></a>Открытие представления процессов  
  
1. В меню **Spy** выберите пункт **Процессы**.  
  
   ![Представление процессов Spy&#43;&#43; ](../debugger/media/spy-processes.png "_Processes Spy + +")  
   Представление процессов в Spy++  
  
   На рисунке выше показано представление процессов, где развернуты узлы процессов и потоков.  
  
### <a name="in-this-section"></a>В этом разделе  
 [Поиск процесса в представлении процессов](../debugger/how-to-search-for-a-process-in-processes-view.md)  
 Описывает, как найти конкретный процесс в представлении процессов.  
  
 [Отображение свойств процесса](../debugger/how-to-display-process-properties.md)  
 Объясняет, как отобразить дополнительные сведения о сообщении.  
  
### <a name="related-sections"></a>См. также  
 [Представления Spy++](../debugger/spy-increment-views.md)  
 Описание древовидных представлений окон, сообщений, процессов и потоков в Spy + +.  
  
 [Использование Spy++](../debugger/using-spy-increment.md)  
 Содержит описание средства Spy + + и объясняет, как его можно использовать.  
  
 [Диалоговое окно "Поиск процесса"](../debugger/process-search-dialog-box.md)  
 Используется для поиска узла для определенного процесса в представлении процессов.  
  
 [Диалоговое окно "Свойства процесса"](../debugger/process-properties-dialog-box.md)  
 Отображает свойства процесса, выбранного в представлении процессов.  
  
 [Справочник по Spy++](../debugger/spy-increment-reference.md)  
 Включает разделы, описывающие каждое меню и диалоговое окно Spy + +.
