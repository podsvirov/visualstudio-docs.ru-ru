---
title: Использование задачи AspNetCompiler для предварительной компиляции ASP.NET
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 43b7ccc11e8d265c0b1490e7e8de0bd33d903904
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036188"
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler - задача

Задача `AspNetCompiler` создает оболочку для программы *aspnet_compiler.exe*, которая выполняет предварительную компиляцию приложений ASP.NET.

## <a name="task-parameters"></a>Параметры задачи

В следующей таблице приводятся параметры задачи `AspNetCompiler` .

|Параметр|Описание|
|---------------|-----------------|
|`AllowPartiallyTrustedCallers`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, сборка со строгим именем допускает вызовы с частичным доверием.|
|`Clean`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, то для предварительно скомпилированного приложения будет выполнена чистая сборка. Все ранее скомпилированные компоненты будут перекомпилированы. Значение по умолчанию — `false`. Этот параметр соответствует параметру командной строки **-c** для *aspnet_compiler.exe*.|
|`Debug`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, то во время компиляции создается отладочная информация (PDB-файл). Значение по умолчанию — `false`. Этот параметр соответствует параметру командной строки **-d** для *aspnet_compiler.exe*.|
|`DelaySign`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, сборка не подписывается полностью при создании.|
|`FixedNames`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, скомпилированным сборкам будут присвоены фиксированные имена.|
|`Force`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, задача перезаписывает конечный каталог, если он уже существует. Все содержимое каталога будет утеряно. Значение по умолчанию — `false`. Этот параметр соответствует параметру командной строки **-f** для *aspnet_compiler.exe*.|
|`KeyContainer`|Необязательный параметр `String`.<br /><br /> Задает контейнер ключа для строгого имени.|
|`KeyFile`|Необязательный параметр `String`.<br /><br /> Указывает физический путь к файлу ключа для строгого имени.|
|`MetabasePath`|Необязательный параметр `String`.<br /><br /> Указывает полный путь к метабазе IIS приложения. Этот параметр нельзя использовать вместе с параметром `VirtualPath` или `PhysicalPath`. Этот параметр соответствует параметру командной строки **-m** для *aspnet_compiler.exe*.|
|`PhysicalPath`|Необязательный параметр `String`.<br /><br /> Указывает физический путь к компилируемому приложению. Если этот параметр отсутствует, для поиска приложения используется метабаза IIS. Этот параметр соответствует параметру командной строки **-p** для *aspnet_compiler.exe*.|
|`TargetFrameworkMoniker`|Необязательный параметр `String`.<br /><br /> Задает параметр TargetFrameworkMoniker, который определяет используемую версию .NET Framework для *aspnet_compiler.exe*. Принимает только моникеры платформы .NET Framework.|
|`TargetPath`|Необязательный параметр `String`.<br /><br /> Указывает физический путь, по которому компилируется приложение. Если этот параметр не указан, приложение предкомпилируется на месте.|
|`Updateable`|Необязательный параметр `Boolean`.<br /><br /> Если этот параметр имеет значение `true`, то предкомпилированное приложения будет обновляемым.  Значение по умолчанию — `false`. Этот параметр соответствует параметру командной строки **-u** для *aspnet_compiler.exe*.|
|`VirtualPath`|Необязательный параметр `String`.<br /><br /> Виртуальный путь к компилируемому приложению. Если указан параметр `PhysicalPath`, для поиска приложения используется физический путь. В противном случае используется метабаза IIS, и предполагается, что приложение расположено в узле по умолчанию. Этот параметр соответствует параметру командной строки **-v** для *aspnet_compiler.exe*.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>Пример

В следующем примере кода задача `AspNetCompiler` выполняет предварительную компиляцию приложения ASP.NET.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="PrecompileWeb">
        <AspNetCompiler
            VirtualPath="/MyWebSite"
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"
            TargetPath="c:\precompiledweb\MyWebSite\"
            Force="true"
            Debug="true"
        />
    </Target>
</Project>
```

## <a name="see-also"></a>См. также

* [Задачи](../msbuild/msbuild-tasks.md)
* [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
