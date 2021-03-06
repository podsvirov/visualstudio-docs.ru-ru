---
title: Диалоговое окно "Исполняемый файл для сеанса отладки" | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exefordebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- executable files, specifying when debugging
- DLLs, debugging
- debugger, Executable for Debugging Session dialog box
- Executable for Debugging Session dialog box
ms.assetid: c0ddbe32-b99f-4425-acf1-f48842804f56
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92cf53ed499318d60c8da5147685e3f0f340e404
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736237"
---
# <a name="executable-for-debugging-session-dialog-box"></a>Исполняемый файл для сеанса отладки - диалоговое окно

Это диалоговое окно появляется при попытке выполнить отладку библиотеки DLL, для которой не указан исполняемый файл. Visual Studio не может запустить библиотеку DLL непосредственно. Вместо этого Visual Studio запускает указанный исполняемый файл. Отладку библиотеки DLL можно выполнить, когда она будет вызвана исполняемым файлом.

 **Имя исполняемого файла.** Введите путь к исполняемому файлу, который вызовет отлаживаемую библиотеку DLL.

 **URL-адрес, по которому можно получить доступ к проекту (только для ATL-сервера).** Если выполняется отладка библиотеки DLL сервера ATL, введите URL-адрес, по которому может быть найден проект.

 Определенные параметры хранятся в страницах свойств проекта, поэтому в последующих сеансах отладки повторно задавать их не нужно. Если возникнет необходимость в их изменении, можно открыть окно "Страницы свойств" и задать требуемые значения. Дополнительные сведения об указании исполняемого файла для сеанса отладки см. в разделе [Отладка библиотек DLL](../debugger/how-to-debug-from-a-dll-project.md).

## <a name="see-also"></a>См. также

- [Отладка в Visual Studio](../debugger/index.yml)
- [Первое знакомство с отладчиком](../debugger/debugger-feature-tour.md)