---
title: "IEEVisualizerServiceProvider | Microsoft Docs"
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
  - "IEEVisualizerServiceProvider"
helpviewer_keywords: 
  - "IEEVisualizerServiceProvider-Schnittstelle"
ms.assetid: 859d1a51-1c65-4c8b-ae74-3b74b181ebcd
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerServiceProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle ermöglicht den Zugriff auf eine Methode, die einen schnellansichtsdienst erstellen kann die Schnellansicht Aufgaben für die IDE\-Handle verwendet wird.  
  
## Syntax  
  
```  
IEEVisualizerServiceProvider : IUnknown  
```  
  
## Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um ein Dienstobjekt Schnellansicht zu erstellen, der wiederum mit der Klassen\-IDs angeben \(`CLSID`s\) des Typs Schnellansichten zu Visual Studio\-IDE.  
  
## Hinweise für Aufrufer  
 Ruft die Auswertung eines Ausdrucks \(EE\) [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md) diese Schnittstelle zu erhalten.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CreateVisualizerService](../../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)|Erstellt die schnellansichtsdienst|  
  
## Hinweise  
 Die `IEEVisualizerServiceProvider` Schnittstelle abgerufen wird, während der Durchführung des [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Die schnellansichtsdienst, der diese Schnittstelle erstellt dient zum Bereitstellen von Funktionen zu einer [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) Schnittstelle, die die EE für die Implementierung verantwortlich ist. Die EE ist auch für die Durchführung einer [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Schnittstelle, über die Typ\-Schnellansichten anzeigen und ändern den Wert einer Eigenschaft.  
  
 Finden Sie unter [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md) Weitere Informationen zur Interaktion dieser Schnittstellen.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [Visualisieren und Anzeigen von Daten](../../../extensibility/debugger/visualizing-and-viewing-data.md)