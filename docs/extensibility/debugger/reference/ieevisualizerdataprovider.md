---
title: "IEEVisualizerDataProvider | Microsoft Docs"
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
  - "IEEVisualizerDataProvider"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider-Schnittstelle"
ms.assetid: 5fdfe6e3-b94e-4edb-acc5-41d8773d8ca5
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle bietet die Möglichkeit, den Wert eines Objekts mithilfe einer Schnellansicht Typ zu ändern.  
  
## Syntax  
  
```  
IEEVisualizerDataProvider : IUnknown  
```  
  
## Hinweise für Implementierer  
 Die Auswertung eines Ausdrucks implementiert diese Schnittstelle, um die Änderung von Daten auf ein Objekt über eine Schnellansicht Typ unterstützen.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird verwendet, bei der Erstellung der [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Objekt durch einen Aufruf von [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md). Ausführliche Informationen finden Sie unter [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md).  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CanSetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-cansetobjectforvisualizer.md)|Bestimmt, ob es möglich ist, aktualisieren Sie das Objekt \(und folglich den Wert\), die diese Schnellansicht ist darstellt.|  
|[GetNewObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)|Erzwingt eine erneute Bewertung des Objekts für diese Schnellansicht.|  
|[GetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getobjectforvisualizer.md)|Ruft ein vorhandenes Objekt für diese Schnellansicht \(keine Auswertung erfolgt\).|  
|[SetObjectForVisualizer](../../../extensibility/debugger/reference/ieevisualizerdataprovider-setobjectforvisualizer.md)|Aktualisiert das Objekt für diese Schnellansicht, ändern und somit auch den Wert, den die Schnellansicht enthält.|  
  
## Hinweise  
 Die schnellansichtsdienst \(dargestellt durch die [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) Schnittstelle und zurückgegebene [CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)\) behält einen Verweis auf das Objekt implementiert die `IEEVisualizerDataProvider` Schnittstelle. Daher die `IEEVisualizerDataProvider` Schnittstelle sollte nicht implementiert werden, auf das gleiche Objekt, implementiert die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) wenn das Objekt einen Verweis auf verwaltet die `IEEVisualizerService` Objekt: führt ein zirkulärer Verweis und ein Deadlock tritt auf, wenn die Objekte zerstört. Die empfohlene Vorgehensweise ist das implementieren `IEEVisualizerDataProvider` auf ein separates Objekt, das `IDebugProperty2` \-Objekt Delegaten ohne Aufruf `IUnknown::AddRef` darauf.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)