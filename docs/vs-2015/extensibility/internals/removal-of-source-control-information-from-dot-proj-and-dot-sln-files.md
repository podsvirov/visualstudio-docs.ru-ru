---
title: Удаление данных системы управления версиями из. Proj и. Файлы SLN | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7cdaeb02f77d3775096f840a513f68e531b1299
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199375"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Удаление сведений системы управления версиями из файлов PROJ и SLN
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В версии 1,2 интерфейса API подключаемого модуля системы управления версиями данные SCC хранятся в МССККПРЖ. Файл SCC. Преимущество МССККПРЖ. Файл SCC — это то, что данные SCC не управляются исходным кодом, как и в proj-и. sln файлах.  
  
## <a name="version-12-changes"></a>Изменения версии 1,2  
 В подключаемых модулях системы управления версиями, основанных на API подключаемого модуля системы управления версиями 1,1, сведения о системе управления версиями хранятся в файлах проекта (proj) и решения (SLN). Расположение базы данных для сведений системы управления версиями задается параметром Аукспас, а конкретное расположение в базе данных указывается с помощью параметра ProjName. Такое поведение может вызвать проблемы после ветвления, ветвления или копирования, поскольку после выполнения любой из этих операций ProjName обычно будет недействительным.  
  
 В интерфейсе API подключаемого модуля системы управления версиями 1,1 среда IDE использовала файлы ~ SAK, чтобы определить, поддерживает ли подключаемый модуль МССККПРЖ. Метод SCC для хранения данных системы управления версиями. Интерфейс API подключаемого модуля системы управления версиями 1,2 предоставляет новую возможность для обнаружения поддержки МССККПРЖ. Файл SCC без использования файла ~ SAK. Дополнительные сведения см. в разделе [исключение файлов ~ SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>См. также:  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
