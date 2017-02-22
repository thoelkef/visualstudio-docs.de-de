---
title: "Evaluieren einen &#220;berwachungsausdruck-Fenster | Microsoft Docs"
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
  - "Ansehen von Ausdrücken"
  - "Überwachungsfenster, Ausdrücke"
  - "Auswertung von Ausdrücken, Ausdrücken des Debuggerfensters überwachen"
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Evaluieren einen &#220;berwachungsausdruck-Fenster
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Wenn die Ausführung angehalten wird, ruft Visual Studio Debugging\-Modul \(DE\), um den aktuellen Wert der einzelnen Ausdrücke aus der Watchlist zu bestimmen. Die DE wertet jeden Ausdruck, der mithilfe der ausdrucksauswertung \(EE\) und Visual Studio zeigt den Wert in der **Überwachen** Fenster.  
  
 Hier ist ein Überblick darüber, wie ein Liste Überwachungsausdruck ausgewertet wird:  
  
1.  Visual Studio aufgerufen werden, die DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) einem Ausdruckskontext abgerufen, die zum Auswerten von Ausdrücken verwendet werden können.  
  
2.  Für jeden Ausdruck in der Überwachungsliste, ruft Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) den Text des Ausdrucks in einer analysierten Ausdruck konvertiert.  
  
3.  `IDebugExpressionContext2::ParseText` Ruft [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) auf die eigentliche Arbeit zum Analysieren von Text und Erzeugen von einem [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.  
  
4.  `IDebugExpressionContext2::ParseText` erstellt ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) \-Objekt und speichert die `IDebugParsedExpression` in dieses Objekt. Diese ich`DebugExpression2` Objekt wird dann zu Visual Studio zurückgegeben.  
  
5.  Visual Studio Aufrufe [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Auswerten des analysierten Ausdrucks.  
  
6.  `IDebugExpression2::EvaluateSync` übergibt den Aufruf von [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) die tatsächliche Auswertung und erzeugt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) zurückgegebene Objekt in Visual Studio ist.  
  
7.  Visual Studio Aufrufe [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) um den Wert des Ausdrucks abzurufen, die in der Überwachungsliste angezeigt wird.  
  
## Analysieren und Auswerten  
 Da Analysieren eines komplexen Ausdrucks evaluieren viel länger dauern kann, ist der Prozess der Auswertung eines Ausdrucks sich in zwei Schritte unterteilt: \(1\) den Ausdruck analysiert, und \(2\) der analysierten Ausdruck auszuwerten. Auf diese Weise kann Auswertung oft durchgeführt, aber der Ausdruck muss nur einmal verarbeitet werden. Fortgeschrittene analysierten Ausdrucks wird zurückgegeben, die AA in ein [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) \-Objekt, das wiederum gekapselt und die DE als zurückgegebenes ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt. Das `IDebugExpression` Objekt verzögert alle Auswertung der `IDebugParsedExpression` Objekt.  
  
> [!NOTE]
>  Es ist nicht notwendig für eine EE dieser zweistufige Prozess zum einhalten, obwohl Visual Studio wird dabei davon ausgegangen. die EE analysieren und auswerten, die in demselben Schritt kann bei [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) aufgerufen wird \(Dies ist das Beispiel MyCEE, z. B. Funktionsweise\). Wenn Ihre Sprache komplexe Ausdrücke bilden kann, empfiehlt es sich, die den Analyse Schritt von der Auswertungsschritt getrennt. Dies kann die Leistung in Visual Studio\-Debugger verbessern, wenn viele Ausdrücke zu beobachten sind angezeigt wird.  
  
## In diesem Abschnitt  
 [Beispielimplementierung der Auswertung von Ausdrücken](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)  
 MyCEE Beispiel verwendet schrittweise durch den Prozess der Auswertung des Ausdrucks.  
  
 [Evaluieren einen Überwachungsausdruck](../../extensibility/debugger/evaluating-a-watch-expression.md)  
 Erläutert, was geschieht, nachdem ein Ausdruck erfolgreich analysiert.  
  
## Verwandte Abschnitte  
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md)  
 Stellt die Argumente übergeben werden, wenn das Debugging\-Modul \(DE\) der Auswertung eines Ausdrucks \(EE\) aufruft.  
  
## Siehe auch  
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)