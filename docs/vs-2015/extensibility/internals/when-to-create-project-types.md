---
title: Когда следует создавать типы проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b5bc2bacb53973bd552b983b742e4f9e68fe31b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687699"
---
# <a name="when-to-create-project-types"></a>Когда следует создавать типы проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Создание нового типа проекта предоставляет базу для настройки [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для пользователей. Однако создание нового типа проекта не является обязательным для всех [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] настроек. Следующие рекомендации помогут определить, требуется ли для вашего сценария новый тип проекта.  
  
## <a name="create-a-new-project-type"></a>Создание нового типа проекта  
 Если необходимо настроить [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] для работы один или несколько из следующих способов, необходимо создать тип проекта.  
  
- Участвуйте в сборке, развертывании, конфигурациях и системе управления версиями.  
  
- Поддержка отладки предложений.  
  
- Отображение элементов проекта в **Обозреватель решений**.  
  
- Используйте диалоговое окно **Открытие проекта** или **Создание проекта** .  
  
- Поддержка вложений проектов.  
  
## <a name="extend-an-existing-project-type"></a>Расширение существующего типа проекта  
 Может потребоваться создать новый тип проекта, который может использовать [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] следующие способы изменения или расширения поведения существующего типа проекта, например изменение процесса сборки для [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] проектов:  
  
- Работать с несколькими файлами как единым целым.  
  
- Отображение одного файла в виде иерархии дочерних элементов.  
  
- Отображать контекст команды вокруг редакторов.  
  
- Отображение контекста службы для редакторов.  
  
## <a name="use-an-existing-project-type"></a>Использовать существующий тип проекта  
 Иногда создание нового проекта не является обязательным. В следующей таблице приведены задачи, для которых не нужно создавать тип проекта.  
  
|Задача|Описание|  
|----------|-----------------|  
|Обработка команд|Любой пакет VSPackage может выполнять команды.|  
|Создание редактора|Пользовательские редакторы могут быть зарегистрированы. Дополнительные сведения см. в разделе [окна документов и редакторы](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc).|  
|Владелец Windows|Вы можете создавать окна инструментов и документов, не добавляя новый тип проекта.|  
|Предоставление свойств в окно свойств|Все объекты могут предоставлять свойства.|  
  
## <a name="create-a-project-subtype"></a>Создание подтипа проекта  
 Подтипы проекта можно использовать для расширения типа управляемого проекта без создания нового типа проекта. Подтипы проектов используют агрегирование COM для расширения управляемых проектов, написанных на Microsoft [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] или [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . С помощью агрегирования COM можно повторно использовать большую часть реализации управляемой системы проектов и по-прежнему настраивать для конкретного сценария посредством агрегирования и использования вспомогательных интерфейсов. Дополнительные сведения о подтипах проектов см. в разделе [Project подтипы](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>См. также:  
 [Окна документов и редакторы](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [Контрольный список: создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
