---
title: Регистрация окна инструментов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d7b82353247776eb2dac8135a0a412b396d571a1
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584720"
---
# <a name="register-a-tool-window"></a>Регистрация окна инструментов
Вы можете зарегистрировать окна инструментов с помощью <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> и  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> .

## <a name="example"></a>Пример

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 В приведенном выше коде <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> регистрирует `PersistedWindowPane` `DynamicWindowPane` окна инструментов и в Visual Studio. Окно сохраненного инструмента закреплено с **Обозреватель решений**, а динамическому окну дается начальное положение и размер по умолчанию. Динамическое окно становится временным, что означает, что он не создается при запуске. При этом записывается `DontForceCreate` значение `ToolWindows` ключа в системном реестре. Дополнительные сведения см. в разделе [Настройка экрана окна инструментов](../vs-2015/extensibility/tool-window-display-configuration.md?view=vs-2015&preserve-view=true).