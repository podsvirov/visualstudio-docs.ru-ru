---
title: Добавление параметров командной строки | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562280"
---
# <a name="adding-command-line-switches"></a>Добавление параметров командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При выполнении devenv.exe можно добавить параметры командной строки, которые применяются к пакету VSPackage. Используйте <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> для объявления имени переключателя и его свойств. В этом примере параметр Мисвитч добавляется для подкласса VSPackage с именем **аддкоммандсвитчпаккаже** без аргументов и при этом автоматически загружается пакетом VSPackage.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Именованные параметры показаны в следующей таблице.  
  
 Аргументы  
 Число аргументов для переключателя. Может быть "*" или списком аргументов.  
  
 DemandLoad  
 Загружать VSPackage автоматически, если задано значение 1, в противном случае — значение 0.  
  
 HelpString  
 Строка справки или идентификатор ресурса строки, отображаемой с помощью **команды devenv/?**.  
  
 Имя  
 Параметр.  
  
 PackageGuid  
 Идентификатор GUID пакета.  
  
 Первое значение аргумента обычно равно 0 или 1. Специальное значение "*" можно использовать для указания того, что весь остаток командной строки является аргументом. Это может быть полезно для сценариев отладки, в которых пользователь должен передать командную строку отладчика.  
  
 Значение DemandLoad либо `true` (1), либо `false` (0) указывает, что пакет VSPackage должен быть загружен автоматически.  
  
 Значение HelpString — это идентификатор ресурса строки, которая отображается в devenv/? Отображение справки. Это значение должно быть в формате "#nnn", где NNN — целое число. Строковое значение в файле ресурсов должно заканчиваться символом новой строки.  
  
 Значение Name — это имя переключателя.  
  
 Значение PackageGuid — это идентификатор GUID пакета, который реализует этот параметр. Интегрированная среда разработки использует этот идентификатор GUID для поиска пакета VSPackage в реестре, к которому применяется параметр командной строки.  
  
## <a name="retrieving-command-line-switches"></a>Получение параметров командной строки  
 После загрузки пакета можно получить параметры командной строки, выполнив следующие действия.  
  
1. В <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации VSPackage вызовите on, `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> чтобы получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> интерфейс.  
  
2. Вызовите метод, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> чтобы получить параметры командной строки, которые пользователь указал.  
  
   В следующем коде показано, как определить, была ли указана пользователем команда Мисвитч в командной строке:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 Вы обязаны проверять параметры командной строки каждый раз при загрузке пакета.  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Параметры командной строки для команды devenv](../ide/reference/devenv-command-line-switches.md)   
 [Служебная программа CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [Файлы .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
