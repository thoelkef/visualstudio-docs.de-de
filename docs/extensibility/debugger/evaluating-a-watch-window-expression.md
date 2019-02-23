---
title: Auswerten eines Überwachungsfensterausdrucks | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10cd8b5e302809147f8f6e48210ca513534ce37e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695166"
---
# <a name="evaluate-a-watch-window-expression"></a>Auswerten eines überwachungsfensterausdrucks
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn die Ausführung angehalten wird, ruft Visual Studio die Debug-Engine (DE), um zu bestimmen, den aktuellen Wert der einzelnen Ausdrücke in der Liste sehen Sie sich an. Die DE wertet jeden Ausdruck, der mit einer ausdrucksauswertung (EE) und Visual Studio zeigt an, dessen Wert in der **Watch** Fenster.

 Es folgt einen Überblick darüber, wie ein Liste Überwachungsausdruck ausgewertet wird:

1.  Visual Studio ruft die DE [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) einen Ausdruckskontext abzurufen, die zum Auswerten von Ausdrücken verwendet werden können.

2.  Für jeden Ausdruck in der Liste sehen Sie sich, Visual Studio ruft [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) den Text des Ausdrucks in einen analysierten Ausdruck zu konvertieren.

3.  `IDebugExpressionContext2::ParseText` Aufrufe [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) die eigentliche Arbeit der Analyse von Text und erstellen Sie eine [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Objekt.

4.  `IDebugExpressionContext2::ParseText` erstellt eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt und speichert die `IDebugParsedExpression` -Objekts hinein. Diese ich`DebugExpression2` Objekt wird dann zurückgegeben, in Visual Studio.

5.  Visual Studio-Aufrufe [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) zum Auswerten des analysierten Ausdrucks.

6.  `IDebugExpression2::EvaluateSync` übergibt den Aufruf von [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) die eigentliche Auswertung und erzeugt eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das in Visual Studio zurückgegeben wird.

7.  Visual Studio-Aufrufe [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) um den Wert des Ausdrucks zu erhalten, die in der Liste sehen Sie sich dann angezeigt werden.

## <a name="parse-then-evaluate"></a>Analysieren und Auswerten
 Da beim Analysieren eines komplexen Ausdrucks viel länger als das Auswerten von es in Anspruch nehmen kann, wird der Prozess der Auswertung eines Ausdrucks in zwei Schritte unterteilt: (1) Analyse der Ausdruck "und" 2 ") auszuwerten den analysierten Ausdruck. Auf diese Weise kann Auswertung viele Male vorkommen, aber der Ausdruck muss nur einmal analysiert werden. Die analysierte intermediären Ausdrucks wird zurückgegeben, aus der EE in ein [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) -Objekt, das wiederum gekapselt und von der DE als zurückgegeben wird ein [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt. Die `IDebugExpression` Objekt verzögert alle Auswertung der `IDebugParsedExpression` Objekt.

> [!NOTE]
>  Es ist nicht notwendig, für eine EE dieser zweistufige Prozess befolgen, obwohl Visual Studio Dies setzt voraus. die EE analysieren und Auswerten von in der gleichen Schritt kann bei [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) aufgerufen wird (Dies ist die MyCEE, z. B. Funktionsweise des Beispiels). Wenn Ihre Sprache komplexe Ausdrücke bilden kann, empfiehlt es sich, den Schritt der Analyse von der bewertungsschritt zu trennen. Dies kann die Leistung in Visual Studio-Debugger verbessern, wenn viele Ausdrücke zu beobachten sind angezeigt werden.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Beispielimplementierung der ausdrucksauswertung](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) im MyCEE-Beispiel verwendet, um den Prozess der Auswertung des Ausdrucks zu durchlaufen.

 [Auswerten eines Überwachungsausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md) wird erläutert, was geschieht, nachdem eine Analyse der Ausdruck erfolgreich.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md) übergibt die Argumente, die übergeben werden, wenn die Debug-Engine (DE) die ausdrucksauswertung (EE) aufruft.

## <a name="see-also"></a>Siehe auch
 [Schreiben Sie eine CLR-ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)