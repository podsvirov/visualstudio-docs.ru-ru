---
title: Директива сборки T4 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 44949749-ce3c-4fb5-8690-a17f1564ac2f
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bc0e6e7e1530abb63beabc6fa4aedd4a0fa985af
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672341"
---
# <a name="t4-assembly-directive"></a>Директива Assembly T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В текстовом шаблоне времени проектирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] директива `assembly` загружает сборку, чтобы в коде шаблона можно было использовать ее типы. Это дает эффект, аналогичный добавлению ссылки на сборку в проекте [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Общие сведения о создании текстовых шаблонов см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> В текстовом шаблоне времени выполнения (предварительно обработанном) директива `assembly` не требуется. Вместо этого добавьте необходимые сборки в **ссылки** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проекта.

## <a name="using-the-assembly-directive"></a>Использование директивы Assembly
 Синтаксис директивы таков:

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

 Имя сборки должно быть одним из следующих:

- Строгое имя сборки в глобальном кэше сборок, такое как `System.Xml.dll`. Кроме того, можно использовать полную форму, такую как `name="System.Xml, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"`. Для получения дополнительной информации см. <xref:System.Reflection.AssemblyName>.

- абсолютный путь к сборке;

  Синтаксис `$(variableName)` можно использовать для ссылки на переменные [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], такие как `$(SolutionDir)`, а синтаксис `%VariableName%` — для ссылки на переменные среды. Пример:

```
<#@ assembly name="$(SolutionDir)\MyProject\bin\Debug\SomeLibrary.Dll" #>
```

 В предварительно преобразованном текстовом шаблоне директива assembly не производит никакого эффекта. Вместо этого включите необходимые ссылки в раздел **ссылок** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] проекта. Дополнительные сведения см. [в разделе Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="standard-assemblies"></a>Стандартные сборки
 Следующие сборки загружаются автоматически, поэтому для них не нужно создавать директивы сборки:

- `Microsoft.VisualStudio.TextTemplating.1*.dll`

- `System.dll`

- `WindowsBase.dll`

  При использовании пользовательской директивы процессор директив может загружать дополнительные сборки. Например, при создании шаблонов для доменного языка (DSL) не требуется создавать директивы сборки для следующих сборок:

- `Microsoft.VisualStudio.Modeling.Sdk.1*.dll`

- `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.1*.dsl`

- `Microsoft.VisualStudio.TextTemplating.Modeling.1*.dll`

- Сборка, содержащая DSL.

## <a name="using-project-properties-in-both-msbuild-and-visual-studio"></a><a name="msbuild"></a> Использование свойств проекта в MSBuild и Visual Studio
 Макросы Visual Studio, такие как $(SolutionDir), не работают в MSBuild. Если требуется преобразовывать шаблоны на компьютере сборки, необходимо использовать свойства проекта.

 Измените CSPROJ- или VBPROJ-файл для определения свойства проекта. В этом примере определяется свойство с именем `myLibFolder`.

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>

```

 Теперь можно использовать свойство проекта в текстовых шаблонах, которые будут правильно преобразовываться как в Visual Studio, так и в MSBuild:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
```

## <a name="see-also"></a>См. также:
 [Директива Include T4](../modeling/t4-include-directive.md)
