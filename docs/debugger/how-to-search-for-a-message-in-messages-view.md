---
title: Поиск сообщения в представлении сообщений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Message Search dialog box
- Messages view
- messages, searching for
ms.assetid: 732b7ccc-54ea-41db-823b-2b96e3e4083e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c4b597870d7a87b396b4c6e828da814c49f9bfb
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852013"
---
# <a name="how-to-search-for-a-message-in-messages-view"></a>Практическое руководство. поиск сообщения в представлении сообщений
В представлении сообщений вы можете найти конкретное сообщение по значению его дескриптора, типа или идентификатора. Допустимым критерием для поиска считается любое из этих свойств или любое их сочетание. Также вы можете указать начальное направление поиска. Поля в диалоговом окне предварительно заполняются атрибутами текущего выбранного окна.

### <a name="to-search-for-a-message-in-messages-view"></a>Поиск сообщения в представлении сообщений

1. Расположите окна так, чтобы были видны окно Spy++ и активное окно [Представление сообщений](../debugger/messages-view.md).

2. В меню **Поиск** выберите **Найти сообщение**.

    Откроется [диалоговое окно "Поиск сообщений"](../debugger/message-search-dialog-box.md).

3. Перетащите **инструмент поиска** на нужное окно. В процессе перетаскивания в диалоговом окне **Поиск сообщения** отображаются сведения о выбранном окне.

   - или

     Если у вас есть дескриптор окна, в котором вы хотите изучить сообщения, введите его в текстовое поле **Дескриптор**.

   - или

     Если вам известны тип и (или) идентификатор нужного сообщения, выберите соответствующие значения в раскрывающихся меню **Тип** и **Сообщение**, а также очистите текстовое поле **Дескриптор**.

4. Очистите все поля, в которых не нужно указывать значения.

   > [!TIP]
   > Чтобы на экране было меньше беспорядка, поставьте флажок **Скрыть Spy**. Этот параметр скрывает главное окно Spy++, а поверх других приложений отображается только диалоговое окно **Поиск окна**. Главное окно Spy++ восстанавливается при нажатии кнопки **ОК** или **Отмена** или при снятии флажка **Скрыть Spy++** .

5. Нажимайте кнопки **Вверх** или **Вниз**, чтобы выбрать начальное направление поиска.

6. Нажмите кнопку **ОК**.

   Если будет найдено подходяще сообщение, оно выделяется в окне "Представление сообщений". Подробнее о представлении сообщений см. [здесь](../debugger/messages-view.md).