---
title: Включение и выключение режима "Изменить и продолжить" | Документация Майкрософт
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: ce531a0f7f9d6e26db38b5cf041f06d42209261a
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851402"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Практическое руководство. Включение и выключение режима "Изменить и продолжить" (C#, VB, C++)

Режим **Изменить и продолжить** можно включить или отключить во время разработки в диалоговом окне **Параметры** в Visual Studio. Операция **Изменить и продолжить** работает только в отладочных сборках. Дополнительные сведения см. в разделе [Изменить и продолжить](../debugger/edit-and-continue.md).

В случае машинного кода C++ для режима **Изменить и продолжить** необходимо использовать параметр `/INCREMENTAL`. Дополнительные сведения о требованиях для компонентов в C++ см. в этой [записи блога](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) и статье о режиме ["Изменить и продолжить" (C++)](../debugger/edit-and-continue-visual-cpp.md).

**Включение и отключение режима "Изменить и продолжить"**

1. Если вы находитесь в сеансе отладки, остановите отладку (**Отладка** > **Остановить отладку** или сочетанием клавиш **SHIFT**+**F5**).

1. В разделе **Средства** > **Параметры** (или **Отладка** > **Параметры**) > **Отладка** > **Общие** в области справа выберите **Изменить и продолжить**.

    > [!NOTE]
    > Если включено средство IntelliTrace и собираются как события IntelliTrace, так и сведения о вызовах, операция "Изменить и продолжить" становится недоступна. Дополнительные сведения см. в статье об [IntelliTrace](../debugger/intellitrace.md).

1. В случае с кодом C++ убедитесь, что установлен флажок **Включить функцию "Изменить машинный код и продолжить"** , и задайте дополнительные параметры:
    - **Применить изменения при продолжении (только машинный код)**

      Если этот флажок установлен, Visual Studio автоматически компилирует и применяет изменения кода при продолжении отладки из состояния останова. В противном случае можно выбрать применение изменений с помощью команд **Отладка** > **Применить изменения кода**.

    - **Предупреждать об устаревшем коде (только машинный код)**

      Если этот флажок установлен, появляются предупреждения об устаревшем коде.

1. Нажмите кнопку **ОК**.
