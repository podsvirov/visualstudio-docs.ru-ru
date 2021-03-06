---
title: Как отключить предупреждения анализа кода для созданного кода | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52caadd7f4dd9349eccb80a366a1458212aba5ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646277"
---
# <a name="how-to-suppress-code-analysis-warnings-for-generated-code"></a>Практическое руководство. Отключение предупреждений анализа созданного кода
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Компиляторы управляемого кода часто создают код, который добавляется в проект для упрощения разработки кода. Кроме того, разработчики часто используют сторонние средства для быстрой разработки приложений. Эти средства также создают код, который добавляется в проект.

 Может потребоваться просмотреть нарушения правил, обнаруживаемые анализом кода в созданном коде. Однако вы, возможно, не хотите видеть их, если не можете просматривать и поддерживать код, содержащий нарушение.

 Флажок **подавлять результаты из созданного кода** на странице свойств анализ кода проекта позволяет выбрать, следует ли отображать предупреждения анализа кода из кода, созданного сторонним средством.

> [!NOTE]
> Этот параметр не подавляет ошибки анализа кода и предупреждения из созданного кода при появлении ошибок и предупреждений в формах и шаблонах. Вы можете просматривать и обслуживать исходный код для формы или шаблона.

### <a name="to-suppress-warnings-for-generated-code-in-a-project"></a>Отключение предупреждений для созданного кода в проекте

1. Щелкните правой кнопкой мыши проект в обозреватель решений и выберите пункт **Свойства**.

2. Щелкните **Анализ кода**.

3. Установите флажок **подавлять результаты из созданного кода** .
