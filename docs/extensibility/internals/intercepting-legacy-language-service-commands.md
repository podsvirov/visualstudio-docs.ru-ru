---
title: Перехват команд языковой службы прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707450"
---
# <a name="intercepting-legacy-language-service-commands"></a>Перехват команд языковой службы прежних версий
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] можно использовать команды перехвата языковой службы, которые в противном случае будут обработаны текстовым представлением. Это полезно для поведения конкретного языка, которое не управляется представлением текста. Вы можете перехватить эти команды, добавив один или несколько фильтров команд в текстовое представление из языковой службы.

## <a name="getting-and-routing-the-command"></a>Получение и маршрутизация команды
 Фильтр команд — это <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> объект, отслеживающий определенные последовательности символов или ключевые команды. С одним представлением текста можно связать более одного фильтра команд. Каждое текстовое представление поддерживает цепочку фильтров команд. После создания нового фильтра команды вы добавите фильтр в цепочку для соответствующего текстового представления.

 Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод для, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> чтобы добавить фильтр команды в цепочку. При вызове <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] возвращает другой фильтр команд, к которому можно передать команды, не обрабатываемые фильтром команд.

 Для обработки команд доступны следующие параметры.

- Обработайте команду и передайте команду в следующий фильтр команд в цепочке.

- Обработайте команду и не передавайте команду в следующий фильтр команд.

- Не обрабатывать команду, но передайте ее в следующий фильтр команд.

- Игнорируйте команду. Не обрабатывайте его в текущем фильтре и не передавайте его следующему фильтру.

  Сведения о том, какие команды должны быть обработаны языковой службой, см. в разделе [важные команды для фильтров языковой службы](../../extensibility/internals/important-commands-for-language-service-filters.md).
