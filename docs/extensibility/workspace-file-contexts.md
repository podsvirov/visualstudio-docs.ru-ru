---
title: Контексты файлов рабочей области в Visual Studio | Документация Майкрософт
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 36f986db6f2c7b483b46060e1f514acc8dd9e758
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952819"
---
# <a name="workspace-file-contexts"></a>Контексты файлов рабочей области

Все аналитические данные в рабочих областях [открытых папок](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) создаются "поставщиками контекста файлов", которые реализуют <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> интерфейс. Эти расширения могут искать закономерности в папках или файлах, читать файлы MSBuild и Makefile, определять зависимости пакетов и т. д., чтобы накапливать ценные сведения, необходимые для определения контекста файла. Сам по себе контекст файла не выполняет никаких действий, а предоставляет данные, которые затем может выполнять другое расширение.

<xref:Microsoft.VisualStudio.Workspace.FileContext>У каждого есть `Guid` связанный с ним объект, который определяет тип данных, которые он передает. Рабочая область использует это `Guid` позднее для сопоставления с расширениями, которые потребляют данные через <xref:Microsoft.VisualStudio.Workspace.FileContext.Context> свойство. Поставщик контекста файла экспортируется с метаданными, определяющими контекст файла, `Guid` для которого он может создавать данные.

После определения контекст файла может быть связан с любым количеством файлов или папок в рабочей области. Данный файл или папка могут быть связаны с любым количеством контекстов файлов. Это связь «многие ко многим».

Наиболее распространенные сценарии для контекстов файлов связаны со службами сборки, отладки и языка. Дополнительные сведения см. в других разделах, относящихся к этим сценариям.

## <a name="file-context-lifecycle"></a>Жизненный цикл контекста файла

Жизненные циклы для a `FileContext` не являются детерминированными. В любое время компонент может асинхронно запрашивать некоторый набор типов контекста. Будут запрошены поставщики, поддерживающие определенное подмножество типов контекста запроса. `IWorkspace`Экземпляр выступает в качестве среднего человека между потребителем и поставщиками через <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> метод. Потребители могут запросить контекст и выполнить некоторое краткосрочное действие на основе контекста, тогда как другие могут запросить контекст и поддерживать долгосрочную ссылку.

Изменения могут происходить для файлов, которые приводят к тому, что контекст файла становится устаревшим. Поставщик может запустить событие в, `FileContext` чтобы уведомить потребителей об обновлениях. Например, если для какого-либо файла указан контекст сборки, но изменение на диске сделает этот контекст недействительным, то исходный производитель может вызвать событие. Все потребители, на которые все еще ссылаются, `FileContext` могут затем запросить новое `FileContext` .

>[!NOTE]
>Нет модели push-уведомлений для потребителей. Потребители не будут уведомлены о новом поставщике `FileContext` после своего запроса.

## <a name="expensive-file-context-computations"></a>Ресурсоемкие вычисления в контексте файлов

Чтение содержимого файла с диска может быть дорогостоящим, особенно если поставщику требуется разрешить связь между файлами. Например, поставщик может запрашиваться для некоторого контекста файла исходного файла, но контекст файла зависит от метаданных из файла проекта. Анализ файла проекта или его оценка с помощью MSBuild является дорогостоящей. Вместо этого расширение может экспортировать, `IFileScanner` чтобы создавать `FileDataValue` данные во время индексирования рабочей области. Теперь при запросе на контексты файлов `IFileContextProvider` можно быстро запросить эти индексированные данные. Дополнительные сведения об индексировании см. в разделе [индексирование рабочей области](workspace-indexing.md) .

>[!WARNING]
>Будьте осторожны с другими способами, `FileContext` которые могут быть затратными для вычислений. Некоторые взаимодействия пользовательского интерфейса являются синхронными и основываются на большом объеме `FileContext` запросов. Примеры включают открытие вкладки редактора и открытие **Обозреватель решений** контекстного меню. Эти действия делают множество запросов типов контекста сборки.

## <a name="file-context-related-apis"></a>API, связанные с контекстом файла

- <xref:Microsoft.VisualStudio.Workspace.FileContext> содержит данные и метаданные.
- <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider> и <xref:Microsoft.VisualStudio.Workspace.IFileContextProvider`1> Создайте контекст файла.
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextProviderAttribute> экспортирует поставщик контекста файла.
- <xref:Microsoft.VisualStudio.Workspace.IWorkspace.GetFileContextsAsync%2A> используется для получения контекстов файлов для потребителей.
- <xref:Microsoft.VisualStudio.Workspace.Build.BuildContextTypes> Определяет типы контекста сборки, которые будут использоваться при открытии папки.

## <a name="file-context-actions"></a>Действия контекста файла

Хотя `FileContext` сам по себе представляет собой только данные о некоторых файлах, <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> а — это способ выразить эти данные и работать с ними. `IFileContextAction` гибкость при использовании. Два из наиболее распространенных случаев — сборка и отладка.

## <a name="reporting-progress"></a>Отчеты о ходе выполнения

<xref:Microsoft.VisualStudio.Workspace.IFileContextActionBase.ExecuteAsync%2A>Метод передается `IProgress<IFileContextActionProgressUpdate>` , но аргумент не должен использоваться как этот тип. `IFileContextActionProgressUpdate` является пустым интерфейсом, и вызов `IProgress<IFileContextActionProgressUpdate>.Report(IFileContextActionProgressUpdate)` может вызвать исключение `NotImplementedException` . Вместо этого `IFileContextAction` аргумент должен приводить к другому типу, если это необходимо для сценария.

Сведения о типах, предоставляемых Visual Studio, см. в документации по соответствующему сценарию.

## <a name="file-context-action-related-apis"></a>API-интерфейсы, связанные с действием контекста файла

- <xref:Microsoft.VisualStudio.Workspace.IFileContextAction> выполняет определенное поведение на основе `FileContext` .
- <xref:Microsoft.VisualStudio.Workspace.IFileContextActionProvider> создает экземпляры `IFileContextAction` .
- <xref:Microsoft.VisualStudio.Workspace.ExportFileContextActionProviderAttribute> экспортирует тип `IWorkspaceProviderFactory<IFileContextActionProvider>` .

## <a name="file-watching"></a>Наблюдение за файлами

Рабочая область прослушивает уведомления об изменении файлов и предоставляет <xref:Microsoft.VisualStudio.Workspace.IFileWatcherService> протокол VIA <xref:Microsoft.VisualStudio.Workspace.WorkspaceServiceHelper.GetFileWatcherService%2A> . Файлы, соответствующие параметру "Ексклудедитемс", не будут создавать события уведомления о файлах. Пороговое значение между событиями используется для упрощения уведомлений и уменьшения числа повторений. Если необходимо реагировать на изменение файла, следует подписываться на эту службу.

>[!TIP]
>[Служба индексирования](workspace-indexing.md) рабочей области подписывается на события файлов по умолчанию. Добавление и изменение файлов приведет к `IFileScanner` вызову соответствующих событий s для новых данных для этого файла. Удаление файлов приведет к удалению индексированных данных. Вам не нужно подписываться `IFileScanner` на службу наблюдателя файлов.

## <a name="next-steps"></a>Дальнейшие действия

* [Индексирование](workspace-indexing.md) — индексирование рабочей области собирает и сохраняет сведения о рабочей области.
* [Рабочие области](workspaces.md) — проверьте основные понятия и хранилище параметров рабочей области.
