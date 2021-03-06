---
title: Как установить подключаемый модуль системы управления версиями | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], source control plug-ins
- source control plug-ins, installing
ms.assetid: 9e2e01d9-7beb-42b2-99b2-86995578afda
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 997e734f6d2ab6bcf70e3a4843ac66564683c79b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843268"
---
# <a name="how-to-install-a-source-control-plug-in"></a>Практическое руководство. Установка подключаемого модуля системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Создание подключаемого модуля системы управления версиями состоит из трех этапов:  
  
1. Создайте библиотеку DLL с функциями, определенными в разделе Справочник по API подключаемого модуля системы управления версиями этой документации.  
  
2. Реализуйте определяемые API-функции подключаемого модуля системы управления версиями. При [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] вызове для него интерфейсы и диалоговые окна можно сделать доступными из подключаемого модуля.  
  
3. Зарегистрируйте библиотеку DLL, сделав соответствующие записи в реестре.  
  
## <a name="integration-with-visual-studio"></a>Интеграция с Visual Studio  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] поддерживает подключаемые модули системы управления версиями, которые соответствуют интерфейсу API подключаемого модуля системы управления версиями.  
  
### <a name="registering-the-source-control-plug-in"></a>Регистрация подключаемого модуля системы управления версиями  
 Прежде чем запустить интегрированную среду разработки (IDE) в системе управления версиями, сначала необходимо найти библиотеку DLL подключаемого модуля системы управления версиями, которая экспортирует API.  
  
##### <a name="to-register-the-source-control-plug-in-dll"></a>Регистрация библиотеки DLL подключаемого модуля системы управления версиями  
  
1. Добавьте две записи в раздел HKEY_LOCAL_MACHINE в подразделе программного обеспечения, в котором указан подраздел названия организации, а затем — подраздел Product Name. Шаблон — HKEY_LOCAL_MACHINE \софтваре \\ *[название компании]* \\ *[название продукта]* \\ *[запись]* = значение. Две записи всегда называются Скксервернаме и Скксерверпас. Каждый является обычной строкой.  
  
     Например, если название компании — Microsoft, а продукт системы управления версиями имеет имя SourceSafe, то этот путь реестра будет HKEY_LOCAL_MACHINE \Софтваре\микрософт\саурцесафе. В этом подразделе первая запись, Скксервернаме, является понятным для пользователя строковым именем вашего продукта. Вторая запись, Скксерверпас, представляет собой полный путь к библиотеке DLL подключаемого модуля системы управления версиями, к которой должна подключаться интегрированная среда разработки. Ниже приведены примеры записей реестра.  
  
    |Пример записи реестра|Образец значения|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE \Софтваре\микрософт\саурцесафе\скксервернаме|Microsoft Visual SourceSafe|  
    |HKEY_LOCAL_MACHINE \Софтваре\микрософт\саурцесафе\скксерверпас|c:\vss\win32\ssscc.dll|  
  
    > [!NOTE]
    > Скксерверпас — это полный путь к подключаемому модулю SourceSafe. Подключаемый модуль системы управления версиями будет использовать разные названия компаний и продуктов, но те же пути к записям реестра.  
  
