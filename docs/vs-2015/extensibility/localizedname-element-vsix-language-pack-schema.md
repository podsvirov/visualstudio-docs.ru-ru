---
title: Элемент LocalizedName (схема языкового пакета VSIX) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58e491290122a9d525ff8129333ac0f52ac5f778
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284364"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Элемент LocalizedName (схема языкового пакета VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обязательный. Локализованное имя устанавливаемого расширения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|None||  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Обязательный. Предоставляет корневой элемент для языкового пакета VSIX.|  
  
## <a name="text-value"></a>Текстовое значение  
 Обязательный. Имя языкового пакета на целевом языке.  
  
## <a name="element-information"></a>Сведения об элементе  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Пространство имен    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Имя схемы   |                 Схема языкового пакета VSIX                 |
| Файл проверки |                Всикслангуажепакксчема. xsd                 |
|  Может быть пустым   |                      Неприменимо                       |
  
## <a name="see-also"></a>См. также:  
 [Справочник по схеме языкового пакета VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)   
 [Справочник по схеме расширения VSIX 1,0](/previous-versions/dd393700(v=vs.110))
