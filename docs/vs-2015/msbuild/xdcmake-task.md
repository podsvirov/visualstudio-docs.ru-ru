---
title: Задача XDCMake | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c16c92b41aa0635ecb24d83e30e2c347620b2c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675539"
---
# <a name="xdcmake-task"></a>Задача XDCMake
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Является оболочкой для средства XML-документации (xdcmake.exe), которая помещает в XML-файл файлы комментариев (XDC-файлы) для документа XML.  
  
 XDC-файл создается, если ввести комментарии к документации в исходный код Visual C++ и выполнить компиляцию с использованием параметра компиляции [/doc](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63). Дополнительные сведения см. в разделах [Справочник по XDCMake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [Страницы свойств средства создания XML-документов](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0), а также в разделе справки, вызываемом с помощью параметра командной строки (**/?**) для файла xdcmake.exe.  
  
## <a name="remarks"></a>Remarks  
 По умолчанию средство xdcmake.exe поддерживает несколько параметров командной строки. Для поддержки дополнительных параметров необходимо указать параметр командной строки **/old**.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описываются параметры задачи **XDCMake**.  
  
|Параметр|Description|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|Необязательный параметр типа **String[]** .<br /><br /> Указывает один или несколько дополнительных XDC-файлов для слияния.<br /><br /> Дополнительные сведения см. в описании параметра **Дополнительные файлы документации** в разделе [Страницы свойств средства создания XML-документов](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0). Также см. описание параметров командной строки **/old** и **/Fs** для файла xdcmake.exe.|  
|**AdditionalOptions**|Необязательный параметр **String** .<br /><br /> Список параметров, как указано в командной строке. Например, "*/параметр1/параметр2/параметр№*". Этот параметр используется для указания параметров, не представленных каким-либо другим параметром задачи **XDCMake**.<br /><br /> Дополнительные сведения см. в разделах [Справочник по XDCMake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [Страницы свойств средства создания XML-документов](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0), а также в разделе справки, вызываемом с помощью параметра командной строки (**/?**) для файла xdcmake.exe.|  
|**DocumentLibraryDependencies**|Необязательный параметр типа **Boolean**.<br /><br /> Если имеет значение `true` и текущий проект содержит зависимости от проекта статической библиотеки (.lib) в решении, XDC-файлы для такого проекта библиотеки включаются в выходной XML-файл для текущего проекта.<br /><br /> Дополнительные сведения см. в описании параметра **Зависимости библиотек документов** в разделе [Страницы свойств средства создания XML-документов](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0).|  
|**OutputFile**|Необязательный параметр **String** .<br /><br /> Переопределяет имя выходного файла по умолчанию. Имя по умолчанию является производным от имени первого обработанного XDC-файла.<br /><br /> Дополнительные сведения см. в описании параметра **/out:** `filename` в [справочнике](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac)по программе xdcmake. Также см. описание параметров командной строки **/old** и **/Fo** для файла xdcmake.exe.|  
|**Имя проекта**|Необязательный параметр **String** .<br /><br /> Имя текущего проекта.|  
|**SlashOld**|Необязательный параметр типа **Boolean**.<br /><br /> Если имеет значение `true`, могут использоваться дополнительные параметры для xdcmake.exe.<br /><br /> Дополнительные сведения см. в описании параметра командной строки **/old** для xdcmake.exe.|  
|**Источники**|Обязательный параметр `ITaskItem[]`.<br /><br /> Определяет массив элементов исходного файла MSBuild, который может использоваться и создаваться задачами.|  
|**SuppressStartupBanner**|Необязательный параметр типа **Boolean**.<br /><br /> Если задано значение `true`, запрещается отображение сообщения о номере версии и авторских правах при запуске задачи.<br /><br /> Дополнительные сведения см. в описании параметра **/nologo** в разделе [Справочник по XDCMake](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac).|  
|**TrackerLogDirectory**|Необязательный параметр **String** .<br /><br /> Задает каталог для журнала отслеживания.|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)
