---
title: Архитектура типов проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706322"
---
# <a name="project-types-architecture"></a>Архитектура типов проектов
В этом разделе содержатся подробные сведения об архитектуре типов проектов в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>в этом разделе
- [Элементы модели проекта](../../extensibility/internals/elements-of-a-project-model.md)

 Перечисляет службы, которые может использовать тип проекта, и интерфейсы, которые он должен реализовать.

- [Основные компоненты модели проекта](../../extensibility/internals/project-model-core-components.md)

 Описывает типы проектов интерфейсов, которые должны быть реализованы и могут быть реализованы для предоставления дополнительных функциональных возможностей.

- [Когда следует создавать типы проектов](../../extensibility/internals/when-to-create-project-types.md)

 Помогает решить, когда необходимо создать тип проекта, а также можно использовать другие [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] функции расширяемости, такие как пакеты VSPackage и редакторы, для достижения той же цели.

- [Иерархии и выбор](../../extensibility/internals/hierarchies-and-selection.md)

 Описывает использование [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] иерархий и контекста выбора для обеспечения единообразного и упрощенного взаимодействия с пользователем.

## <a name="related-sections"></a>См. также
- [Подтипы проектов](../../extensibility/internals/project-subtypes.md)

 Объясняет, как подтипы проектов позволяют настраивать поведение систем проектов [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

- [Типы проектов](../../extensibility/internals/project-types.md)

 Содержит общие сведения о проектах в качестве основных стандартных блоков [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Имеются ссылки на дополнительные разделы, объясняющие, как проекты управляют сборкой и компиляцией кода.
