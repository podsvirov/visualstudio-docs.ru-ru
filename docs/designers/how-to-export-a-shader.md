---
title: Практическое руководство. Экспорт шейдера
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 0bd48bf4-9792-4456-a545-e462a2be668d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9495e5aac16821927f5f61005cd16bd20e82687
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768988"
---
# <a name="how-to-export-a-shader"></a>Практическое руководство. Экспорт шейдера

В этом документе показано, как использовать **конструктор шейдеров**, чтобы экспортировать шейдер DGSL для использования в приложении.

## <a name="export-a-shader"></a>Экспорт шейдера

Чтобы использовать шейдер в приложении после создания с помощью конструктора шейдеров, его нужно экспортировать в формате, совместимый с API графики. Шейдер можно экспортировать разными способами для достижения различных целей.

1. В Visual Studio откройте файл **Visual Shader Graph (.dgsl)** .

     Если у вас нет файла **Визуальный граф шейдера (DGSL)** , создайте его, как описано в разделе [Практическое руководство. Создание простейшего шейдера цвета](../designers/how-to-create-a-basic-color-shader.md).

2. На панели инструментов **Конструктор шейдеров** выберите **Дополнительно** > **Экспорт** > **Экспортировать как**. Откроется диалоговое окно **Экспортировать шейдер**.

3. В раскрывающемся списке **Тип файла** выберите формат для экспорта.

     Ниже приведен список доступных форматов:

     **Шейдер пикселей HLSL (\*.hlsl)** Экспортирует шейдер в виде исходного кода HLSL. Этот параметр позволяет позднее изменить шейдер, даже после его развертывания в приложении. Это может упростить отладку и исправление кода с учетом проблем, возникших у конечных пользователей, но также позволяет пользователю легче вносить в шейдер нежелательные изменения, например чтобы получить незаслуженное преимущество в конкурентной игре. Это также может увеличить время загрузки шейдера.

     **Скомпилированный шейдер пикселей (\*.cso)** Экспортирует шейдер в виде байт-кода HLSL. Этот параметр позволяет позднее изменить шейдер, даже после его развертывания в приложении. Это может упростить отладку и исправление кода с учетом проблем, возникших у конечных пользователей, а так как шейдер компилируется предварительно, его загрузка приложением не создает дополнительных издержек во время выполнения. Достаточно опытные пользователи все равно могут внести нежелательные изменения в шейдер, однако компиляция шейдера значительно усложняет эту задачу.

     **Заголовок C++ (\*.h)** Экспортирует шейдер в виде заголовка в стиле C, который определяет массив байтов, содержащий байт-код HLSL. Этот параметр увеличивает временные затраты на отладку и исправление кода с учетом проблем, возникших у конечных пользователей, так как для проверки исправления приложения требуется перекомпилировать. Однако этот параметр делает практически невозможным внесение нежелательных изменений в шейдер после его развертывания в приложении.

4. В поле со списком **Имя файла** укажите имя для экспортируемого шейдера и нажмите кнопку **Сохранить**.

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Создание простейшего шейдера цвета](../designers/how-to-create-a-basic-color-shader.md)
- [Конструктор шейдеров](../designers/shader-designer.md)
