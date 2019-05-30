---
title: Architektur der Ausdrucksauswertung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 42c52e3d6b71b58668a05434e9ca8f65eb3e7832
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353766"
---
# <a name="expression-evaluator-architecture"></a>Architektur der ausdrucksauswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Die Integration in das Visual Studio-Paket Debuggen bedeutet, Sie dass von eine proprietäre Sprache muss richten Sie die erforderlichen Expression Evaluator (EE)-Schnittstellen und rufen Sie die common Language Run-Time-Symbol-Dienstanbieter (SP) und den Binder-Schnittstellen. Die SP und Binder-Objekte zusammen mit der aktuellen Adresse für die Ausführung stehen für Kontext in dem Ausdrücke ausgewertet werden. Die Informationen, die diese Schnittstellen zu erzeugen und nutzen, stellt die wichtigsten Konzepte in der Architektur eine EE dar.

## <a name="overview"></a>Übersicht

### <a name="parse-the-expression"></a>Analysieren des Ausdrucks
 Wenn Sie ein Programm debuggen, werden Ausdrücke ausgewertet, für eine Reihe von Gründen aber immer wenn die zu debuggende Programm wird an einem Haltepunkt (entweder ein Haltepunkt eingefügt, die vom Benutzer oder eine durch eine Ausnahme verursacht hat) wurde beendet. Es ist zu diesem Zeitpunkt an, wenn Visual Studio einen Stapelrahmen erhält, dargestellt durch die [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) Schnittstelle, von der Debug-Engine (DE). Visual Studio ruft dann [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zum Abrufen der [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Schnittstelle. Diese Schnittstelle stellt einen Kontext, in dem Ausdrücke ausgewertet werden können; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ist der Einstiegspunkt für den Prozess der Evaluierung. Bis zu diesem Punkt werden alle Schnittstellen durch die DE implementiert.

 Wenn `IDebugExpressionContext2::ParseText` wird aufgerufen, die DE instanziiert die EE verknüpft ist, mit der Sprache der Quelldatei, in der Haltepunkt aufgetreten ist (die DE instanziiert außerdem die SH an diesem Punkt). Die EE wird dargestellt, durch die [IDebugExpressionEvaluator](../../extensibility/debugger/reference/idebugexpressionevaluator.md) Schnittstelle. Ruft die DE dann [analysieren](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) zum Konvertieren des Ausdrucks (in Textform) in einer analysierten Ausdruck bereit, für die Evaluierung. Durch diese analysierten Ausdruck dargestellt wird die [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) Schnittstelle. Der Ausdruck wird in der Regel analysiert und an diesem Punkt nicht ausgewertet.

 Die DE erstellt ein Objekt, das implementiert die [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle, setzt der `IDebugParsedExpression` -Objekt in der `IDebugExpression2` -Objekt und gibt die `IDebugExpression2` -Objekt aus `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>Wertet den Ausdruck
 Visual Studio ruft entweder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) zum Auswerten des analysierten Ausdrucks. Beide Methoden rufen [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (`IDebugExpression2::EvaluateSync` Ruft die Methode sofort beendet, während er sich `IDebugExpression2::EvaluateAsync` Ruft die Methode über einen Hintergrundthread) zu den analysierten Ausdruck ausgewertet und zurückgegeben ein [ IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle, die den Wert und Typ des analysierten Ausdrucks darstellt. `IDebugParsedExpression::EvaluateSync` verwendet die angegebene SH, Adresse und den Binder, konvertieren den analysierten Ausdruck in einen tatsächlichen Wert, der durch dargestellt die `IDebugProperty2` Schnittstelle.

### <a name="for-example"></a>Beispiel:
 Nach dem in ein ausgeführtes Programm ein Haltepunkt erreicht wird, wählt des Benutzers an eine Variable in der **Schnellüberwachung** Dialogfeld. Dieses Dialogfeld zeigt den Namen der Variablen, dessen Wert und den Typ an. Der Benutzer kann den Wert in der Regel ändern.

 Wenn die **Schnellüberwachung** Dialogfeld wird angezeigt, der Namen der Variablen, die überprüft wird, wird als Text, der gesendet [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Dies gibt eine [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) Objekt, das in diesem Fall den analysierten Ausdruck darstellt, die Variable. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wird aufgerufen, um das Erstellen einer `IDebugProperty2` Objekt, das den Wert der Variable und Typ sowie den Namen darstellt. Es ist diese Informationen, die angezeigt wird.

 Wenn der Benutzer den Wert der Variablen, ändert [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) wird aufgerufen, mit dem neuen Wert, der den Wert der Variablen im Speicher ändert, damit es verwendet wird, wenn das Programm fortgesetzt wird ausgeführt.

 Finden Sie unter [anzeigen "lokal"](../../extensibility/debugger/displaying-locals.md) für Weitere Informationen zu diesem Prozess die Werte der Variablen anzuzeigen. Finden Sie unter [Ändern des Werts eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md) Weitere Einzelheiten, wie der Wert einer Variablen geändert wird.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md) übergibt die Argumente, die übergeben werden, wenn die DE die EE aufruft.

 [Wichtige Schnittstellen für die ausdrucksauswertung Ausdruck](../../extensibility/debugger/key-expression-evaluator-interfaces.md) beschreibt die wichtigen Schnittstellen erforderlich, wenn ein EE, zusammen mit den Auswertungskontext zu schreiben.

## <a name="see-also"></a>Siehe auch
- [Schreiben Sie eine CLR-ausdrucksauswertung](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)
- [Ändern des Werts eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md)