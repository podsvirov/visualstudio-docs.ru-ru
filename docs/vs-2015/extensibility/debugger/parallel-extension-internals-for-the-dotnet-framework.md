---
title: Внутренние модули параллельного расширения для .NET Framework | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42c472190469e7d008fa8c525f50eabfaf37053f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65680925"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Внутренние компоненты параллельных расширений для .NET Framework
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В этом разделе описываются внутренние типы, методы и поля классов, которые помогают реализовать пользовательский отладчик для параллельных расширений .NET Framework.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Класс Task](../../extensibility/debugger/task-class-internal-members.md)  
 Описывает внутренние элементы данных <xref:System.Threading.Tasks.Task?displayProperty=fullName> класса.  
  
 [Класс TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 Описывает внутренние элементы данных <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> класса.  
  
 [Класс ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 Описывает внутренние элементы данных `System.Threading.Tasks.ContingentProperties` класса.  
  
 Структура [AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 Описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> структуры.  
  
 Структура [AsyncTaskMethodBuilder\<TResult>](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 Описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> структуры.  
  
 [Структура AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 Описывает внутренние элементы <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> структуры.  
  
## <a name="see-also"></a>См. также:  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Расширяемость отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [Параллельное программирование](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
