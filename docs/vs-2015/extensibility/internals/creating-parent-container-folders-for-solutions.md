---
title: Создание папок родительского контейнера для решений | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solutions, creating parent containers
- source control plug-ins, creating parent containers
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b756da118943dd94bfd3bc5220dfc398c60e2a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196926"
---
# <a name="creating-parent-container-folders-for-solutions"></a>Создание папок родительского контейнера для решений
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В интерфейсе API подключаемого модуля системы управления версиями 1,2 пользователь может указать одно назначение корневого каталога для всех веб-проектов в решении. Этот единственный корневой каталог называется Super Unified (SUR).  
  
 В интерфейсе API подключаемого модуля системы управления версиями 1,1, если пользователь добавил многопроектное решение в систему управления версиями, пользователю было предложено указать одно назначение системы управления версиями для каждого веб-проекта.  
  
## <a name="new-capability-flags"></a>Новые флаги возможностей  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## <a name="new-functions"></a>Новые функции  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Интегрированная среда разработки почти всегда создает папку Sur при добавлении решения в систему управления версиями. В частности, это происходит в следующих случаях:  
  
- Проект представляет собой веб-проект файлового ресурса.  
  
- Для проекта и файла решения существуют разные диски.  
  
- Для проекта и файла решения существуют разные общие папки.  
  
- Проекты были добавлены отдельно (в решении, управляемом системой управления версиями).  
  
  В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] предложении рекомендуется, чтобы имя папки Sur совпадало с именем решения без расширения. В следующей таблице приведена сводка по поведению в двух версиях.  
  
|Компонент|API для подключаемого модуля Control для tSource версии 1,1|API подключаемого модуля системы управления версиями, версия 1,2|  
|-------------|----------------------------------------------|---------------------------------------------|  
|Добавить решение в SCC|СкЦинитиализе ()<br /><br /> Сккжетпрожпас ()<br /><br /> Сккжетпрожпас ()<br /><br /> Сккопенпрожект ()|СкЦинитиализе ()<br /><br /> Сккжетпрожпас ()<br /><br /> Скккреатесубпрожект ()<br /><br /> Скккреатесубпрожект ()<br /><br /> Сккопенпрожект ()|  
|Добавление проекта в решение с управлением версиями|Сккжетпрожпас ()<br /><br /> OpenProject ()|Сккжетпарентпрожектпас ()<br /><br /> Сккопенпрожект () **Примечание.**  в Visual Studio предполагается, что решение является прямым дочерним элементом Sur.|  
  
## <a name="examples"></a>Примеры  
 В следующей таблице приведено два примера. В обоих случаях [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пользователю предлагается указать целевое расположение для решения в системе управления версиями до тех пор, пока  *user_choice* не будет указан в качестве назначения. Если указано значение user_choice, то решение и два проекта добавляются без запроса пользователя для целевых объектов системы управления версиями.  
  
|Решение содержит|В расположениях на диске|Структура базы данных по умолчанию|  
|-----------------------|-----------------------|--------------------------------|  
|SLN1. sln<br /><br /> Web1<br /><br /> Web2|C:\Solutions\sln1<br /><br /> C:\Inetpub\wwwroot\Web1<br /><br /> \\\сервер\ввврут $ \web2|$/*user_choice*/SLN1<br /><br /> $/*user_choice*/C/web1<br /><br /> $/*user_choice*/web2|  
|SLN1. sln<br /><br /> Web1<br /><br /> Win1|C:\Solutions\sln1<br /><br /> D:\Inetpub\wwwroot\Web1<br /><br /> C:\solutions\sln1\Win1|$/*user_choice*/SLN1<br /><br /> $/*user_choice*/D/web1<br /><br /> $/*user_choice*/SLN1/win1|  
  
 Папка SUR и вложенные папки создаются независимо от того, была ли операция отменена или завершается ошибкой из-за ошибки. Они не удаляются автоматически в условиях отмены или ошибки.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] по умолчанию используется поведение версии 1,1, если подключаемый модуль системы управления версиями не возвращает и не имеет `SCC_CAP_CREATESUBPROJECT` `SCC_CAP_GETPARENTPROJECT` флагов возможностей. Кроме того, пользователи [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] могут вернуться к поведению версии 1,1, задав для параметра следующий раздел значение DWORD: 00000001:  
  
 [HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\8.0\SourceControl] "Доноткреатесолутионрутфолдеринсаурцеконтрол" = DWORD: 00000001  
  
## <a name="see-also"></a>См. также:  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
