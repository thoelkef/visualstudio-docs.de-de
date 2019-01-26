---
title: IPropertyProxyProvider | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyProvider
helpviewer_keywords:
- IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 716f3caedd2b3da9ce115148ecf15b33834238fc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953876"
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Diese Schnittstelle stellt eine Proxyschnittstelle zum Anzeigen und ändern die Daten eines Objekts bereit.  
  
## <a name="syntax"></a>Syntax  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung (EE) implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle als Teil der EE Unterstützung des Typ-Schnellansichten.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugProperty3` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die `IPropertyProxyProvider` -Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Ruft eine Eigenschaft Proxyschnittstelle zum Anzeigen von Daten für ein Objekt ab.|  
  
## <a name="remarks"></a>Hinweise  
 Obwohl die EE dieser Schnittstelle, die Implementierung von implementiert [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) erfolgt in der Regel durch [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Finden Sie unter [visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) ausführliche Informationen zum Abrufen der IEEVisualizerService-Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)