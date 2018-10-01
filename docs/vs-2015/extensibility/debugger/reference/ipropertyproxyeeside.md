---
title: IPropertyProxyEESide | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a012c40026921419fee1f70b3db8294e3397079d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47524105"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IPropertyProxyEESide](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ipropertyproxyeeside).  
  
Diese Schnittstelle bietet Methoden zum Anzeigen von Daten für das zugeordnete Objekt. Diese Schnittstelle ist Teil der Unterstützung für Typ-Schnellansichten.  
  
## <a name="syntax"></a>Syntax  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine ausdrucksauswertung implementiert diese Schnittstelle, um die Typ-Schnellansichten unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) dieser Schnittstelle abgerufen. Rufen Sie [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) auf eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle zum Abrufen der [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgenden Methoden werden von dieser Schnittstelle implementiert:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialisiert ein Datenquellenanbieter, sodass die Daten des Objekts zugegriffen werden können.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Ruft Informationen zu der Assembly des Objekts ab.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ruft den ursprünglichen Daten für das Objekt ab.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Erstellt eine Kopie einer vorhandenen Data Storage.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Erstellt einen Verweis auf eine vorhandene Datenspeicher.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Ruft Informationen zu einer bestimmten Assembly im Kontext der Assembly mit der dieses Objekt ab.|  
  
## <a name="remarks"></a>Hinweise  
 Eine typschnellansicht verwendet diese Schnittstelle zum Zugriff auf die Werte von das Objekt, dem diese Schnittstelle Teil ist. Die Daten erfolgt über die [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) Schnittstelle, die eine schreibgeschützte Ansicht der Daten bereitstellt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

