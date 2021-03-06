---
title: Регистрация обработчиков команд сборки взаимодействия | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9d2822e9eef36806f5c251813925fb4244242519
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705816"
---
# <a name="registering-interop-assembly-command-handlers"></a>Регистрация обработчиков команд сборки взаимодействия
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Пакет VSPackage должен быть зарегистрирован в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , чтобы интегрированная среда разработки (IDE) правильно маршрутизирует свои команды.  
  
 Реестр можно обновить либо вручную, либо с помощью файла регистратора (RGS). Для получения дополнительной информации см. [Creating Registrar Scripts](https://msdn.microsoft.com/library/cbd5024b-8061-4a71-be65-7fee90374a35).  
  
 Платформа управляемого пакета (MPF) предоставляет эту функцию через <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> класс.  
  
 [Справочные ресурсы по формату командной таблицы](https://msdn.microsoft.com/09e9c6ef-9863-48de-9483-d45b7b7c798f) находятся в неуправляемых библиотеках DLL ВСПОМОГАТЕЛЬных интерфейсов.  
  
## <a name="command-handler-registration-of-a-vspackage"></a>Регистрация пакета VSPackage в обработчике команд  
 Пакет VSPackage, выступающий в качестве обработчика для команд на основе ПОЛЬЗОВАТЕЛЬСКОГО интерфейса, требует наличия записи реестра с именем после пакета VSPackage `GUID` . Эта запись реестра указывает расположение файла ресурсов пользовательского интерфейса VSPackage и ресурс меню в этом файле. Сама запись реестра находится в папке HKEY_LOCAL_MACHINE \Софтваре\микрософт\висуалстудио \\ *\<Version>* \менус, где *\<Version>* — это версия, например [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 9,0.  
  
> [!NOTE]
> Корневой путь HKEY_LOCAL_MACHINE \Софтваре\микрософт\висуалстудио \\ *\<Version>* можно переопределить с помощью альтернативного корня при [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] инициализации оболочки. Дополнительные сведения о корневом пути см. в разделе [Установка пакетов VSPackage с помощью установщик Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
### <a name="the-ctmenu-resource-registry-entry"></a>Запись реестра ресурсов CTMENU  
 Структура записи реестра:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\  
  Menus\  
    <GUID> = <Resource Information>  
```  
  
 \<*GUID*> — Это пакет `GUID` VSPackage в форме {XXXXXX-XXXX-XXXX-XXXX-XXXXXXXXX}.  
  
 *\<Resource Information>* состоит из трех элементов, разделенных запятыми. Эти элементы по порядку:  
  
 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>  
  
 В следующей таблице описаны поля \<*Resource Information*> .  
  
|Элемент|Описание|  
|-------------|-----------------|  
|\<*Path to Resource DLL*>|Это полный путь к библиотеке DLL ресурсов, содержащей ресурс меню, или оставить это поле пустым, указывая на необходимость использования библиотеки DLL ресурсов VSPackage (как указано в подразделе Packages, где зарегистрирован пакет VSPackage).<br /><br /> Это поле остается незаполненным.|  
|\<*Menu Resource ID*>|Это идентификатор ресурса `CTMENU` , который содержит все элементы пользовательского интерфейса для VSPackage, скомпилированные из [vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) -файла.|  
|\<*Menu Version*>|Это число, используемое в качестве версии `CTMENU` ресурса. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] использует это значение для определения необходимости повторного слияния содержимого `CTMENU` ресурса со своим кэшем всех `CTMENU` ресурсов. Повторная слияние запускается при помощи команды установки devenv.<br /><br /> Изначально это значение должно быть равно 1 и увеличиваться после каждого изменения в `CTMENU` ресурсе и перед повторным слиянием.|  
  
### <a name="example"></a>Пример  
 Ниже приведен пример нескольких записей ресурсов:  
  
```  
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\  
  Menus\  
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10  
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3  
```  
  
## <a name="see-also"></a>См. также:  
 [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды и меню, которые используют сборки взаимодействия](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
