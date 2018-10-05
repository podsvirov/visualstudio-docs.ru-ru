---
title: 'Управляемая отладка: Рекомендуемые параметры свойств | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], managed
- debugging managed code, recommended property settings
ms.assetid: 3d14a8d4-2925-44d0-be41-ec546d411db9
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 50fa9b61d017be3e860c10f11688bcd79f252969
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559109"
---
# <a name="managed-debugging-recommended-property-settings"></a>Управляемая отладка: рекомендуемые параметры свойств
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [управляемых отладка: рекомендуемые параметры свойств](https://docs.microsoft.com/visualstudio/debugger/managed-debugging-recommended-property-settings).  
  
Некоторые свойства должны быть установлены одинаково для всех скриптов управляемой отладки.  
  
 В следующих таблицах приводятся рекомендованные параметры свойств.  
  
 Параметры, не указанные в данном списке, могут иметь различные значения для различных типов управляемых проектов. Например **действие при запуске** устанавливается по-разному в проекте Windows Forms, чем в [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] проекта.  
  
### <a name="configuration-properties-on-the-build-c-or-compile-visual-basic-tab"></a>Свойства конфигурации на вкладках "Построение" (C#) или "Компиляция" (Visual Basic)  
  
|**Имя свойства**|**Параметр**|  
|-----------------------|-----------------|  
|**Определить константу DEBUG**|C# и F#: установить флажок. Это позволяет приложению использовать класс Debug.|  
|**Определить константу TRACE**|C# и F#: установить флажок. Это позволяет приложению использовать класс Trace.|  
|**Оптимизировать код**|C# и F#: установить значение "false". Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если вы в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, можно включить этот параметр, но помните, что код, показанный на **Дизассемблированный код** окна формируется из оптимизированного источника и может не совпадать с вы видите в коде Редактор. Чтобы отладить оптимизированный код, необходимо отключить [Just My Code](just-my-code.md).<br /><br /> Дополнительные сведения см. в разделе [параметры проекта для конфигурации отладки C#](../debugger/project-settings-for-csharp-debug-configurations.md) или [параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).|  
|**Путь для создаваемых файлов**|Устанавливается равным bin\Debug\\.|  
|**Дополнительные параметры компиляции**|Только Visual Basic. Нажмите кнопку **Дополнительно** для задания дополнительных свойств, которые описаны в следующей таблице.|  
  
### <a name="advanced-compiler-settings-dialog-box"></a>Диалоговое окно "Дополнительные параметры компилятора"  
  
|**Имя свойства**|**Параметр**|  
|-----------------------|-----------------|  
|**Включить оптимизацию**|Установлено значение false в случаях, указанных в **оптимизировать код** параметр в предыдущей таблице.|  
|**Создает отладочную информацию**|Установите этот флажок, чтобы установить флаг "/Debug" для компиляции, что обеспечит создание информации, необходимой для упрощения отладки.|  
|**Определить константу DEBUG**|Установите этот флажок, чтобы определить константу `DEBUG`, которая позволяет приложению использовать класс <xref:System.Diagnostics.Debug>.|  
|**Определить константу TRACE**|Установите этот флажок, чтобы определить константу `TRACE`, которая позволяет приложению использовать класс <xref:System.Diagnostics.Trace>.|  
  
## <a name="see-also"></a>См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Типы проектов C#, F# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)


