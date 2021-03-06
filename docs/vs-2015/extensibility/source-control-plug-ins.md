---
title: Подключаемые модули системы управления версиями | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5a99ebdf2366ce6a60a6a724afc7d742db7150f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705793"
---
# <a name="source-control-plug-ins"></a>Подключаемые модули системы управления версиями
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В разделе Справочник по подключаемому модулю SDK для системы управления версиями содержится полная спецификация интерфейса, позволяющая интегрировать системы управления версиями с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Он задает синтаксис и семантику различных функций и типов данных, которые должен реализовать подключаемый модуль системы управления версиями, для взаимодействия с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интегрированной средой разработки (IDE).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)  
 Содержит список функций, которые должны быть реализованы с помощью подключаемого модуля системы управления версиями, чтобы обеспечить соответствие интерфейсу API подключаемого модуля системы управления версиями.  
  
 [Функции обратного вызова, реализуемые интегрированной средой разработки](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Описывает функции, которые подключаемый модуль системы управления версиями использует для передачи информации обратно в интегрированную среду разработки во время выполнения определенных команд.  
  
 [Enumerators](../extensibility/enumerators.md)  
 Перечисляет типы данных перечислителя в интерфейсе API подключаемого модуля системы управления версиями, о которых должен быть знаком подключаемый модуль системы управления версиями.  
  
 [Флаги возможностей](../extensibility/capability-flags.md)  
 Описывает `SCC_CAP_xxx` Флаги, которые указывают возможности поставщика.  
  
 [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)  
 Перечисляет флаги, которые полезны в контексте определенных команд.  
  
 [Код ошибки](../extensibility/error-codes.md)  
 Список стандартных значений ошибок, возвращаемых функциями в качестве `SCCTRN` .  
  
 [Строки, используемые в качестве ключей поиска подключаемого модуля системы управления версиями](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Описание ключей для доступа к реестру для поиска подключаемого модуля системы управления версиями.  
  
 [Файл MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Описывает файл на стороне клиента, который содержит сведения, непрозрачные для интегрированной среды разработки, но используется подключаемым модулем системы управления версиями для нахождение решения или проекта в системе управления версиями.  
  
 [Рекомендации по реализации подключаемого модуля системы управления версиями](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Предоставляет набор важных технических напоминаний, которые следует помнить при реализации API подключаемого модуля системы управления версиями.  
  
 [Ограничения длины строки](../extensibility/restrictions-on-string-lengths.md)  
 Описывает ограничения в интерфейсе API подключаемого модуля системы управления версиями на основе длины строк, используемых в различных функциях.  
  
 [Словарь терминов](../extensibility/source-control-plug-in-glossary.md)  
 Содержит полезные термины и их определения для чтения документации по пакету SDK для подключаемого модуля системы управления версиями.  
  
 [Практическое руководство. Отключение предупреждений о совместимости для подключаемых модулей системы управления версиями](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Описание отключения предупреждений.  
  
## <a name="related-sections"></a>См. также  
 [Пример подключаемого модуля системы управления версиями](https://msdn.microsoft.com/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Предоставляет образец функциональных возможностей подключаемого модуля системы управления версиями.  
  
 [Руководство по тестированию подключаемых модулей системы управления версиями](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Описывает процедуры тестирования, связанные с подключаемым модулем системы управления версиями.  
  
 [Создание подключаемого модуля системы управления версиями](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Описывает создание подключаемого модуля системы управления версиями, предоставляющего функции управления версиями при использовании пользовательского [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] интерфейса системы управления версиями.  
  
 [Справочник по пакету SDK для Visual Studio](../extensibility/visual-studio-sdk-reference.md)  
 Содержит список справочных разделов.
