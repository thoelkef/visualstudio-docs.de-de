---
title: IPropertyProxyProvider | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyProvider
helpviewer_keywords: IPropertyProxyProvider interface
ms.assetid: 52e9f7fc-6fe0-4d23-890b-5673dca8c3cb
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: de400fc9e5b631a7ccffb0547fa693a8bf0ac419
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyprovider"></a>IPropertyProxyProvider
Diese Schnittstelle bietet eine Proxyschnittstelle zum Anzeigen und Ändern von Daten in einem Objekt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IPropertyProxyProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung (EE) implementiert diese Schnittstelle für das gleiche Objekt, das implementiert die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) -Schnittstelle als Teil der EE-Unterstützung des Typ-Schnellansichten.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf eine `IDebugProperty3` Schnittstelle, um diese Schnittstelle zu erhalten.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die `IPropertyProxyProvider` Schnittstelle implementiert, die folgende Methode:  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)|Ruft eine Eigenschaft Proxyschnittstelle zum Anzeigen von Daten für ein Objekt ab.|  
  
## <a name="remarks"></a>Hinweise  
 Obwohl die EE über diese Schnittstelle, die Implementierung von implementiert [GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) erfolgt in der Regel durch [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md). Finden Sie unter [Visualizing und Anzeige von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) ausführliche Informationen zum Abrufen der IEEVisualizerService-Schnittstelle.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)   
 [Typ-Schnellansicht und den benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)