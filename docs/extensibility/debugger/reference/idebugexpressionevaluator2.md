---
title: "IDebugExpressionEvaluator2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2-Schnittstelle"
ms.assetid: cebe649f-1c77-4d33-854f-30d4f00eceb4
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugExpressionEvaluator2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Stellt eine erweiterte Version einer Auswertung eines Ausdrucks \(EE\) dar.  
  
## Syntax  
  
```  
IDebugExpressionEvaluator2 : IDebugExpressionEvaluator  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von der ausdrucksauswertung implementiert.  
  
## Methoden  
 Zusätzlich zu den Methoden für die [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md) Schnittstelle, die diese Schnittstelle implementiert die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetService](../../../extensibility/debugger/reference/idebugexpressionevaluator2-getservice.md)|Ruft ein Dienstobjekt unter Berücksichtigung der eindeutigen Bezeichner ab.|  
|[PreloadModules](../../../extensibility/debugger/reference/idebugexpressionevaluator2-preloadmodules.md)|Die Module, die vom Anbieter angegebene Symbol gekennzeichnet werden vorab geladen.|  
|[SetCallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcallback.md)|Ermöglicht die Auswertung eines Ausdrucks \(EE\) an die Rückrufschnittstelle, auf denen der Debugger\-Modul \(DE\) Metric\-Einstellung lesen.|  
|[SetCorPath](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setcorpath.md)|Legt den Pfad fest, um die common Language Runtime \(CLR\), das im Debugger geladen.|  
|[SetIDebugIDECallback](../../../extensibility/debugger/reference/idebugexpressionevaluator2-setidebugidecallback.md)|Ermöglicht eine Debugging\-Modul, um einen Rückruf an der Auswertung eines Ausdrucks während der Initialisierung zu übergeben.|  
|[Beenden](../../../extensibility/debugger/reference/idebugexpressionevaluator2-terminate.md)|Beendet und bereinigt die Auswertung eines Ausdrucks.|  
  
## Anforderungen  
 Header: Ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll