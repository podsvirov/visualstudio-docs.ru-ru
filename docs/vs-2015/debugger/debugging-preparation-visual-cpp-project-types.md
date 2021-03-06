---
title: 'Подготовка к отладке: типы проектов Visual C++ | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- project templates, debugging
- Visual C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f92b96d99889c88236df34b3f60c7fd71d5032d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691346"
---
# <a name="debugging-preparation-visual-c-project-types"></a>Подготовка к отладке: типы проектов Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В этом разделе описана отладка основных типов проектов, созданных с использованием шаблонов проектов [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].  
  
 Обратите внимание, что типы проектов, которые в результате создают DLL, были сгруппированы в разделе [Отладка проектов DLL](../debugger/debugging-dll-projects.md) из-за их общих особенностей.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Содержание раздела  
 [Рекомендуемые значения свойств](#BKMK_Recommended_Property_Settings)  
  
 [Проекты Win32](#BKMK_Win32_Projects)  
  
- [Отладка приложения Win32 на C или C++](#BKMK_To_debug_a_C_or_C___Win32_application)  
  
- [Ручная установка конфигурации отладки](#BKMK_To_manually_set_a_Debug_configuration)  
  
  [Приложения Windows Forms (.NET)](#BKMK_Windows_Forms_Applications___NET_)  
  
## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Рекомендуемые значения свойств  
 Некоторые свойства должны быть установлены одинаково для всех скриптов неуправляемой отладки. В следующих таблицах приводятся рекомендованные параметры свойств. Параметры, здесь не перечисленные, могут иметь различные значения для различных типов неуправляемых проектов. Дополнительные сведения см. в разделе [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md) .  
  
### <a name="configuration-properties-124-cc-124-optimization-node"></a>Свойства конфигурации | С/С++ | Узел оптимизации  
  
|Имя свойства|Параметр|  
|-------------------|-------------|  
|**Optimization**|Установите значение **Отключено (/0d)** . Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, этот параметр можно разрешить, но следует помнить, что код, показываемый в окне **Дизассемблированный код**, формируется из оптимизированного источника и может не совпадать с тем, что наблюдается в исходных окнах. Другие возможности, такие как пошаговое выполнение, могут действовать не так, как ожидалось.|  
  
### <a name="configuration-properties-124-linker-124-debugging-node"></a>Свойства конфигурации | Компоновщик | Узел отладки  
  
|Имя свойства|Параметр|  
|-------------------|-------------|  
|**Создать отладочную информацию**|Следует всегда устанавливать этот параметр в **Да (/DEBUG)** для создания символов отладки и необходимых для нее файлов. Когда приложение выходит в производство, этот параметр можно отключить.|  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Проекты Win32  
 Win32-приложения — это традиционные программы для Windows, написанные на C или C++. Отладка приложений такого типа в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] не вызывает никаких затруднений.  
  
 Win32-приложения включают приложения MFC и ATL-проекты. В них используются Windows API и могут использоваться MFC или ATL, но они не используют среду CLR. Они могут, однако, вызывать управляемый код, использующий среду CLR.  
  
 В следующей процедуре описывается отладка проекта Win32 в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Еще одним способом отладки приложений Win32 является запуск приложения вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и подключение к этому приложению. Дополнительные сведения см. в статье [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> Отладка приложения Win32 на C или C++  
  
1. Откройте проект в Visual Studio.  
  
2. В меню **Отладка** выберите команду **Пуск**.  
  
3. Отладка с использованием методик, описанных в разделе [основы отладчика](../debugger/debugger-basics.md).  
  
### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Ручная установка конфигурации отладки  
  
1. В меню **Вид** выберите команду **Страницы свойств**.  
  
2. Щелкните узел **Свойства конфигурации**, чтобы раскрыть его, если он еще не раскрыт.  
  
3. Выберите **Общие** и установите для строки **Вывод** значение **Отладка**.  
  
4. Откройте узел **С/С++** и выберите пункт **Общие**.  
  
    В строке **Отладка** можно указать тип отладочной информации, которая будет создана компилятором. Можно выбрать **База данных программы (/Zi)** или **База данных программы для операции "Изменить и продолжить" (/ZI)** .  
  
5. Выберите **Оптимизация** и в строке **Оптимизация** выберите пункт **Отключена (/0D)** в раскрывающемся списке.  
  
    Оптимизированный код отлаживать труднее, так как созданные команды не полностью соответствуют исходному коду. Если в программе обнаруживается ошибка, проявляющаяся только в оптимизированном коде, этот параметр можно разрешить, но следует помнить, что код, показываемый в окне Дизассемблированный код, формируется из оптимизированного источника и может не совпадать с тем, что наблюдается в исходных окнах. Такие возможности, как пошаговое выполнение, скорее всего будут неправильно показывать точки останова и точки выполнения.  
  
6. Откройте узел **Компоновщик** и выберите **Отладка**. В первой строке **Создать** выберите параметр **Да (/DEBUG)** из раскрывающегося списка. Всегда делайте так при отладке.  
  
   Дополнительные сведения см. в статье [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
   [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="windows-forms-applications-net"></a><a name="BKMK_Windows_Forms_Applications___NET_"></a> Приложения Windows Forms (.NET)  
 Шаблон **Приложение Windows Forms (.NET)** создает приложение Windows Forms [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]. Дополнительные сведения см. в разделе [Практическое руководство. создать проект приложения Windows](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Отладка приложений такого типа в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] аналогична отладке управляемых приложений Windows Forms.  
  
 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] автоматически создает требуемые параметры для отладки и выпуска. При необходимости эти параметры можно изменить в диалоговом окне ** \<project name> страницы свойств** . Дополнительные сведения см. в разделе [Конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  
  
 Дополнительные сведения см. в статье [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
 Еще одним способом отладки приложений Windows Forms является запуск приложения вне [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] и подключение к этому приложению. Дополнительные сведения см. в разделе [Подключение к выполняющейся программе или к нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 [Содержание раздела](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)  
  
## <a name="see-also"></a>См. также:  
 [Основы отладчика](../debugger/debugger-basics.md)   
 [Параметры проекта для конфигурации отладки C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Подключение к запущенной программе или нескольким программам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Конфигурации отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Практическое руководство. Создание проекта приложения Windows](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa)
