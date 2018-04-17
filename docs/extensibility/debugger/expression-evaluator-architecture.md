---
title: Expression Evaluator-Architektur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fdcdfef67531af40027a2dfe8c731fe9ba5128f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="expression-evaluator-architecture"></a>Expression Evaluator-Architektur
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Integrieren von eine proprietäre Sprache in Visual Studio-debugpaket bedeutet, dass erforderlichen Expression Evaluator (EE) Schnittstellen implementieren und aufrufen, die common Language Run-Time-Symbol Dienstanbieter (SP) und den Binder-Schnittstellen. Die SP und Binder-Objekte zusammen mit der aktuellen Adresse für die Ausführung sind den Kontext, in dem Ausdrücke ausgewertet werden. Die Informationen, die diese Schnittstellen zu erzeugen und nutzen stellt die grundlegenden Konzepte in der Architektur des ein EE dar.  
  
## <a name="overview"></a>Übersicht  
  
### <a name="parsing-the-expression"></a>Analysieren des Ausdrucks  
 Wenn Sie ein Programm debuggen, werden Ausdrücke ausgewertet, für eine Reihe von Gründen jedoch immer wenn die Anwendung gedebuggt wird an einem Haltepunkt (entweder ein Haltepunkt eingefügt, die vom Benutzer oder eine durch eine Ausnahme verursacht hat) beendet wurde. Es ist zu diesem Zeitpunkt an, wenn Visual Studio einen Stapelrahmen erhält, dargestellt durch die [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle, von der Debugging-Modul (DE). Visual Studio ruft dann [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zum Abrufen der [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Diese Schnittstelle stellt einen Kontext, in dem Ausdrücke ausgewertet werden können; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ist der Einstiegspunkt zum Bewertungsprozess. Bis zu diesem Punkt sind alle Schnittstellen vom DE implementiert.  
  
 Wenn `IDebugExpressionContext2::ParseText` wird aufgerufen, die DE instanziiert die EE verknüpft sind, mit der Sprache der Quelldatei, in der Breakpoint aufgetreten ist (die DE auch instanziiert die SH zu diesem Zeitpunkt). Die EE wird dargestellt, indem die [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) Schnittstelle. Ruft die DE dann [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Konvertieren des Ausdrucks (in Textform) in einem analysierten Ausdrucks bereit, für die Evaluierung. Diese analysierten Ausdrucks wird dargestellt, von der [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle. Beachten Sie, dass der Ausdruck ist in der Regel analysiert und zu diesem Zeitpunkt nicht ausgewertet.  
  
 DE erstellt ein Objekt, implementiert die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle, setzt der `IDebugParsedExpression` -Objekt in der `IDebugExpression2` Objekt und gibt die `IDebugExpression2` -Objekt aus `IDebugExpressionContext2::ParseText`.  
  
### <a name="evaluating-the-expression"></a>Auswertung des Ausdrucks  
 Visual Studio aufgerufen werden, entweder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) zum Auswerten des analysierten Ausdrucks. Beide Methoden aufrufen [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` Ruft die Methode sofort beendet, während er sich `IDebugExpression2::EvaluateAsync` Ruft die Methode über einen Hintergrundthread) um die analysierten Ausdrucks auszuwerten und zurückzugeben eine [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die den Wert und Typ des analysierten Ausdrucks darstellt. `IDebugParsedExpression::EvaluateSync` verwendet die angegebene SH, Adresse und den Binder analysierten Ausdrucks in einen tatsächlichen Wert, dargestellt durch Konvertieren der `IDebugProperty2` Schnittstelle.  
  
### <a name="for-example"></a>Zum Beispiel  
 Nachdem in einem ausgeführten Programm ein Haltepunkt erreicht wird, wählt der Benutzer an eine Variable in der **Schnellüberwachung** (Dialogfeld). Dieses Dialogfeld zeigt den Namen der Variablen, seinen Wert und dessen Typ auf. Der Benutzer kann den Wert in der Regel ändern.  
  
 Wenn die **Schnellüberwachung** Dialogfeld wird angezeigt, wird der Name der Variablen, der überprüft wird als Text gesendet [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Dies gibt eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt, das in diesem Fall den analysierten Ausdruck darstellt, die Variable. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wird aufgerufen, um erzeugen ein `IDebugProperty2` Objekt, das den Wert der Variablen und Typ sowie den Namen darstellt. Es ist diese Informationen, die angezeigt wird.  
  
 Wenn der Benutzer den Wert der Variablen, ändert [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) aufgerufen wird und der neue Wert, der den Wert der Variablen im Speicher ändert, damit es verwendet wird, wenn das Programm fortgesetzt wird ausgeführt.  
  
 Finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md) detaillierte Informationen zu diesem Vorgang zum Anzeigen von die Werte von Variablen. Finden Sie unter [Wertänderung in einer lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md) für Weitere Informationen zu den wie der Wert einer Variablen geändert wird.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Auswertungskontext](../../extensibility/debugger/evaluation-context.md)  
 Stellt die Argumente, die übergeben werden, wenn die DE die EE aufruft.  
  
 [Wichtige Schnittstellen für die Ausdrucksauswertung](../../extensibility/debugger/key-expression-evaluator-interfaces.md)  
 Beschreibt die entscheidenden Schnittstellen erforderlich, wenn Sie eine EE, zusammen mit den Auswertungskontext zu schreiben.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben Sie eine CLR-Ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Anzeigen von "lokal"](../../extensibility/debugger/displaying-locals.md)   
 [Ändern des Werts eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md)