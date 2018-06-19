---
title: IPropertyProxyEESide | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f1dea4c3124cd532177618d84e2302a32e8bc4a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31125478"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
Diese Schnittstelle bietet Methoden zum Anzeigen von Daten auf das zugeordnete Objekt. Diese Schnittstelle ist Teil der Unterstützung für die Typ-Schnellansichten.  
  
## <a name="syntax"></a>Syntax  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Eine ausdrucksauswertung implementiert diese Schnittstelle, um die Typ-Schnellansichten unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) beim Abrufen dieser Schnittstelle. Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle zum Abrufen der [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md) Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgenden Methoden werden von dieser Schnittstelle implementiert:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialisiert ein Datenquellenanbieter, so, dass die Daten des Objekts zugegriffen werden können.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Ruft Informationen zu der Assembly des Objekts ab.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ruft den ursprünglichen Daten für das Objekt ab.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Erstellt eine Kopie einer vorhandenen Datenspeicher.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Erstellt einen Verweis auf einen vorhandenen Datenspeicher.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Ruft Informationen zu einer bestimmten Assembly im Kontext der Assembly mit diesem Objekt ab.|  
  
## <a name="remarks"></a>Hinweise  
 Eine Schnellansicht Typ mithilfe dieser Schnittstelle Zugriff auf die Werte, die das Objekt, dem diese Schnittstelle Teil ist zugeordnet. Die Daten erfolgt über die [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) -Schnittstelle, die eine schreibgeschützte Ansicht der Daten bereitstellt.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Typ-Schnellansicht und den benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)