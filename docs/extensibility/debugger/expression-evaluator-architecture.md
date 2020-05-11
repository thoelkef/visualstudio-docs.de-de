---
title: Expression Evaluator Architektur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738698"
---
# <a name="expression-evaluator-architecture"></a>Expression-Evaluator-Architektur
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Wenn Sie eine proprietäre Sprache in das Visual Studio-Debugpaket integrieren, müssen Sie die Schnittstellen für den erforderlichen Ausdrucksevaluator (EE) einrichten und die Common Language Run-Time Symbol Provider (SP) und Binderschnittstellen aufrufen. Die SP- und Binderobjekte sind zusammen mit der aktuellen Ausführungsadresse der Kontext, in dem Ausdrücke ausgewertet werden. Die Informationen, die diese Schnittstellen erzeugen und nutzen, stellen die wichtigsten Konzepte in der Architektur eines EE dar.

## <a name="overview"></a>Übersicht

### <a name="parse-the-expression"></a>Analysieren des Ausdrucks
 Wenn Sie ein Programm debuggen, werden Ausdrücke aus einer Reihe von Gründen ausgewertet, aber immer dann, wenn das zu debuggende Programm an einem Haltepunkt angehalten wurde (entweder ein vom Benutzer platzierter Haltepunkt oder einer, der durch eine Ausnahme verursacht wurde). In diesem Moment ruft Visual Studio einen Stackframe, wie er durch die [IDebugStackFrame2-Schnittstelle](../../extensibility/debugger/reference/idebugstackframe2.md) dargestellt wird, vom Debugmodul (DE) ab. Visual Studio ruft dann [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um die [IDebugExpressionContext2-Schnittstelle](../../extensibility/debugger/reference/idebugexpressioncontext2.md) abruft. Diese Schnittstelle stellt einen Kontext dar, in dem Ausdrücke ausgewertet werden können. [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) ist der Einstiegspunkt für den Auswertungsprozess. Bis zu diesem Zeitpunkt werden alle Schnittstellen von der DE implementiert.

 Wenn `IDebugExpressionContext2::ParseText` aufgerufen wird, instanziiert die DE die EE, die der Sprache der Quelldatei zugeordnet ist, in der der Haltepunkt aufgetreten ist (die DE instanziiert an dieser Stelle auch das SH). Der EE wird durch die [IDebugExpressionEvaluator-Schnittstelle](../../extensibility/debugger/reference/idebugexpressionevaluator.md) dargestellt. Die DE ruft dann [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) auf, um den Ausdruck (in Textform) in einen analysierten Ausdruck zu konvertieren, der zur Auswertung bereit ist. Dieser analysierte Ausdruck wird durch die [IDebugParsedExpression-Schnittstelle](../../extensibility/debugger/reference/idebugparsedexpression.md) dargestellt. Der Ausdruck wird in der Regel analysiert und zu diesem Zeitpunkt nicht ausgewertet.

 Die DE erstellt ein Objekt, das die [IDebugExpression2-Schnittstelle](../../extensibility/debugger/reference/idebugexpression2.md) implementiert, `IDebugParsedExpression` das Objekt in das `IDebugExpression2` Objekt einfügt und das `IDebugExpression2` Objekt von `IDebugExpressionContext2::ParseText`zurückgibt.

### <a name="evaluate-the-expression"></a>Auswerten des Ausdrucks
 Visual Studio ruft entweder [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um den analysierten Ausdruck auszuwerten. Beide Methoden rufen [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) auf (`IDebugExpression2::EvaluateSync` ruft `IDebugExpression2::EvaluateAsync` die Methode sofort auf, während die Methode über einen Hintergrundthread aufruft), um den analysierten Ausdruck auszuwerten und eine [IDebugProperty2-Schnittstelle](../../extensibility/debugger/reference/idebugproperty2.md) zurückzugeben, die den Wert und Typ des analysierten Ausdrucks darstellt. `IDebugParsedExpression::EvaluateSync`verwendet das angegebene SH, die Adresse und den Bindemittel, um `IDebugProperty2` den analysierten Ausdruck in einen tatsächlichen Wert zu konvertieren, der durch die Schnittstelle dargestellt wird.

### <a name="for-example"></a>Beispiel:
 Nachdem ein Haltepunkt in einem laufenden Programm erreicht wurde, wählt der Benutzer eine Variable im **QuickWatch-Dialogfeld** anzeigen. In diesem Dialogfeld werden der Name, der Wert und der Typ der Variablen angezeigt. Der Benutzer kann den Wert in der Regel ändern.

 Wenn das **QuickWatch-Dialogfeld** angezeigt wird, wird der Name der untersuchten Variablen als Text an [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)gesendet. Dadurch wird ein [IDebugExpression2-Objekt](../../extensibility/debugger/reference/idebugexpression2.md) zurückgegeben, das den analysierten Ausdruck, in diesem Fall die Variable, darstellt. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) wird dann aufgerufen, um ein `IDebugProperty2` Objekt zu erzeugen, das den Wert und Typ der Variablen sowie ihren Namen darstellt. Es sind diese Informationen, die angezeigt werden.

 Wenn der Benutzer den Wert der Variablen ändert, wird [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) mit dem neuen Wert aufgerufen, wodurch der Wert der Variablen im Arbeitsspeicher geändert wird, sodass sie verwendet wird, wenn das Programm wieder ausgeführt wird.

 Weitere Informationen zu diesem Prozess zum Anzeigen der Werte von Variablen finden Sie unter Anzeigen von [Locals.](../../extensibility/debugger/displaying-locals.md) Weitere Informationen dazu, wie der Wert einer Variablen geändert wird, finden Sie unter [Ändern des Werts eines lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md) Gebiets.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Evaluierungskontext](../../extensibility/debugger/evaluation-context.md) Stellt die Argumente bereit, die übergeben werden, wenn die DE den EE aufruft.

 [Schlüsselausdrucksauswertungsschnittstellen](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Beschreibt die wichtigsten Schnittstellen, die beim Schreiben eines EE erforderlich sind, zusammen mit dem Evaluierungskontext.

## <a name="see-also"></a>Weitere Informationen
- [Schreiben eines CLR-Ausdrucksevaluators](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Anzeigen von Einheimischen](../../extensibility/debugger/displaying-locals.md)
- [Ändern des Werts eines lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md)
