---
title: Auswerten eines Überwachungsfensterausdrucks | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738842"
---
# <a name="evaluate-a-watch-window-expression"></a>Auswerten eines Überwachungsfensterausdrucks
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn die Ausführung angehalten wird, ruft Visual Studio das Debugmodul (DE) auf, um den aktuellen Wert jedes Ausdrucks in seiner Überwachungsliste zu bestimmen. Die DE wertet jeden Ausdruck mit einem Ausdrucksevaluator (EE) aus, und Visual Studio zeigt seinen Wert im **Überwachungsfenster** an.

 Im Folgenden finden Sie eine Übersicht darüber, wie ein Watchlist-Ausdruck ausgewertet wird:

1. Visual Studio ruft den [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) der DE auf, um einen Ausdruckskontext abzuruft, der zum Auswerten von Ausdrücken verwendet werden kann.

2. Für jeden Ausdruck in der Überwachungsliste ruft Visual Studio [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) auf, um den Ausdruckstext in einen analysierten Ausdruck zu konvertieren.

3. `IDebugExpressionContext2::ParseText`ruft [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) auf, um die eigentliche Arbeit zum Analysieren des Textes zu erledigen und ein [IDebugParsedExpression-Objekt](../../extensibility/debugger/reference/idebugparsedexpression.md) zu erstellen.

4. `IDebugExpressionContext2::ParseText`erstellt ein [IDebugExpression2-Objekt](../../extensibility/debugger/reference/idebugexpression2.md) und legt das `IDebugParsedExpression` Objekt darin ab. Dieses`DebugExpression2` I-Objekt wird dann an Visual Studio zurückgegeben.

5. Visual Studio ruft [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) auf, um den analysierten Ausdruck auszuwerten.

6. `IDebugExpression2::EvaluateSync`übergibt den Aufruf an [EvaluateSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) um die eigentliche Auswertung durchzuführen und ein [IDebugProperty2-Objekt](../../extensibility/debugger/reference/idebugproperty2.md) zu erstellen, das an Visual Studio zurückgegeben wird.

7. Visual Studio ruft [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) auf, um den Wert des Ausdrucks abzuerhalten, der dann in der Überwachungsliste angezeigt wird.

## <a name="parse-then-evaluate"></a>Parse bewerten dann
 Da das Analysieren eines komplexen Ausdrucks viel länger dauern kann als die Auswertung, wird der Prozess der Auswertung eines Ausdrucks in zwei Schritte unterteilt: 1) analysieren Sie den Ausdruck und 2) den analysierten Ausdruck aus. Auf diese Weise kann die Auswertung oft vorkommen, aber der Ausdruck muss nur einmal analysiert werden. Der analysierte Zwischenausdruck wird von der EE in einem [IDebugParsedExpression-Objekt](../../extensibility/debugger/reference/idebugparsedexpression.md) zurückgegeben, das wiederum gekapselt und von der DE als [IDebugExpression2-Objekt](../../extensibility/debugger/reference/idebugexpression2.md) zurückgegeben wird. Das `IDebugExpression` Objekt verschiebt die `IDebugParsedExpression` gesamte Auswertung auf das Objekt.

> [!NOTE]
> Es ist nicht erforderlich, dass ein EE diesem zweistufigen Prozess folgt, auch wenn Visual Studio davon ausgeht. Der EE kann im selben Schritt analysiert und ausgewertet werden, wenn [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) aufgerufen wird (z. B. funktioniert das MyCEE-Beispiel). Wenn Ihre Sprache komplexe Ausdrücke bilden kann, können Sie den Analyseschritt vom Auswertungsschritt trennen. Dies kann die Leistung im Visual Studio-Debugger erhöhen, wenn viele Überwachungsausdrücke angezeigt werden.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Beispielimplementierung der Ausdrucksauswertung](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Verwendet das MyCEE-Beispiel, um den Prozess der Ausdrucksauswertung zu durchlaufen.

 [Auswerten eines Uhrausdrucks](../../extensibility/debugger/evaluating-a-watch-expression.md) Erläutert, was nach einer erfolgreichen Ausdrucksanalyse geschieht.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md) Stellt die Argumente bereit, die übergeben werden, wenn das Debugmodul (DE) den Ausdrucksevaluator (EE) aufruft.

## <a name="see-also"></a>Weitere Informationen
 [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
