---
title: IEEVisualizerService | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerService
helpviewer_keywords: IEEVisualizerService interface
ms.assetid: 3bdb124b-c582-47ba-b465-13c6a1cdb702
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 404dcdd61955a1d3ac37fc2206d1b0fdf79684f6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerservice"></a>IEEVisualizerService
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle implementiert, wichtige Methoden, die Funktionen zum Angeben der [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) und [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) Schnittstellen.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEEVisualizerService : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um eine ausdrucksauswertung (EE) Typ-Schnellansichten unterstützen können.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ruft die EE [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) diese Schnittstelle nicht als Teil der Unterstützung für die Typ-Schnellansichten abgerufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)|Ruft die Anzahl der benutzerdefinierten Viewer diesen Dienst kennt ab.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)|Ruft die Liste der benutzerdefinierten Viewer ab.|  
|[GetPropertyProxy](../../../extensibility/debugger/reference/ieevisualizerservice-getpropertyproxy.md)|Ein Proxyobjekt für eine Eigenschaft zurückgegeben.|  
|[GetValueDisplayStringCount](../../../extensibility/debugger/reference/ieevisualizerservice-getvaluedisplaystringcount.md)|Ruft die Anzahl von Zeichenfolgen, die für die angegebene Eigenschaft oder das Feld angezeigt.|  
  
## <a name="remarks"></a>Hinweise  
 Die IDE verwendet die [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle, um festzustellen, ob alle benutzerdefinierten Viewer sind, oder geben Sie die Schnellansichten für die Eigenschaft. Durch Erstellen einer Schnellansicht-Diensts (mit [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)), die EE kann die Funktionen zum Angeben der `IDebugProperty3` und [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) (unterstützt anzeigen und Ändern einer der Eigenschaftswert) Schnittstellen und dadurch Typ-Schnellansichten unterstützen.  
  
 Verfügt ein EE benutzerdefinierten Viewer, die selbst implementiert wird, kann die EE Anfügen der `CLSID`s von diesen benutzerdefinierten Viewer bis zum Ende der Liste zurückgegebenes [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md). Dies ermöglicht eine EE Typ-Schnellansichten und einen eigenen benutzerdefinierten Viewer zu unterstützen. Nur stellen sicher, dass [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) das Hinzufügen von jeder benutzerdefinierte Viewer widerspiegelt.  
  
 Finden Sie unter [Typ Schnellansicht und den benutzerdefinierten Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) eine Erläuterung des Unterschieds zwischen Schnellansichten und Viewern.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)   
 [Typschnellansicht und benutzerdefinierter Viewer](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)