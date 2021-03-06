---
title: Окно "Вывод", узел "Отладка", диалоговое окно "Параметры" | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.options.OutputWindow
- VS.ToolsOptionsPages.Debugger.OutputWindow
- vs.debug.options.Output
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: d67387c2-39e9-4790-93bc-e41bff12fb9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9224258a2dfd48cc17ed15f9723e455e225af8b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904791"
---
# <a name="output-window-debugging-options-dialog-box"></a>Окно "Вывод", узел "Отладка", диалоговое окно "Параметры"
Существует возможность указывать типы отладочной информации, появляющейся в окне **Вывод**. Для отображения этих параметров откройте меню **Сервис**, выберите пункт **Параметры**, разверните узел **Отладка** и выберите **Окно вывода**.

**Общие параметры вывода.** В этой категории содержатся элементы, управляющие появлением общих сообщений отладки в окне **Вывод**. Здесь можно указать, какие типы сообщений будут отображаться.

**Параметры трассировки WPF.** В этой категории содержатся элементы управления, позволяющие определить уровень сообщений трассировки WPF, появляющихся в окне **Вывод**. Здесь можно задать тип отображаемых сообщений и уровень: от значения **Критический** до значения **Все**.

Дополнительные сведения см. в разделе [Практическое руководство. отобразить данные трассировки WPF](../debugger/how-to-display-wpf-trace-information.md).

Чтобы восстановить параметры по умолчанию, выберите **Сервис** > **Импорт и экспорт параметров** > **Сбросить все параметры**. Если требуется только сбросить несколько параметров, сохраните их в мастере **импорта и экспорта параметров** перед внесением изменений, которые нужно протестировать, а затем импортируйте сохраненные параметры.

## <a name="see-also"></a>См. также
- [Папка "Отладка", диалоговое окно "Параметры"](../debugger/debugging-options-dialog-box.md)
- [Окно выходных данных](../ide/reference/output-window.md)