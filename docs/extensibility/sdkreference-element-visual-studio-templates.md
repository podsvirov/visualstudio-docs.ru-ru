---
title: Элемент SDKReference (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 72c8b352-0b7a-42b3-ba5d-2a2d1e90c34b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f43c813e688c1e175f1d36e6f06125f92404c48
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700167"
---
# <a name="sdkreference-element-visual-studio-templates"></a>SDKReference - элемент (шаблоны Visual Studio)
Указывает, что шаблон элемента использует ссылку на пакет SDK.

## <a name="syntax"></a>Синтаксис

```xml
<VSTemplate>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>SDKname</SDKReference>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Ссылки](../extensibility/reference-element-visual-studio-templates.md)|Указывает ссылку на сборку, которую нужно добавить при добавлении элемента в проект.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

## <a name="remarks"></a>Remarks
 Этот текст определяет ссылку на пакет SDK, которую нужно добавить в проект при создании экземпляра шаблона элемента.

```xml
<VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
    <TemplateData> . . . </TemplateData>
    <TemplateContent>
        <References>
            <Reference>
                <SDKReference>Microsoft Visual C++ Runtime Package, Version=11.0.0.0</SDKReference>
...
```

## <a name="see-also"></a>См. также раздел
- [Элемент References (шаблоны Visual Studio)](../extensibility/references-element-visual-studio-templates.md)
- [Элемент Reference (шаблоны Visual Studio)](../extensibility/reference-element-visual-studio-templates.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
