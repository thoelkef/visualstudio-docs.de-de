---
title: "IPropertyProxyEESide | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IPropertyProxyEESide"
helpviewer_keywords: 
  - "IPropertyProxyEESide-Schnittstelle"
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt Methoden für die Ansichtsdaten für das zugeordnete Objekt bereit.  Diese Schnittstelle ist Teil der Unterstützung für Typ schnellansichten.  
  
## Syntax  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Ausdrucksauswertung implementiert diese Schnittstelle, um Typ schnellansichten zu unterstützen.  
  
## Hinweise für Aufrufer  
 [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) Aufruf zum Abrufen dieser Schnittstelle.  Aufruf [QueryInterface](/visual-cpp/atl/queryinterface) auf einer [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)\-Schnittstelle zu erhalten, die [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)\-Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 Die folgenden Methoden werden durch diese Schnittstelle implementiert:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|Initialisiert einen Datenquellenanbieter, damit die Daten des Objekts zugegriffen werden kann.|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|Ruft Informationen über die Assembly des Objekts ab.|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|Ruft die ursprünglichen Daten für das Objekt ab.|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|Erstellt eine Kopie einer vorhandenen Datenspeicherung.|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|Erstellt einen Verweis auf eine vorhandene Datenspeicherung.|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|Ruft Informationen zu einer bestimmten Assembly im Kontext der Assembly ab, die dieses Objekt enthält.|  
  
## Hinweise  
 Eine Typ schnellansicht verwendet diese Schnittstelle, um die Werte zuzugreifen, die dem Objekt zugeordnet sind, auf die diese Schnittstelle ein Teil ist.  Die Daten werden von der [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)\-Schnittstelle zugegriffen, die eine schreibgeschützte Ansicht der Daten bereitstellt.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Typ\-Schnellansicht und benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)