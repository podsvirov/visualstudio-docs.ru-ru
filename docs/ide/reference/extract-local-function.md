---
title: Извлечение локальной функции
description: Чтобы преобразовать фрагмент кода в его собственный метод, выберите код и нажмите CTRL+R, CTRL+M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77519329"
---
# <a name="extract-local-function-refactoring"></a>Извлечение рефакторинга локальной функции

Область применения этого рефакторинга:

- C#

**Что?** Позволяет преобразовать фрагмент кода из существующего метода в локальную функцию.

**Когда?** Если в каком-либо методе существует фрагмент кода, который должен вызываться из локальной функции.

**Зачем?** Вы можете скопировать и вставить этот код, но это приведет к дублированию. Лучшим решением является рефакторинг этого фрагмента в собственную локальную функцию.

## <a name="how-to"></a>Практические советы

1. Выделите код, который требуется извлечь.

2. Нажмите клавиши **CTRL**+ **.** чтобы открыть меню **Быстрые действия и рефакторинг**. 

3. Выберите **Извлечь локальную функцию**.

    ![Извлечение локальной функции](media/extract-local-function.png)

## <a name="see-also"></a>См. также

- [Рефакторинг](../refactoring-in-visual-studio.md)
- [Просмотр изменений](../../ide/preview-changes.md)
