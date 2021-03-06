---
title: 'CA1824: Пометка сборок с помощью NeutralResourcesLanguageAttribute | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19077a63d5aa22bda3f968943703a82488e2745d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545292"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824. Помечайте сборки с помощью NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|Категория|Microsoft. Performance|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка содержит ресурс на основе **RESX**, но не имеет <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> примененного к нему ресурса.

## <a name="rule-description"></a>Описание правила
 Атрибут **NeutralResourcesLanguage** информирует **ResourceManager** о языке, который использовался для вывода ресурсов нейтральной культуры для сборки. При поиске ресурсов в той же культуре, что и нейтральный язык ресурсов, **ResourceManager** автоматически использует ресурсы, расположенные в основной сборке. Это делается вместо поиска вспомогательной сборки, имеющей текущий язык и региональные параметры пользовательского интерфейса для текущего потока. При этом повышается эффективность поиска первого загружаемого ресурса и может сократиться рабочее множество.

## <a name="fixing-violations"></a>Устранение нарушений
 Чтобы устранить нарушение этого правила, добавьте атрибут в сборку и укажите язык ресурсов нейтрального языка и региональных параметров.

## <a name="specifying-the-language"></a>Указание языка

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>Указание языка для ресурса нейтрального языка и региональных параметров

1. В **Обозреватель решений**щелкните правой кнопкой мыши проект и выберите пункт **свойства**.

2. В левой панели навигации выберите **приложение**, а затем щелкните **сведения о сборке**.

3. В диалоговом окне **сведения о сборке** выберите язык из раскрывающегося списка **нейтральный язык** .

4. Нажмите кнопку **ОК**.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Предупреждение можно отключить от этого правила. Однако производительность запуска может снизиться.
