---
title: Ипропертипроксеесиде | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 660c792d9e13fabbd433aee46c57474fb824453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684674"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет методы для просмотра данных в связанном объекте. Этот интерфейс является частью поддержки визуализаторов типов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Средство оценки выражений реализует этот интерфейс для поддержки визуализаторов типов.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Чтобы получить этот интерфейс, вызовите [жетпропертипрокси](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) . Вызовите [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) в интерфейсе [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , чтобы получить интерфейс [ипропертипроксипровидер](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) .  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке vtable  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Инициализирует поставщик источника данных, чтобы можно было получить доступ к данным этого объекта.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Извлекает сведения о сборке объекта.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Возвращает исходные данные для объекта.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Создает копию существующего хранилища данных.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Создает ссылку на существующее хранилище данных.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Извлекает сведения о конкретной сборке в контексте сборки, содержащей этот объект.|  
  
## <a name="remarks"></a>Remarks  
 Визуализатор типов использует этот интерфейс для доступа к значениям, связанным с объектом, частью которого является этот интерфейс. Доступ к данным осуществляется через интерфейс [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md) , который предоставляет представление данных только для чтения.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Основные интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
