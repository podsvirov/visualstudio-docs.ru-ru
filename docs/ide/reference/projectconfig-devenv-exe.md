---
title: -ProjectConfig (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8bb4b2860d40828a96e25ec6e6c73d947dd60c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567662"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Указывает конфигурацию сборки проекта, применяемую при сборке, очистке, перестроении или развертывании проекта, указанного в аргументе `/Project`.

## <a name="syntax"></a>Синтаксис

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Аргументы

- *SolutionName*

  Обязательный элемент. Полный путь и имя для файла решения.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Обязательный элемент. [Создает](build-devenv-exe.md), [очищает](clean-devenv-exe.md), [развертывает](deploy-devenv-exe.md) или [повторно создает](rebuild-devenv-exe.md) проект.

- *SolnConfigName*

  Необязательный параметр. Имя конфигурации решения (например, `Debug` или `Release`) для применения в решении, указанном в *SolutionName*. Если доступно несколько платформ решений, необходимо также указать платформу (например, `Debug|Win32`). Если этот аргумент не определен или является пустой строкой (`""`), используется действующая конфигурация решения.

- `/Project` *ProjName*

  Необязательный параметр. Путь и имя для файла проекта в решении. Можно ввести отображаемое имя проекта или относительный путь из папки *SolutionName* к файлу проекта. Можно также ввести полный путь и имя файла проекта.

- `/ProjectConfig` *ProjConfigName*

  Необязательный параметр. Имя конфигурации сборки проекта (например, `Debug` или `Release`) для применения к указанному проекту `/Project`. Если доступно несколько платформ решений, необходимо также указать платформу (например, `Debug|Win32`).

- `/Out` *OutputFilename*

  Необязательный параметр. Имя файла, в который вы хотите отправить выходные данные средства. Если файл уже существует, средство добавляет в его конец выходные данные.

## <a name="remarks"></a>Remarks

Параметры `/ProjectConfig` и `/Project` следует использовать вместе в составе команды `/Build`, /`Clean`, `/Deploy` или `/Rebuild`.

Строки с пробелами заключаются в двойные кавычки.

Сводные данные по сборкам, включая ошибки, могут отображаться в окне команд или в любом файле журнала, указанном с помощью параметра `/Out`.

## <a name="example"></a>Пример

Следующая команда выполняет сборку проекта `CSharpWinApp` с использованием конфигурации сборки проекта `Debug` в решении `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>См. также раздел

- [Параметры командной строки для devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
