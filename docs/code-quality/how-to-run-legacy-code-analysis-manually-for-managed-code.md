---
title: Запуск анализа прежних версий вручную (.NET)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ca865b33d59f87453cafc337e1595c9d772b17a2
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808617"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Как выполнить анализ кода прежних версий вручную для управляемого кода

Средство анализа кода предоставляет сведения о возможных дефектах в исходном коде. Вы можете выполнять анализ кода автоматически при каждой сборке проекта кода, а также выполнять анализ кода вручную. Правила, проверяемые при выполнении анализа кода, указываются на странице "анализ кода" страниц свойств проекта. Дополнительные сведения см. [в разделе инструкции. Настройка анализа кода для проекта управляемого кода](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Запуск анализа кода вручную

1. Если вы используете Visual Studio 2019 версии 16,5 или более поздней, перед запуском Visual Studio выполните в командной строке следующую команду:

```
set EnableLegacyCodeAnalysis = true
```

2. В **Обозреватель решений**щелкните проект.

3. В меню **анализ** выберите пункт **выполнить анализ кода для** *имени проекта*.
