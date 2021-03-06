---
title: Новые возможности MSBuild 16.0 | Документация Майкрософт
ms.date: 03/11/2019
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 48fc1a02ad34a3d5229ead0da79c0f6fa781670e
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/21/2020
ms.locfileid: "88711655"
---
# <a name="whats-new-in-msbuild-160"></a>Новые возможности в MSBuild 16.0

В этой статье описываются обновленные возможности и свойства MSBuild 16.0. Подробные заметки о выпуске см. в статье [MSBuild 16.0](https://github.com/microsoft/msbuild/releases/tag/v16.0.461.62831).

## <a name="changed-path"></a>Измененный путь

 MSBuild устанавливается в папку *\Current* каждой версии Visual Studio, а исполняемые файлы находятся в подпапке *\Bin*. Например, путь к *MSBuild.exe* установленному с помощью сообщества Visual Studio 2019 — *C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Current\Bin\MSBuild.exe*. Для поиска MSBuild можно также использовать модуль PowerShell: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

## <a name="changed-properties"></a>Измененные свойства

 В связи с выходом нового номера версии изменены следующие свойства MSBuild.

- `MSBuildToolsVersion` для этой версии средств считается текущей. Версия сборки имеет такой же номер, как и Visual Studio 2017, т. е. 15.1.0.0.

- `VisualStudioVersion` для этой версии средств имеет значение 16.0.

## <a name="updates"></a>Обновления

MSBuild и Visual Studio теперь по умолчанию создают код для .NET Framework 4.7.2. Если вы хотите использовать новые функции API MSBuild, необходимо также обновить сборку, но существующий код будет продолжать работать.

## <a name="see-also"></a>См. также

- [MSBuild](../msbuild/msbuild.md)
