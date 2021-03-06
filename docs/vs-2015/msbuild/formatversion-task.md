---
title: Задача FormatVersion | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee6e163bd6587d93c970a56ac1c08383084ddc0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149618"
---
# <a name="formatversion-task"></a>Задача FormatVersion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Добавляет номер редакции к номеру версии.  
  
- #1 регистра: входные данные: Version = \<undefined> ;  Редакция = \<don't care> ;   Выходные данные: OutputVersion = "1.0.0.0"  
  
- Случай 2. Входные данные: Version="1.0.0.*"  Revision="5"; выходные данные: OutputVersion="1.0.0.5"  
  
- #3 регистра: ввод: Version = "1.0.0.0" редакция = \<don't care> ;  Выходные данные: OutputVersion = "1.0.0.0"  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице приводятся параметры задачи `FormatVersion`.  
  
|Параметр|Description|  
|---------------|-----------------|  
|`FormatType`|Необязательный параметр `String`.<br /><br /> Определяет тип формата.<br /><br /> — "Version" = версия.<br />— "Path" = замените "." на "_".|  
|`OutputVersion`|Необязательный выходной параметр `String`.<br /><br /> Указывает выходную версию, содержащую номер редакции.|  
|`Revision`|Необязательный параметр `Int32`.<br /><br /> Указывает редакцию, добавляемую к версии.|  
|`Version`|Необязательный параметр `String`.<br /><br /> Указывает строку номера версии для форматирования.|  
  
## <a name="remarks"></a>Remarks  
 Помимо параметров, перечисленных в таблице, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который сам является производным от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описание см. в разделе [базовый класс TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>См. также:  
 [Операции](../msbuild/msbuild-tasks.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
