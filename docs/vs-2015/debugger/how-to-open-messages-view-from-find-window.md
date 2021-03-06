---
title: Практическое руководство. Открытие представления сообщений из окна поиска | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Messages View in Spy++, opening
- opening Messages View in Spy++
ms.assetid: 601a193e-432a-417b-9406-6fec9e401264
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee29135e659eff7e4965b6b1fb0d24de2c2e90cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157883"
---
# <a name="how-to-open-messages-view-from-find-window"></a>Практическое руководство. открытие представления сообщений из окна поиска
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Иногда бывает удобно использовать диалоговое окно **Поиск окна** для выбора целевого окна, а затем открывать представление сообщений для этого окна.  
  
### <a name="to-open-a-messages-view-window-using-the-find-window-dialog-box"></a>Открытие окна представления сообщений с помощью диалогового окна "Поиск окна"  
  
1. Расположите окна так, чтобы были видны и окно Spy++, и целевое окно.  
  
2. В меню **Spy** выберите пункт **Поиск окна**.  
  
     Откроется [диалоговое окно "Поиск окна"](../debugger/find-window-dialog-box.md).  
  
3. Из вкладки **Windows** перетащите **инструмент поиска** в целевое окно. В процессе перетаскивания в диалоговом окне **Поиск окна** отображаются сведения о выбранном окне.  
  
     — или —  
  
     Если у вас есть дескриптор нужного окна (например, скопированный из отладчика), вы можете ввести его в текстовое поле **Дескриптор**.  
  
4. В разделе **Показать** выберите **Сообщения**.  
  
5. Нажмите кнопку **ОК**.  
  
     Откроется пустое окно [Представление сообщений](../debugger/messages-view.md), а на панели инструментов Spy++ появится меню **Сообщения**.  
  
6. В меню **Сообщения** выберите **Параметры ведения журнала**.  
  
     Откроется диалоговое окно [Параметры сообщений](../debugger/message-options-dialog-box.md).  
  
7. Отметьте те сообщения, которые хотите отобразить.  
  
8. Нажмите **ОК**, чтобы начать запись сообщений в журнал.  
  
     В зависимости от выбранных параметров, сообщения будут поступать в активное окно представления сообщений.  
  
9. Получив достаточное количество сообщений, выберите **Остановить ведение журнала** в меню **Сообщения**.
