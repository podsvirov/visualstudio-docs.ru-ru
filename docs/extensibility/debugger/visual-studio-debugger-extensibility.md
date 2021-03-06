---
title: Расширяемость отладчика Visual Studio | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712502"
---
# <a name="visual-studio-debugger-extensibility"></a>Расширяемость отладчика Visual Studio
Visual Studio включает в себя полностью интерактивный отладчик исходного кода, предоставляющий мощный и простой в использовании инструмент для отслеживания ошибок в программе. Отладчик имеет полную поддержку для Visual Basic, C#, C/C++ и JavaScript. Однако в [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , который доступен в [центре загрузки Майкрософт](https://www.microsoft.com/download/details.aspx?id=21835), другие языки программирования могут поддерживаться в отладчике с теми же широкими возможностями.

 Отладчик является общим интерфейсным интерфейсом [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (таким, как пользовательского интерфейса) для отладочных компонентов, которые, в свою очередь, специфичны для отлаживаемого языка. Для новых языков, необходимых для поддержки [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладчика, необходимо создать необходимые серверные компоненты, такие как модуль отладки (de). Это место, где [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] входит в.

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Содержит полную ссылку на все элементы, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимые для создания нового de. Кроме того, есть примеры и учебники, которые помогут вам приступить к работе.

 Полный пример системы проектного языка с поддержкой отладки см. в [образце IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 В следующих разделах описывается расширение отладчика с помощью [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>В этом разделе
 [Начало работы](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Описание [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] предложений по отладке и установки пакета SDK.

 [Создание пользовательского модуля отладки](../../extensibility/debugger/creating-a-custom-debug-engine.md) Документирует пользовательский процесс DE, от подготовки программы к отсоединению de.

 [Написание вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Объясняет, нужно ли писать средство оценки выражений.

 [Выбор стратегии реализации модуля отладки](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Описывает, как реализовать метод DE.

 [Справочные материалы](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Документирует [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API отладки.

 [Примеры](../../extensibility/debugger/visual-studio-debugging-samples.md) Содержит ссылки на пример средства оценки выражений среды CLR и пример модуля отладки.