2. Для изменения поведения подключаемого модуля системы управления версиями можно использовать следующие необязательные записи реестра. Эти записи попадают в тот же подраздел, что и Скксервернаме и Скксерверпас.  
  
    - Запись Хидеинвисуалстудиорегистри можно использовать, если не требуется, чтобы подключаемый модуль системы управления версиями отображался в списке выбора подключаемых модулей [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Эта запись также влияет на автоматическое переключение на подключаемый модуль системы управления версиями. Один из возможных вариантов использования этой записи заключается в том, что вы предоставляете пакет управления версиями, который заменяет подключаемый модуль системы управления версиями, но вы хотите упростить миграцию пользователя из использования подключаемого модуля системы управления версиями в пакет управления версиями. После установки пакета системы управления версиями он задает эту запись реестра, которая скрывает подключаемый модуль.  
  
         Хидеинвисуалстудио является значением типа DWORD и имеет значение 1, чтобы скрыть подключаемый модуль или 0 для отображения подключаемого модуля. Если запись реестра не отображается, по умолчанию используется режим отображения подключаемого модуля.  
  
    - Запись реестра дисаблесккманажер может использоваться для отключения или скрытия пункта меню **запуска \<Source Control Server> ** , который обычно отображается в **File**  ->  подменю**системы управления версиями** файлов. При выборе этого пункта меню вызывается функция [сккрунскк](../../extensibility/sccrunscc-function.md) . Подключаемый модуль системы управления версиями может не поддерживать внешнюю программу, поэтому может потребоваться отключить или даже скрыть пункт меню " **Пуск** ".  
  
         Дисаблесккманажер — это значение типа DWORD, равное 0, чтобы включить команду меню " **Пуск \<Source Control Server> ** ", значение "1", чтобы отключить пункт меню, и значение "2", чтобы скрыть пункт меню. Если эта запись реестра не отображается, в качестве поведения по умолчанию отображается пункт меню.  
  
    |Пример записи реестра|Образец значения|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE \Софтваре\микрософт\саурцесафе\хидеинвисуалстудио|1|  
    |HKEY_LOCAL_MACHINE \Софтваре\микрософт\саурцесафе\дисаблесккманажер|1|  
  
3. Добавьте подраздел Саурцекодеконтролпровидер в раздел HKEY_LOCAL_MACHINE в подразделе программное обеспечение.  
  
     В этом подразделе для записи реестра Провидеррегкэй задана строка, представляющая подраздел, который вы поместили в реестре на шаге 1. Шаблон — HKEY_LOCAL_MACHINE \софтваре\саурцекодеконтролпровидер\провидеррегкэй = Software \\ *[название компании]* \\ *[название продукта]*.  
  
     Ниже приведен пример содержимого для этого подраздела.  
  
    |Параметр реестра|Образец значения|  
    |--------------------|------------------|  
    |HKEY_LOCAL_MACHINE \Софтваре\саурцекодеконтролпровидер\провидеррегкэй|софтваре\микрософт\саурцесафе|  
  
    > [!NOTE]
    > Подключаемый модуль системы управления версиями будет использовать те же имена подраздела и записи, но значение будет другим.  
  
4. Создайте подраздел с именем Инсталледсккпровидерс в подразделе Саурцекодеконтролпровидер, а затем поместите одну запись в этот подраздел.  
  
     Имя этой записи — понятное пользователю имя поставщика (то же, что и значение, указанное для записи Скксервернаме), а значение — еще раз — подраздел, созданный на шаге 1. Шаблон — HKEY_LOCAL_MACHINE \софтваре\саурцекодеконтролпровидер\инсталледсккпровидерс \\ *[отображаемое имя]* = Software \\ *[название компании]* \\ *[название продукта]*.  
  
     Пример:  
  
    |Пример записи реестра|Образец значения|  
    |---------------------------|------------------|  
    |HKEY_LOCAL_MACHINE \Софтваре\саурцекодеконтролпровидер\инсталледсккпровидерс\микрософт Visual SourceSafe|софтваре\микрософт\саурцесафе|  
  
    > [!NOTE]
    > Таким способом может быть зарегистрировано несколько подключаемых модулей системы управления версиями. Таким способом выполняется [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Поиск всех установленных подключаемых модулей на основе API управления версиями.  
  
## <a name="how-an-ide-locates-the-dll"></a>Обнаружение библиотеки DLL в интегрированной среде разработки  
 В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среде разработки есть два способа поиска библиотеки DLL подключаемого модуля системы управления версиями:  
  
- Найдите подключаемый модуль системы управления версиями по умолчанию и подключитесь к нему автоматически.  
  
- Найти все зарегистрированные подключаемые модули системы управления версиями, из которых пользователь выбирает одну из них.  
  
  Чтобы найти библиотеку DLL в первую очередь, интегрированная среда разработки выполняет поиск в подразделе HKEY_LOCAL_MACHINE \Софтваре\саурцекодеконтролпровидер для записи Провидеррегкэй. Значение этой записи указывает на другой подраздел. Затем интегрированная среда разработки ищет запись с именем Скксерверпас во втором подразделе в разделе HKEY_LOCAL_MACHINE. Значение этой записи указывает среде IDE на библиотеку DLL.  
  
> [!NOTE]
> Интегрированная среда разработки не загружает библиотеки DLL из относительных путей (например, .\NewProvider.DLL). Необходимо указать полный путь к библиотеке DLL (например, c:\Providers\NewProvider.DLL). Это позволяет усилить безопасность интегрированной среды разработки, предотвращая несанкционированные или олицетворенные подключаемые модули DLL.  
  
 Чтобы найти библиотеку DLL вторым образом, интегрированная среда разработки ищет в подразделе HKEY_LOCAL_MACHINE \Софтваре\саурцекодеконтролпровидер\инсталледсккпровидерс все записи<em>.</em> У каждой записи есть имя и значение. Интегрированная среда разработки отображает список этих имен для пользователя<em>.</em> Когда пользователь выбирает имя, интегрированная среда разработки находит значение для выбранного имени, которое указывает на подраздел. Интегрированная среда разработки ищет запись с именем Скксерверпас в этом подразделе в разделе HKEY_LOCAL_MACHINE. Значение этой записи указывает среде IDE на правильную библиотеку DLL.  
  
 Подключаемый модуль системы управления версиями должен поддерживать оба способа поиска библиотеки DLL и, следовательно, устанавливать Провидеррегкэй, перезаписывая все предыдущие настройки. Что более важно, он должен добавить себя в список Инсталледсккпровидерс, чтобы пользователь мог выбрать используемый подключаемый модуль системы управления версиями.  
  
> [!NOTE]
> Поскольку используется ключ HKEY_LOCAL_MACHINE, в качестве подключаемого модуля системы управления версиями по умолчанию на данном компьютере можно зарегистрировать только один подключаемый модуль системы управления версиями (тем не менее, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пользователи могут определить, какой подключаемый модуль системы управления версиями будет использоваться для конкретного решения). В процессе установки проверьте, установлен ли уже подключаемый модуль системы управления версиями. Если да, попросите пользователя указать, следует ли устанавливать новый подключаемый модуль системы управления версиями по умолчанию. Во время отмены установки не удаляйте другие подразделы реестра, общие для всех подключаемых модулей системы управления версиями в HKEY_LOCAL_MACHINE \Софтваре\саурцекодеконтролпровидер. Удалите только определенный подраздел SCC.  
  
## <a name="how-the-ide-detects-version-1213-support"></a>Как интегрированная среда разработки обнаруживает поддержку версии 1.2/1.3  
 Как [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] обнаруживает, поддерживает ли подключаемый модуль интерфейс API подключаемого модуля системы управления версиями 1,2 и 1,3? Чтобы объявить дополнительные возможности, подключаемый модуль системы управления версиями должен реализовать соответствующую функцию.  
  
 Сначала [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] проверяет значение, возвращаемое вызовом [сккжетверсион](../../extensibility/sccgetversion-function.md). Оно должно быть больше или равно 1,2.  
  
 Затем [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] определяет, поддерживается ли конкретная новая возможность, путем проверки `lpSccCaps` аргумента в [скЦинитиализе](../../extensibility/sccinitialize-function.md).  
  
 Если выполняются оба этих условия, можно вызывать новые функции, поддерживаемые в версиях 1,2 и 1,3.  
  
## <a name="see-also"></a>См. также:  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
