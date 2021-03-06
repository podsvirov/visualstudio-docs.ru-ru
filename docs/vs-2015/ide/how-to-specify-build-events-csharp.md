---
title: Практическое руководство. Указание событий сборки (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41d3ef0efd4c9eb8eab16bd12cc79f8df1449d65
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670686"
---
# <a name="how-to-specify-build-events-c"></a>Практическое руководство. Назначение событий построения (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Используйте события сборки для указания команд, которые выполняются до начала сборки или после ее завершения. События сборки выполняются, только если сборка успешно достигает этих точек в процессе сборки.

 При сборке проекта события перед сборкой добавляются в файл с именем PreBuildEvent.bat, а события после сборки — в файл с именем PostBuildEvent.bat. Если вы хотите обеспечить проверку ошибок, добавьте собственные команды проверки ошибок в шаги сборки.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="how-to-specify-pre-build-and-post-build-events"></a>Как указать события перед сборкой и после нее

#### <a name="to-specify-a-build-event"></a>Чтобы указать событие сборки

1. В **обозревателе решений** выберите проект, для которого необходимо задать событие сборки.

2. В меню **Проект** выберите **Свойства**.

3. Откройте вкладку **События построения**.

4. В поле **Командная строка события перед сборкой** укажите синтаксис события сборки.

    > [!NOTE]
    > События перед сборкой не выполняются, если проект актуален и сборка не запускается.

5. В поле **Командная строка события после сборки** укажите синтаксис события сборки.

    > [!NOTE]
    > Добавьте оператор `call` перед всеми командами после сборки, запускающими BAT-файлы. Например, `call C:\MyFile.bat` или `call C:\MyFile.bat call C:\MyFile2.bat`.

6. В поле **Выполнить событие после сборки** укажите при каких условиях должно выполняться событие после сборки.

    > [!NOTE]
    > Чтобы добавить длинный синтаксис или выбрать любой из макросов сборки в [диалоговом окне Командная строка события перед сборкой или после сборки](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), нажмите кнопку с многоточием (**...**), чтобы отобразить поле ввода.

     Синтаксис события сборки может включать любую команду, допустимую в командной строке или в BAT-файле. Для имени пакетного файла необходимо указать префикс `call`, чтобы гарантировать выполнение всех последующих команд.

     **Примечание**. Если событие перед сборкой или после сборки завершается ошибкой, можно прервать сборку, задав завершение действия события с кодом, отличным от нуля (0), что означает успешное выполнение действия.

## <a name="example-how-to-change-manifest-information-by-using-a-post-build-event"></a>Пример: изменение данных манифеста с помощью события после сборки
 В следующей процедуре демонстрируется, как задать минимальную версию операционной системы в манифесте приложения с помощью команды EXE, вызываемой из события после сборки (файл exe.manifest в каталоге проекта). Минимальная версия операционной системы — число из четырех частей, например 4.10.0.0. Чтобы это сделать, команда изменит раздел `<dependentOS>` манифеста:

```
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

#### <a name="to-create-an-exe-command-to-change-the-application-manifest"></a>Чтобы создать команду EXE для изменения манифеста приложения

1. Создайте консольное приложение для команды. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

2. В диалоговом окне **Новый проект** разверните узел **Visual C#**, выберите **Windows**, а затем шаблон **Консольное приложение**. Присвойте проекту имя `ChangeOSVersionCS`.

3. В Program.cs добавьте следующую строку для других инструкций `using` в верхней части файла:

   ```
   using System.Xml;
   ```

4. В пространстве имен `ChangeOSVersionCS` замените реализацию класса `Program` следующим кодом:

   ```
   class Program
   {
      /// <summary>
      /// This function will set the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest).
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

    Команда принимает два аргумента: путь к манифесту приложения (то есть папка, в которой в процессе сборки создается манифест, обычно Projectname.publish), и новую версию операционной системы.

5. Выполните построение проекта. В меню **Сборка** выберите **Построить решение**.

6. Скопируйте EXE-файл в каталог, например `C:\TEMP\ChangeOSVersionVB.exe`.

   Затем вызовите эту команду в событии после сборки для изменения манифеста приложения.

#### <a name="to-invoke-a-post-build-event-to-modify-the-application-manifest"></a>Вызов события после сборки для изменения манифеста приложения

1. Создайте приложение Windows для проекта, который должен быть опубликован. В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.

2. В диалоговом окне **Новый проект** разверните узел **Visual C#**, выберите **Windows**, а затем шаблон **Приложение Windows Forms**. Задайте для проекта имя `CSWinApp`.

3. Выберите проект в **обозревателе решений**, а затем в меню **Проект** щелкните пункт **Свойства**.

4. В конструкторе проектов найдите страницу **Публикация** и для параметра **Расположение публикации** задайте значение `C:\TEMP\`.

5. Опубликуйте проект, щелкнув **Опубликовать сейчас**.

     Файл манифеста будет построен и размещен в `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`. Чтобы просмотреть манифест, щелкните правой кнопкой мыши файл и выберите пункт **Открыть с помощью**, затем выберите **Выбрать программу из списка** и щелкните **Блокнот**.

     Найдите в файле элемент `<osVersionInfo>`. Например, версия может быть следующей:

    ```
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
    ```

6. В конструкторе проектов перейдите на вкладку **события сборки** и нажмите кнопку **изменить событие после сборки** .

7. В **командной строке события после сборки** введите следующую команду:

     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

     При сборке проекта выполнение этой команды приведет к изменению минимальной версии операционной системы в манифесте приложения на 5.1.2600.0.

     Так как макрос `$(TargetPath)` выражает полный путь к создаваемому исполняемому файлу, файл `$(TargetPath)`.manifest будет указывать манифест приложения, созданный в каталог bin. При публикации этот манифест будет скопирован в расположение публикаций, которое было задано ранее.

8. Опубликуйте проект еще раз. Откройте страницу **Публикация** и нажмите кнопку **Опубликовать сейчас**.

     Еще раз просмотрите манифест. Чтобы просмотреть манифест, откройте каталог публикации, щелкните файл правой кнопкой мыши и выберите пункт **Открыть с помощью**, затем выберите **Выбрать программу из списка** и щелкните **Блокнот**.

     Версия должна иметь следующий вид:

    ```
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
    ```

## <a name="see-also"></a>См. также:
 [Страница "события сборки" в конструкторе проектов (C#)](../ide/reference/build-events-page-project-designer-csharp.md) [диалоговое окно "Командная строка события перед построением/после сборки"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) [как указать события сборки (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md) [Компиляция и построение](../ide/compiling-and-building-in-visual-studio.md)
