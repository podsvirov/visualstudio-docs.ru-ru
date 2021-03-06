---
title: Элемент Commands | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739685"
---
# <a name="commands-element"></a>Элемент Commands
Представляет коллекцию команд на панели инструментов VSPackage. Коллекция может содержать до пяти подразделов следующим образом: меню, группы, кнопки, КомБОС и точечные рисунки.

 Каждый дочерний элемент подраздела, например, определяется \<Menu> уникальным идентификатором команды, который является парой GUID и числовым идентификатором. GUID определяет "набор команд" и используется для группирования логически связанных команд. Пакет VSPackage должен определить собственный набор команд, чтобы избежать конфликтов с идентификаторами команд, определенными другими пакетами VSPackage.

## <a name="syntax"></a>Синтаксис

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|пакет|GUID, определяющий пакет VSPackage, предоставляющий команды.<br /><br /> Например, Package = "guidVsPackage1Pkg".|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент menus](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|
|[Элемент Groups](../extensibility/groups-element.md)|Содержит записи, определяющие группы команд в VSPackage.|
|[Button, элемент](../extensibility/buttons-element.md)|Группирует элементы кнопки.|
|[Bitmap, элемент](../extensibility/bitmaps-element.md)|Группирует элементы битовой карты.|
|[КомБОС, элемент](../extensibility/combos-element.md)|Элементы комбинированных элементов групп.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Коммандтабле, элемент](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, которые пакет VSPackage предоставляет интегрированной среде разработки. Возможные элементы: пункты меню, меню, панели инструментов и поля со списком.|

## <a name="example"></a>Пример
 В следующем примере показано, как использовать [элемент Commands](../extensibility/commands-element.md).

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>См. также раздел
- [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
