---
title: "IDebugBinder | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder"
helpviewer_keywords: 
  - "IDebugBinder-Schnittstelle"
ms.assetid: d1f31e5b-c6e2-4e02-8959-b3e86041b29c
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# IDebugBinder
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle bindet ein Symbolfeld, das normalerweise von den Symbol\-Anbieter, um einen Speicherkontext oder ein Objekt, der aktuelle Wert des Symbols enthält zurückgegeben.  
  
## Syntax  
  
```  
IDebugBinder : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle unterstützt die Auswertung von Ausdrücken und muss von dem Debugging\-Modul \(DE\) implementiert werden.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird verwendet, während der Auswertung von Ausdrücken und wird normalerweise verwendet, in der Implementierung von [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md).  
  
## Methoden in Vtable\-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBinder`.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md)|Ruft den Speicherkontext oder das Objekt, das den aktuellen Symbolwert enthält.|  
|[ResolveRuntimeType](../../../extensibility/debugger/reference/idebugbinder-resolveruntimetype.md)|Bestimmt den Laufzeittyp eines Objekts.|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugbinder-getmemorycontext.md)|Konvertiert eine Objekt\-Speicherort oder Arbeitsspeicher\-Adresse für einen Speicherkontext.|  
|[GetFunctionObject](../../../extensibility/debugger/reference/idebugbinder-getfunctionobject.md)|Ruft ein [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) Objekt verwendet, um die Parameter zu erstellen.|  
|[ResolveDynamicType](../../../extensibility/debugger/reference/idebugbinder-resolvedynamictype.md)|Ruft den exakten Typ für eine Variable ab.|  
  
## Hinweise  
 Diese Schnittstelle gibt Objekte, die von der Auswertung eines Ausdrucks in verwendeten Strukturen analysieren. Die ausdrucksauswertung wertet einen Ausdruck mit dem Symbol\-Anbieter konvertieren die Symbole im Ausdruck in Instanzen von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md), die jedes Symbol im Hinblick auf den Typ und den Speicherort im Quellcode beschreiben. Die [Binden](../../../extensibility/debugger/reference/idebugbinder-bind.md) \-Methode konvertiert `IDebugField` Objekte [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekte, die eine Verbindung herstellen, oder binden ein Symbol zu geben, in einen tatsächlichen Wert im Arbeitsspeicher. Diese `IDebugObject` Objekte werden dann in eine Analysestruktur für die spätere Auswertung gespeichert.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ausdruck Evaluation\-Schnittstellen](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)