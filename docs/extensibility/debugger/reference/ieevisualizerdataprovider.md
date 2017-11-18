---
title: IEEVisualizerDataProvider | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerDataProvider
helpviewer_keywords: IEEVisualizerDataProvider interface
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9ffe7e33b4652c0f0d3bd506e28d14c5b0949983
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ieevisualizerdataprovider"></a>IEEVisualizerDataProvider
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle bietet die Möglichkeit, ein Objekt als Wert in einer Schnellansicht Typ zu ändern.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die ausdrucksauswertung implementiert diese Schnittstelle zum Ändern von Daten auf ein Objekt über eine Schnellansicht Typ unterstützen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird verwendet, bei der Erstellung der [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Objekt durch einen Aufruf von [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Finden Sie unter [Visualizing und Anzeige von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) Weitere Details.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Bestimmt, ob es möglich ist, aktualisieren Sie das Objekt (und danach den Wert), die diese Schnellansicht ist, darstellt.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Erzwingt eine erneute Auswertung des Objekts für diese Schnellansicht.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ruft ein vorhandenes Objekt für diese Schnellansicht (keine Auswertung erfolgt).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualisiert das Objekt für diese Schnellansicht, ändern und somit auch den Wert, den die Schnellansicht enthält.|  
  
## <a name="remarks"></a>Hinweise  
 Die schnellansichtsdienst (dargestellt durch die [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) -Schnittstelle und zurückgegebenes [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)) behält einen Verweis auf das Objekt, durch die `IEEVisualizerDataProvider` Schnittstelle . Daher die `IEEVisualizerDataProvider` -Schnittstelle sollten nicht implementiert werden, auf das gleiche Objekt, implementiert der [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) Wenn dieses Objekt einen Verweis auf verwaltet die `IEEVisualizerService` Objekt: ein Zirkelverweis Ergebnisse und ein Deadlock tritt auf, wenn die Objekte zerstört werden. Die empfohlene Vorgehensweise besteht darin zu implementieren `IEEVisualizerDataProvider` auf ein separates Objekt, das `IDebugProperty2` -Objekt Delegaten ohne Aufruf `IUnknown::AddRef` darauf.  
  
## <a name="requirements"></a>Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Ausdruck Auswertung Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)