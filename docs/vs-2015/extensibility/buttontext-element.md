---
title: Элемент ButtonText | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef22471d20df5582fec96c8a685029a1d475a4a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184566"
---
# <a name="buttontext-element"></a>Элемент ButtonText
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это поле позволяет указать текст, отображаемый в различных меню. По умолчанию `ButtonText` элемент отображается в контроллерах меню. `ButtonText`Элемент также станет значением по умолчанию, если другие текстовые поля пусты. `ButtonText`Элемент не может быть пустым, даже если указаны другие текстовые поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<ButtonText>My Command</ButtonText>  
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
|[Элемент Strings](../extensibility/strings-element.md)|Группирует текстовые элементы, такие как `ButtonText` и `CommandName` .|  
  
## <a name="text-value"></a>Текстовое значение  
 Текстовое значение `ButtonText` элемента содержит текст, отображаемый для пунктов меню, КомБОС и других элементов пользовательского интерфейса, имеющих видимый текст.  
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
