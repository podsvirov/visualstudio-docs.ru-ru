---
title: Элемент Дефаултнаме (шаблоны Visual Studio) | Документация Майкрософт
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#DefaultName
helpviewer_keywords:
- DefaultName element [Visual Studio project templates]
ms.assetid: 0ff056c8-b9d2-4747-9308-92adf1811491
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92bd29824cf1d3b91a7bdaa7220479c583ad0f23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712304"
---
# <a name="defaultname-element-visual-studio-templates"></a>Элемент Дефаултнаме (шаблоны Visual Studio)
Указывает имя, которое будет создавать система проектов Visual Studio для проекта или элемента при его создании.

 \<VSTemplate> \<TemplateData>
 \<DefaultName>

## <a name="syntax"></a>Синтаксис

```
<DefaultName>
    Default Project Name
</DefaultName>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Обязательный элемент.<br /><br /> Определяет категорию шаблона и то, отображается ли он в диалоговом окне **Новый проект** или **Добавить новый элемент** .|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение является обязательным.

 В этом тексте указывается имя проекта или элемента по умолчанию.

## <a name="remarks"></a>Remarks
 Параметр `DefaultName` является необязательным элементом.

 Для проектов этот элемент указывает имя каталога, в котором хранится проект на диске. Для элементов указывает имя файла исходного файла.

 При создании проекта или элемента можно изменить имя по умолчанию, используя параметр **имя** , который доступен в диалоговом окне **Создание проекта** или **Добавление нового элемента** .

 Если не требуется, чтобы система проектов создавала имя по умолчанию для проекта или элемента, установите для элемента [провидедефаултнаме](../extensibility/providedefaultname-element-visual-studio-templates.md) значение `False` .

## <a name="example"></a>Пример
 В следующем примере показаны метаданные для стандартного шаблона элемента для [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] класса.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме шаблонов Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Создание шаблонов проектов и элементов](../ide/creating-project-and-item-templates.md)
