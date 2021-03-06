---
title: Использование флажков C++ Core Guidelines | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: fffa4cec6a2bd7a340b90776ac20dc486f28045b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173577"
---
# <a name="using-the-c-core-guidelines-checkers"></a>Использование средств проверки на соответствие C++ Core Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Core Guidelines являются переносимым набором руководств, правил и рекомендаций по написанию кода на C++, созданного экспертами и дизайнерами C++.  Visual Studio теперь поддерживает пакеты надстроек, которые создают дополнительные правила для средств анализа кода, чтобы проверить код на соответствие C++ Core Guidelines и предложить улучшения.  
  
## <a name="the-c-core-guidelines-project"></a>Проект C++ Core Guidelines  
 C++ Core Guidelines, созданные с помощью Бьерном Страуструп и других, являются руководством по безопасному и эффективному использованию современных C++. В рекомендациях особое внимание уделяется безопасности статического типа и безопасности ресурсов. Они позволяют устранить или свести к минимальному числу наиболее подверженные ошибкам части языка и предложить, как сделать код более простым и надежным способом. Эти рекомендации поддерживаются стандартом C++ Foundation. Дополнительные сведения см. в документации, [C++ Core Guidelines](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)и доступ к файлам проекта документации по C++ Core Guidelines в [GitHub](https://github.com/isocpp/CppCoreGuidelines).  
  
 Корпорация Майкрософт поддерживает C++ Core Guidelines усилия, представляя C++ Core Check наборы правил анализа кода, которые можно добавить в проекты с помощью пакета NuGet. Пакет называется Microsoft. CppCoreCheck и доступен по адресу [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Для этого пакета требуется по крайней мере Visual Studio 2015 с обновлением 1.  
  
 Пакет также устанавливает другой пакет как зависимость — библиотеку поддержки рекомендаций только для заголовков (GSL). GSL также доступен на сайте GitHub по адресу [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Включение рекомендаций по C++ Core Check в анализе кода  
 Чтобы включить средства анализа кода C++ Core Check, установите пакет NuGet Microsoft. CppCoreCheck в каждый проект C++, который требуется проверить в Visual Studio.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Добавление пакета Microsoft. CppCoreCheck в проект  
  
1. В **Обозреватель решений**щелкните правой кнопкой мыши, чтобы открыть контекстное меню проекта в решении, в которое требуется добавить пакет. Выберите **Управление пакетами NuGet** , чтобы открыть **Диспетчер пакетов NuGet**.  
  
2. В окне **Диспетчер пакетов NuGet** найдите Microsoft. CppCoreCheck.  
  
    ![В окне диспетчера пакетов NuGet отображается пакет CppCoreCheck](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Выберите пакет Microsoft. CppCoreCheck, а затем нажмите кнопку " **установить** ", чтобы добавить правила в проект.  
  
   Пакет NuGet добавляет дополнительный файл MSBuild. targets в проект, который вызывается при включении анализа кода для проекта. Этот файл targets добавляет правила C++ Core Check в качестве дополнительного расширения для средства анализа кода Visual Studio.  
  
   Вы можете включить анализ кода для проекта, установив флажок **Включить анализ кода при сборке** в разделе **анализ кода** диалогового окна **страницы свойств** проекта.  
  
   ![Страница свойств для общих параметров анализа кода](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   Правила C++ Core Check становятся частью наборов правил по умолчанию, которые выполняются при включении анализа кода. Поскольку правила C++ Core Check находятся под разработкой, некоторые правила могут быть не готовы к использованию во всем коде, но могут быть полезны во время разработки. Эти правила выпускаются в экспериментальном режиме. Вы можете выбрать, следует ли выполнять выпущенные или экспериментальные правила в свойствах проекта.  
  
   ![Страница свойств для параметров расширений анализа кода](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   Чтобы включить или отключить наборы правил C++ Core Check, откройте диалоговое окно **страницы свойств** для проекта. В разделе **Свойства конфигурации**разверните узел  **анализ кода**, **расширения**. В элементе управления "раскрывающийся список" рядом с **параметром включить C++ Core Check (выпущен)** или **включить C++ Core Check (экспериментальное)** выберите **Да** или **нет**. Нажмите кнопку **ОК** или **Применить** , чтобы сохранить изменения.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Проверка типов, границ и времени жизни  
 В настоящее время пакет C++ Core Check содержит средства проверки [безопасности типа](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), обеспечения [безопасности, привязки](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)и профилей [безопасности времени существования](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) .  
  
 Ниже приведен пример типов проблем, которые могут найти C++ Core Check правила.  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 В этом примере показано несколько предупреждений, которые могут найти C++ Core Check правила.  
  
- C26494 — тип правила. 5: всегда инициализировать объект.  
  
- C26485 является границей правила. 3: отсутствует Decay массива в указатель.  
  
- C26481 является границей правила. 1: не используйте арифметические действия с указателями. Взамен рекомендуется использовать `span`.  
  
  Если C++ Core Check наборы правил анализа кода установлены и включены при компиляции этого кода, первые два предупреждения выводятся, но третья подавляется. Вот выходные данные сборки из примера кода:  
  
**1> сборка------запущена: проект: Коречеккексампле, конфигурация: Отладка Win32--**  
**----**  
**1> Коречеккексампле. cpp**  
**1> Коречеккексампле. vcxproj-> К:\усерс\усернаме\документс\висуал Studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1> Коречеккексампле. vcxproj-> К:\усерс\усернаме\документс\висуал Studio 2015 \ P**  
**Рожектс\коречеккексампле\дебуг\коречеккексампле.ПДБ (полный PDB)**  
**к:\усерс\усернаме\документс\висуал Studio 2015 \ прожектс\коречеккексампле\корече**  
**ккексампле\коречеккексампле.КПП (6): Warning C26494: переменная "arr" является унинитиализ**  
**ED. Всегда инициализируйте объект. (Type. 5: https: \/ /go.Microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**к:\усерс\усернаме\документс\висуал Studio 2015 \ прожектс\коречеккексампле\корече**  
**ккексампле\коречеккексампле.КПП (7): предупреждение C26485: выражение "arr": нет массива для**  
**Decay указателя. (Bounds. 3: https: \/ /go.Microsoft.com/fwlink/p/?LinkID=620415)**  
**========== Сборка: успешно: 1, с ошибками: 0, без изменений: 0, пропущено: 0 ==========** 

C++ Core Guidelines, которые помогут вам в написании лучшего и безопасного кода. Однако если у вас есть экземпляр, в котором не следует применять правило или профиль, легко подавить его непосредственно в коде. Атрибут можно использовать `gsl::suppress` для сохранения C++ Core Check обнаружения и сообщения о нарушении правила в следующем блоке кода. Можно пометить отдельные инструкции для подавления определенных правил. Можно даже отключать весь профиль границ путем записи `[[gsl::suppress(bounds)]]` без включения определенного номера правила.  
  
## <a name="use-the-guideline-support-library"></a>Использование библиотеки поддержки рекомендаций  
 Пакет NuGet Microsoft. CppCoreCheck также устанавливает пакет, содержащий реализацию службы поддержки рекомендаций (GSL) корпорацией Майкрософт. GSL также доступен в автономной форме в [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . Эта библиотека полезна, если вы хотите следовать основным рекомендациям. GSL включает определения, позволяющие заменять подверженные ошибкам конструкции более безопасными альтернативами. Например, можно заменить `T*, length` пару параметров на `span<T>` тип. GSL является открытым кодом, поэтому, если вы хотите взглянуть на источники библиотеки, комментарий или участие в программе, проект можно найти по адресу [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .
