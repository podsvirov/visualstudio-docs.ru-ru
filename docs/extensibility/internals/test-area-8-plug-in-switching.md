---
title: Область тестирования 8. Переключение подключаемых модулей | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704391"
---
# <a name="test-area-8-plug-in-switching"></a>Область тестирования 8. Переключение подключаемых модулей
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Интегрированная среда разработки (IDE) имеет пользовательский интерфейс для изменения текущего подключаемого модуля системы управления версиями. Эта область тестирования содержит тестовые случаи для процесса выбора подключаемого модуля для управления исходным кодом решения.

## <a name="command-menu-access"></a>Доступ к меню команд
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]В тестовых случаях используются следующие пути к меню интегрированной среды разработки.

- Текущий подключаемый модуль системы управления версиями: **Сервис**  ->  **Параметры**  ->  **Source Control**  ->  **Выбор подключаемого модуля**системы управления версиями.

- Изменить привязку системы управления версиями: управление исходным **файлом**в системе управления версиями  ->  **Source Control**  ->  **Change Source Control**...

## <a name="common-expected-behavior"></a>Типичное ожидаемое поведение
 Изменение подключаемого модуля системы управления версиями для решения возможно без выхода из Visual Studio или повторной загрузки решения. Кроме того, текущий подключаемый модуль системы управления версиями автоматически изменяется на тот, который используется решением при загрузке решения.

## <a name="test-cases"></a>Тестовые случаи
 Ниже приведены конкретные тестовые случаи для тестовой области переключения подключаемых модулей.

### <a name="case-8a-automatic-change"></a>Case 8a: автоматическое изменение

#### <a name="expected-behavior"></a>Ожидаемое поведение
 Когда пользователь загружает решение, находящееся в системе управления версиями, решение автоматически загружается, а соответствующий подключаемый модуль системы управления версиями выбирается как текущий.

| Действие | Шаги теста | Ожидаемые результаты для проверки |
| - | - | - |
| Автоматическое изменение подключаемого модуля системы управления версиями | 1. Выберите подключаемый модуль в разделе тестирование как текущий (**Сервис**  ->  **Параметры**  ->  **Source Control**  ->  **Выбор подключаемого модуля**системы управления версиями).<br />2. Создайте новый проект.<br />3. Добавьте решение в систему управления версиями.<br />4. Выберите другой подключаемый модуль (например, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />5. принять запрос на выгрузку решения.<br />6. повторно откройте решение с диска. | Решение открыто.<br /><br /> Подключаемый модуль в тесте является текущим подключаемым модулем системы управления версиями. |

### <a name="case-8b-solution-based-change"></a>8B регистра: изменение на основе решения

#### <a name="expected-behavior"></a>Ожидаемое поведение
 Решение может быть изменено соответствующим подключаемым модулем системы управления версиями.

| Действие | Шаги теста | Ожидаемые результаты для проверки |
|----------------------------------| - | - |
| Изменение подключаемого модуля для решения | 1. Выберите подключаемый модуль в разделе тестирование как текущий (**Сервис**  ->  **Параметры**  ->  **Source Control**  ->  **Выбор подключаемого модуля**системы управления версиями).<br />2. Создайте новый проект и решение.<br />3. Добавьте решение в систему управления версиями.<br />4. отменить привязку решения к системе управления версиями (с помощью диалогового окна « **изменение системы управления версиями** »).<br />5. Выберите другой подключаемый модуль (например, [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] ).<br />6. Перезагрузите решение с диска, если оно выгружено.<br />7. Добавьте решение в систему управления версиями.<br />8. Отмена привязки решения из системы управления версиями (с помощью диалогового окна **Смена системы управления версиями** ).<br />9. Выберите подключаемый модуль в разделе тест еще раз.<br />10. Перезагрузите решение с диска, если оно выгружено.<br />11. Привязка решения к исходному расположению (с помощью диалогового окна « **изменение системы управления версиями** »). | Решение добавляется в систему управления версиями с помощью выбранного подключаемого модуля. |

## <a name="see-also"></a>См. также раздел
- [Руководство по тестированию подключаемых модулей системы управления версиями](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
