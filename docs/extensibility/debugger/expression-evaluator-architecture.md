---
title: "Expression Evaluator-Architektur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ausdrucksauswertungen-Architektur"
  - "ausdrucksauswertungen, Architektur"
  - "Debuggen [Debugging-SDK] ausdrucksauswertungen"
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Expression Evaluator-Architektur
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Eine proprietäre Sprache in Visual Studio\-Debug\-Paket integrieren bedeutet, dass die erforderlichen Expression Evaluator \(EE\) Schnittstellen implementieren und Aufrufen der common Language Runtime\-Symbol Dienstanbieter \(SP\) und Binder\-Schnittstellen. Die SP und Binder\-Objekte zusammen mit der aktuellen Adresse für die Ausführung sind den Kontext, in dem Ausdrücke ausgewertet werden. Die Informationen, die diese Schnittstellen zu erzeugen und nutzen stellt die grundlegenden Konzepte in der Architektur von einem EE dar.  
  
## Übersicht  
  
### Analysieren des Ausdrucks  
 Wenn Sie ein Programm debuggen, werden Ausdrücke ausgewertet, für eine Reihe von Gründen jedoch immer wenn die Anwendung gedebuggt wird an einem Haltepunkt \(entweder ein Haltepunkt platziert, die vom Benutzer oder eine durch eine Ausnahme verursacht\) beendet wurde. Es ist zu diesem Zeitpunkt, wenn Visual Studio einen Stapelrahmen erhält, dargestellt durch die [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) \-Schnittstelle, über die Debugging\-Modul \(DE\). Visual Studio ruft dann [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zum Abrufen der [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Diese Schnittstelle stellt einen Kontext, in dem Ausdrücke ausgewertet werden können; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ist der Einstiegspunkt für den Prozess der Evaluierung. Bis zu diesem Punkt werden alle Schnittstellen durch die DE implementiert.  
  
 Wenn `IDebugExpressionContext2::ParseText` wird aufgerufen, die DE instanziiert die EE verknüpft sind, mit der Sprache der Quelldatei, in der Haltepunkt aufgetreten ist \(die DE instanziiert außerdem die SH an diesem Punkt\). Die EE wird dargestellt, durch die [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) Schnittstelle. Anschließend ruft die DE [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Konvertieren des Ausdrucks \(in Textform\) in einer analysierten Ausdruck bereit, für die Evaluierung. Dieser Ausdruck analysiert wird durch dargestellt die [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle. Beachten Sie, dass der Ausdruck in der Regel analysiert und zu diesem Zeitpunkt nicht ausgewertet.  
  
 DE erstellt ein Objekt, implementiert die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle, setzt die `IDebugParsedExpression` \-Objekt in die `IDebugExpression2` Objekt und gibt den `IDebugExpression2` \-Objekt aus `IDebugExpressionContext2::ParseText`.  
  
### Die Auswertung des Ausdrucks  
 Visual Studio aufgerufen werden, entweder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) zum Auswerten des analysierten Ausdrucks. Beide Methoden aufrufen [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) \(`IDebugExpression2::EvaluateSync` Ruft die Methode sofort beendet, während er sich `IDebugExpression2::EvaluateAsync` Ruft die Methode über einen Hintergrundthread\) um die analysierten Ausdruck auszuwerten und zurückzugeben eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die den Wert und Typ des analysierten Ausdrucks darstellt.`IDebugParsedExpression::EvaluateSync` verwendet den angegebenen SH, und Binder um analysierten Ausdrucks in einen tatsächlichen Wert, dargestellt durch Konvertieren der `IDebugProperty2` Schnittstelle.  
  
### Zum Beispiel  
 Nachdem ein Haltepunkt in einem ausgeführten Programm erreicht ist, der Benutzer möchte eine Variable in anzeigen, die **Schnellüberwachung** im Dialogfeld. Dieses Dialogfeld zeigt den Namen der Variablen, seinen Wert und Typ. Der Benutzer kann den Wert in der Regel ändern.  
  
 Wenn die **Schnellüberwachung** Dialogfeld wird angezeigt, der Name der untersuchten Variablen als Text gesendet wird [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Dies gibt ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt, das in diesem Fall den analysierten Ausdruck darstellt, der Variablen.[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wird aufgerufen, um das Erzeugen einer `IDebugProperty2` Objekt, das den Wert der Variablen und Typ sowie den Namen darstellt. Es ist diese Informationen, die angezeigt wird.  
  
 Wenn der Benutzer den Wert der Variablen, ändert [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) wird aufgerufen, mit dem neuen Wert, der den Wert der Variablen im Speicher ändert, damit er verwendet wird, wenn das Programm fortgesetzt wird ausgeführt.  
  
 Finden Sie unter [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md) Weitere Informationen zu dieser Prozess zum Anzeigen der Werte von Variablen. Finden Sie unter [Ändern des Werts von einer lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md) für weitere Einzelheiten, wie der Wert einer Variablen geändert wird.  
  
## In diesem Abschnitt  
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md)  
 Stellt die Argumente übergeben werden, wenn die DE die EE aufruft.  
  
 [Schlüsselausdruck Evaluator\-Schnittstellen](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Beschreibt die wichtigen Schnittstellen erforderlich, wenn eine EE, zusammen mit den Auswertungskontext zu schreiben.  
  
## Siehe auch  
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)   
 [Ändern des Werts von einer lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md)