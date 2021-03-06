---
title: Вызов отладчика для Windows Workflow Foundation (устаревший) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bcceca362f3c2a891d36f8f4e8071d0e35c8f164
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658982"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Вызов отладчика Visual Studio для Windows Workflow Foundation (для прежних версий)
В этом разделе описывается использование отладчика [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для отладки приложений [!INCLUDE[wf](../includes/wf-md.md)] в средстве [!INCLUDE[wfd1](../includes/wfd1-md.md)] прежних версий. [!INCLUDE[wfd2](../includes/wfd2-md.md)] прежних версий используется при создании приложений для [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] или [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Как правило, отладка рабочих процессов прежних версий аналогична отладке программ, написанных на других языках программирования Visual Studio. Запустить отладчик [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] для Windows Workflow Foundation можно следующими способами:

- Выберите **присоединить к процессу** в меню **Отладка** , чтобы выбрать запущенный экземпляр рабочего процесса из доступных процессов.

- Нажмите клавишу **F5** , чтобы начать выполнение экземпляра рабочего процесса или продолжить выполнение после попадания в точку останова.

## <a name="stepping-through-code"></a>Пошаговая отладка
 Отладчик поддерживает одну из самых характерных процедур отладки - отладку по шагам, которая представляет собой построчное выполнение кода. Для пошаговой отладки кода существует три команды:

- **Шаг**с заходом. можно выполнить шаг с заходом с помощью **F11**. Отладчик выполняет пошаговую отладку всех заданных обработчиков. Если обработчики не заданы, то действие пропускается, а в случае составного действия, которое содержит другие действия, выполняется вход в первое выполняющееся действие. Шаг с заходом в обработчики кода из конструктора не поддерживается для следующих действий: **IfElseActivity**, **WhileActivity**, **ConditionedActivityGroup**или **ReplicatorActivity**. Для отладки отладчиков, связанных с этими действиями, необходимо указать в коде явные точки останова.

- **Шаг с выходом**. можно выполнить шаг с выходом из действия, нажав **SHIFT + F11**. Выход из пошаговой отладки действия запускает текущее действие и все родственные действия на выполнение до завершения. Далее отладчик прерывается на текущем родительском объекте действия. При выходе из пошаговой отладки из кода обработчика, отладчик прерывается на действии, с которым связан обработчик.

- **Шаг с обходом**. можно выполнить шаг с обходом действия с помощью клавиши **F10**. При обходе составного действия. отладчик прерывается на первом исполняемом дочернем объекте составного действия. При пошаговом выполнении несоставного, такого как действие **CodeActivity** , отладчик выполняет действие и связанные с ним обработчики и прерывает выполнение следующего действия. Если выполняемое действие является последним дочерним действием в составном действии, то после выполнения отладчик прерывается на родительском действии.

## <a name="attaching-to-a-process"></a>Присоединение к процессу.
 Чтобы выполнить отладку рабочего процесса путем присоединения к процессу, выберите доступный процесс из списка **Доступные процессы** в диалоговом окне **Присоединение к процессу** . Если **автоматически: код рабочего процесса** не отображается в текстовом поле **присоединить к** », нажмите кнопку **выбрать**. В диалоговом окне **Выбор типа кода** щелкните **Отладка этих типов кода** и выберите **Рабочий процесс**. Затем нажмите кнопку **ОК** и выберите команду **присоединить**.

## <a name="debugging-with-f5"></a>Отладка по клавише F5
 Если приложение рабочего процесса и библиотека DLL рабочего процесса расположены в разных проектах Visual Studio, например при использовании библиотеки действий рабочих процессов, необходимо задать проект DLL рабочего процесса в качестве запускаемого проекта Visual Studio для отладки рабочего процесса с помощью **клавиши F5**. Необходимо также задать путь к ведущему приложению в свойстве **запуска внешней программы** проекта DLL рабочего процесса.

 Чтобы задать запускаемый проект в обозреватель решений, щелкните правой кнопкой мыши имя проекта и выберите **Назначить запускаемым проектом**. Чтобы задать путь к узлу в свойстве **Запуск внешней программы** , дважды щелкните узел " **свойства** " проекта рабочего процесса в Обозреватель решений и выберите вкладку " **Отладка** ". В разделе **действие при запуске**выберите **Запуск внешней программы** и введите путь к EXE-файлу, содержащему рабочий процесс, который требуется отладить.

 Если ведущее приложение задано как автозагружаемый проект, то для отладки вызывается только отладчик Visual Studio; отладчик [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] для Windows Workflow Foundation не вызывается. Если используется отладчик Visual Studio, то попадание будет производится только в точки останова кода C# или Visual Basic; в точки останова, заданные в конструкторе рабочих процессов, попадание не выполняется. Например, попадание в точку останова, которая задана в конструкторе в действии <xref:System.Workflow.Activities.ParallelActivity> выполняется, если используется отладчик [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] для Windows Workflow Foundation, но не при использовании отладчика Visual Studio.

## <a name="see-also"></a>См. также:
 [Как задать точки останова в рабочих процессах (устаревший)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [Отладка устаревших рабочих процессов](../workflow-designer/debugging-legacy-workflows.md)