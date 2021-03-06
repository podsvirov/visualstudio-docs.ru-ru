---
title: Добавление шаблонов проектов и элементов проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding
- project items [Visual Studio], adding
ms.assetid: 8c59217f-56e5-4540-a73b-cd10de189373
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14eb1a9e2e63fa6e63d3ba2efa4426421e6b5593
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710197"
---
# <a name="add-project-and-project-item-templates"></a>Добавление шаблонов проектов и элементов проектов
При создании собственных типов проектов необходимо обеспечить поддержку добавления новых проектов и элементов проектов с помощью стандартных [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] диалоговых окон интегрированной среды разработки (IDE). В следующих разделах рассматриваются различные методы добавления проектов и элементов проектов.

## <a name="in-this-section"></a>В этом разделе
- [Контекст проекта](../../extensibility/internals/project-context.md)

 Объясняет, что проект предоставляет большую часть контекстных сведений о том, что происходит в среде.

- [Приоритет проекта](../../extensibility/internals/project-priority.md)

 Объясняется, что элемент проекта обычно является членом одного проекта, чтобы избежать неоднозначности в том, какой проект используется для открытия элемента.

- [Проект прочих файлов](../../extensibility/internals/miscellaneous-files-project.md)

 Предоставляет сведения о двух типах редакторов, которые можно использовать для открытия файлов в проекте, и роль, которую играет проект при определении того, какой редактор следует использовать при открытии элемента проекта.

- [Регистрация шаблонов проектов и элементов](../../extensibility/internals/registering-project-and-item-templates.md)

 Объясняет, что происходит при [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] создании проекта.

- [Добавление элементов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)

 Описание процесса добавления элементов в диалоговое окно " **Добавление нового элемента** ".

- [Добавление каталогов в диалоговое окно "новый проект"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)

 Содержит пример регистрации нового каталога, содержащего пользовательские шаблоны, доступные в VSPackage.

- [Добавление каталогов в диалоговое окно "Добавление нового элемента"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

 Содержит пример регистрации нового набора каталогов для диалогового окна **Добавление нового элемента** .

- [Команды, определяемые интегрированной средой разработки для расширения систем проектов](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)

 Список различных типов командных элементов, используемых для расширения систем проектов.

- [CATID для объектов, которые обычно используются для расширения проектов](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

 Список CATID для объектов, используемых для расширения [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] систем проектов, и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .

## <a name="related-sections"></a>Связанные разделы
- [Пошаговое руководство. открытие редакторов, зависящих от проекта](../../extensibility/how-to-open-project-specific-editors.md)

 Содержит пошаговые инструкции по открытию элемента, привязанного к конкретному редактору для проекта.

- [Руководство. Открытие стандартных редакторов](../../extensibility/how-to-open-standard-editors.md)

 Содержит пошаговые инструкции по открытию стандартного редактора.

- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)

 Содержит ссылки на основные разделы о подтипах проектов. Подтипы проектов расширяют существующие [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] проекты и.

- [Типы проектов](../../extensibility/internals/project-types.md)

 Ссылки на дополнительные разделы, в которых содержатся сведения о проектировании новых типов проектов.
