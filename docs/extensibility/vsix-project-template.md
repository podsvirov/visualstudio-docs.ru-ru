---
title: Шаблон проекта VSIX | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697932"
---
# <a name="vsix-project-template"></a>Шаблон проекта VSIX

Можно использовать шаблон проекта VSIX для упаковки одного или нескольких расширений Visual Studio в проект VSIX, а затем опубликовать пакет на веб-сайте [Visual Studio Marketplace](https://marketplace.visualstudio.com/) .

 Развертывание VSIX поддерживает пакеты VSPackage, сборки, компоненты MEF, шаблоны проектов, шаблоны элементов, элементы управления панели элементов и пользовательские типы расширений.

> [!NOTE]
> Для использования проектов VSIX необходимо установить Visual Studio SDK. Дополнительные сведения о пакете SDK для Visual Studio см. в разделе [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Где найти шаблон проекта VSIX

Шаблон проекта VSIX доступен в диалоговом окне **Новый проект** путем поиска "VSIX".  Существует и версия C#, и Visual Basic.

> [!TIP]
> Убедитесь, что в раскрывающемся списке в верхней части диалогового окна " **Новый проект** " указан .NET Framework 4,5 или более поздней версии.

## <a name="uses-of-the-vsix-project-template"></a>Использование шаблона проекта VSIX

Шаблон проекта VSIX имеет два основных применения:

- Для развертывания шаблонов проектов, шаблонов элементов и расширений.

- Значение, чтобы заключить выходные данные нескольких расширений в один пакет развертывания.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Упаковка расширения в пустой проект VSIX

Можно упаковать существующее расширение или расширение, которое еще не имеет поддержки VSIX, заключив его в пустой проект VSIX. Упакованное расширение должно иметь тип, поддерживаемый [схемой VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Упаковка расширения с помощью проекта VSIX

1. Создайте проекты, составляющие расширение.

2. Создайте проект VSIX с помощью шаблона **проекта VSIX** .

    *Source. extension. vsixmanifest* открывается в **конструкторе манифестов**.

3. На вкладке **активы** нажмите кнопку **создать** .

    Откроется диалоговое окно **Добавление нового ресурса** .

4. В списке **тип** выберите тип добавляемого расширения.

5. Чтобы добавить расширение или элемент содержимого, который включается в текущее решение (например, шаблон элемента или скомпилированную сборку), выполните следующие действия.

   1. В списке **источник** выберите **проект в текущем решении**.

   2. В списке **проект** выберите имя расширения.

   3. В поле **внедрить в эту папку** введите имя папки, в которую будет внедрен ресурс, а затем нажмите кнопку **ОК** .

6. Чтобы добавить расширение или элемент содержимого, который не входит в текущее решение, выполните следующие действия.

   1. В списке **источник** выберите **файл в файловой системе**.

   2. В поле **путь** введите полный путь к скомпилированному или сжатому файлу расширения или воспользуйтесь кнопкой **Обзор** , чтобы перейти к файлу.

   3. В поле **внедрить в эту папку** введите имя папки, в которую будет внедрен ресурс, а затем нажмите кнопку **ОК** .

7. Если вы хотите, чтобы пакет включал дополнительные расширения, добавьте их одинаковым образом.

8. Создайте решение.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает *VSIX* -файл, содержащий файл манифеста VSIX, файл [Content_Types]*. XML* и все ресурсы расширения, добавленные в проект.

## <a name="see-also"></a>См. также раздел

- [Справочник по схеме расширения VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
