---
title: Отладка рабочих процессов с удаленного компьютера (прежние версии) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656847"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Отладка рабочих процессов с удаленного компьютера (для прежних версий)
В данном разделе описывается отладка удаленных приложений [!INCLUDE[wf](../includes/wf-md.md)] более ранней версии, построенных с помощью средства [!INCLUDE[wfd1](../includes/wfd1-md.md)] более ранней версии. Используйте средство [!INCLUDE[wfd2](../includes/wfd2-md.md)] более ранней версии, если приложение должно ориентироваться на [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 При установке [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] одним из вариантов установки компонента является установка [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] отладчика для [!INCLUDE[wf](../includes/wf-md.md)] . При этом устанавливаются компоненты удаленной отладки. Эти компоненты удаленной отладки должны быть установлены на компьютер, который будет использоваться в целях удаленной отладки рабочих процессов.

 Кроме того, сборка, содержащая определение рабочего процесса более ранней версии, отладка которого выполняется на удаленном компьютере, должна быть установлена в глобальный кэш сборок (GAC) на локальном компьютере, на котором выполняется отладка. Например, если рабочий процесс более ранней версии выполняется на удаленном компьютере А и его отладка выполняется с локального компьютера В, определение рабочего процесса должно находиться в GAC компьютера В. Это позволяет конструктору выполнить десериализацию и показать на компьютере В разметку рабочего процесса, который выполняется удаленно на компьютере А. Дополнительные сведения о глобальном кэше сборок (GAC) см. в библиотеке MSDN.

 [!INCLUDE[wf2](../includes/wf2-md.md)] Функция удаленной отладки аналогична удаленной отладке для других [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] компонентов. Дополнительные сведения см [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] . в разделе Удаленная отладка в библиотеке MSDN.

## <a name="see-also"></a>См. также:
 [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)