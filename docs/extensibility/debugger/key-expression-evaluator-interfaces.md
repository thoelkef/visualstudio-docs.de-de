---
title: "Schl&#252;sselausdruck Evaluator-Schnittstellen | Microsoft Docs"
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
  - "Auswertung von Ausdrücken, Schnittstellen"
ms.assetid: 1cac9aa3-0867-4e12-a16e-1e90abbc0fb6
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Schl&#252;sselausdruck Evaluator-Schnittstellen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn Sie eine Auswertung eines Ausdrucks \(EE\), zusammen mit den Auswertungskontext zu schreiben, sollten Sie die folgenden Schnittstellen vertraut sein.  
  
## Eine Beschreibung der Benutzeroberfläche  
  
-   [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)  
  
     Verfügt über eine einzelne Methode, [GetAddress](../../extensibility/debugger/reference/idebugaddress-getaddress.md), der einer Datenstruktur Ruft den aktuellen Punkt der Ausführung darstellt. Die Datenstruktur ist eines der drei Argumente, die an die Debugging\-Modul \(DE\) übergibt die [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) Methode zum Auswerten eines Ausdrucks. Diese Schnittstelle wird in der Regel durch die Symbol\-Anbieter implementiert.  
  
-   [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)  
  
     Hat die [Binden](../../extensibility/debugger/reference/idebugbinder-bind.md) Methode, die den Speicherbereich abruft, der den aktuellen Wert eines Symbols enthält. Sowohl der enthaltenden Methode, dargestellt durch eine [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) \-Objekt und dem Symbol selbst, dargestellt durch eine [IDebugField](../../extensibility/debugger/reference/idebugfield.md) Objekt `IDebugBinder::Bind` Gibt den Wert des Symbols.`IDebugBinder` wird in der Regel durch die DE implementiert.  
  
-   [IDebugField](../../extensibility/debugger/reference/idebugfield.md)  
  
     Stellt einen einfachen Datentyp dar. Verwenden Sie für komplexe Typen wie Arrays und Methoden, die abgeleitete [IDebugArrayField](../../extensibility/debugger/reference/idebugarrayfield.md) und [IDebugMethodField](../../extensibility/debugger/reference/idebugmethodfield.md) Schnittstellen bzw..[IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) eine andere wichtige abgeleitete Schnittstelle, die Symbole darstellt, die anderen Symbolen, z. B. Methoden oder Klassen enthält. Die `IDebugField` \-Schnittstelle \(und seine abgeleiteten\) werden in der Regel durch die Symbol\-Anbieter implementiert.  
  
     Ein `IDebugField` Objekt kann es sich um verwendet, um den Namen und Typ eines Symbols zu finden und, zusammen mit einem [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) Objekt, kann verwendet werden, um den Wert zu ermitteln.  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
     Stellt die eigentlichen Bits des Werts eines Symbols zur Laufzeit dar.[Binden](../../extensibility/debugger/reference/idebugbinder-bind.md) akzeptiert ein [IDebugField](../../extensibility/debugger/reference/idebugfield.md) \-Objekt, das durch ein Symbol dargestellt, und gibt ein [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) Objekt. Die [GetValue](../../extensibility/debugger/reference/idebugobject-getvalue.md) \-Methode gibt den Wert des Symbols in einem Puffer. Ein DE implementiert in der Regel diese Schnittstelle, um den Wert einer Eigenschaft im Speicher darstellen.  
  
-   [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md)  
  
     Diese Schnittstelle stellt die Auswertung eines Ausdrucks selbst. Die wichtigste Methode ist [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md), welche gibt eine [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle.  
  
-   [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md)  
  
     Diese Schnittstelle stellt einen analysierten Ausdruck ausgewertet werden kann. Ist die wichtigste Methode [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) welche gibt ein IDebugProperty2, den Wert und Typ des Ausdrucks darstellt.  
  
-   [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)  
  
     Diese Schnittstelle stellt einen Wert und Typ und das Ergebnis der Auswertung eines Ausdrucks ist.  
  
## Siehe auch  
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md)