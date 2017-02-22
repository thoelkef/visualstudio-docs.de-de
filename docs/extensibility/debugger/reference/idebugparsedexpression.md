---
title: "IDebugParsedExpression | Microsoft Docs"
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
  - "IDebugParsedExpression"
helpviewer_keywords: 
  - "IDebugParsedExpression-Schnittstelle"
ms.assetid: be6486ed-b070-4898-95b1-58581bcb4447
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugParsedExpression
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Diese Schnittstelle stellt einen analysierten Ausdruck ausgewertet werden kann.  
  
## Syntax  
  
```  
IDebugParsedExpression : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Ausdrucksauswerter implementiert diese Schnittstelle einen analysierten Ausdruck darstellt, der zur Evaluierung bereit ist.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) gibt diese Schnittstelle.  
  
## Methoden in Vtable\-Reihenfolge  
 Die folgende Tabelle zeigt die Methode der `IDebugParsedExpression`.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)|Der analysierten Ausdruck ausgewertet.|  
  
## Hinweise  
 Wenn der Aufrufer bereit zum Auswerten des Ausdrucks ist, ruft er [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Zurückgeben einer [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) die das Ergebnis der Auswertung enthält. Dieser zweiteiligen\-Ansatz für die Evaluierung, Analyse und Bewertung ermöglicht den analysierten Ausdruck mehrmals ausgewertet werden soll, unter Umgehung der zeitaufwändig Analysieren des Ausdrucks.  
  
## Anforderungen  
 Header: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)