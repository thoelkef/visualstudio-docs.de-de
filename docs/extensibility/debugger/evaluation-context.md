---
title: "Evaluierungskontext | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen die Auswertung von Ausdrücken [Debuggen SDK]"
  - "Auswertung von Ausdrücken, Kontext"
ms.assetid: 008a20c7-1b27-4013-bf96-d6a3f510da02
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Evaluierungskontext
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn das Debugging\-Modul \(DE\) der Auswertung eines Ausdrucks \(EE\) aufruft, werden drei Argumente zu übergeben [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Kontext zum Suchen und Auswerten von Symbolen, bestimmen, wie in der folgenden Tabelle dargestellt.  
  
## Argumente  
  
|Argument|Beschreibung|  
|--------------|------------------|  
|`pSymbolProvider`|Eine [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) Schnittstelle, die den Symbol\-Handler \(SH\) angibt, verwendet werden, zum Erkennen des Symbols.|  
|`pAddress`|Eine [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) \-Schnittstelle, die den aktuellen Punkt der Ausführung angibt. Dies kann verwendet werden, um die Methode zu suchen, die den ausgeführten Code enthält.|  
|`pBinder`|Eine [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) \-Schnittstelle, die mit dem Wert und Typ eines Symbols mit dem angegebenen Namen gefunden werden kann.|  
  
 `IDebugParsedExpression::EvaluateSync` Gibt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) \-Schnittstelle, die den resultierenden Wert und Typ darstellt.  
  
## Siehe auch  
 [Schlüsselausdruck Evaluator\-Schnittstellen](../../extensibility/debugger/key-expression-evaluator-interfaces.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)   
 [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)