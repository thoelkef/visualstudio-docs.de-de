---
title: Erstellen eines Common Language Runtime Expression Evaluator | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712325"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Schreiben eines Common Language Runtime-Ausdrucksevaluators
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von Ausdrucksevaluatoren veraltet. Informationen zum Implementieren von CLR-Ausdrucksevaluatoren finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Beispiel für den Auswertungsbeispiel für managed expression evaluator](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Der Ausdrucksevaluator (EE) ist der Teil eines Debugmoduls (DE), das die Syntax und Semantik der Programmiersprache verarbeitet, die den zu debuggenden Code erzeugt hat. Ausdrücke müssen im Kontext einer Programmiersprache ausgewertet werden. In einigen Sprachen bedeutet der Ausdruck "A+B" beispielsweise "die Summe von A und B". In anderen Sprachen kann derselbe Ausdruck "A" oder "B" bedeuten. Daher muss für jede Programmiersprache, die Objektcode generiert, der in der Visual Studio-IDE gedebuggen werden soll, eine separate EE geschrieben werden.

 Einige Aspekte des Visual Studio-Debugpakets müssen den Code im Kontext der Programmiersprache interpretieren. Wenn die Ausführung z. B. an einem Haltepunkt angehalten wird, müssen alle Ausdrücke, die der Benutzer in ein **Überwachungsfenster** eingegeben hat, ausgewertet und angezeigt werden. Der Benutzer kann den Wert einer lokalen Variablen ändern, indem er einen Ausdruck in ein **Watch-Fenster** oder in das **Direktfenster** eingibt.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Common Language Runtime und Ausdrucksauswertung](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Erläutert, dass Sie beim Integrieren proprietärer Programmiersprache in die Visual Studio-IDE beim Schreiben eines EE, der Ausdrücke im Kontext der proprietären Sprache auswerten kann, das Kompilieren in eine Microsoft-Zwischensprache (MSIL) ermöglichen, ohne ein Debugmodul zu schreiben.

 [Expression-Evaluator-Architektur](../../extensibility/debugger/expression-evaluator-architecture.md) Erläutert, wie die erforderlichen EE-Schnittstellen implementiert und der Common Language Runtime Symbol Provider (SP) und Binderschnittstellen aufrufen.

 [Registrieren eines Ausdrucksevaluators](../../extensibility/debugger/registering-an-expression-evaluator.md) Stellt fest, dass sich der EE als Klassenfactory sowohl mit der Common Language Runtime- als auch mit Visual Studio-Laufzeitumgebungen registrieren muss.

 [Implementieren eines Ausdrucksevaluators](../../extensibility/debugger/implementing-an-expression-evaluator.md) Beschreibt, wie der Prozess der Auswertung eines Ausdrucks das Debugmodul (DE), den Symbolanbieter (SP), das Binderobjekt und den Ausdrucksevaluator (EE) umfasst.

 [Lokale anzeigen](../../extensibility/debugger/displaying-locals.md) Beschreibt, wie das Debugpaket beim Anhalten der Ausführung die DE aufruft, um eine Liste lokaler Variablen und Argumente abzusondern.

 [Auswerten eines Überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Dokumentiert, wie das Visual Studio-Debugpaket die DE aufruft, um den aktuellen Wert jedes Ausdrucks in seiner Überwachungsliste zu bestimmen.

 [Ändern des Werts eines lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md) Erläutert, dass beim Ändern des Werts eines lokalen Fensters für jede Zeile des Locals-Fensters ein zugeordnetes Objekt mit dem Namen, dem Typ und dem aktuellen Wert eines lokalen Objekts steht.

 [Implementieren von Typvisualisierern und benutzerdefinierten Viewern](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Erläutert, welche Schnittstelle von welcher Komponente implementiert werden muss, um Typvisualisierer und benutzerdefinierte Viewer zu unterstützen.

## <a name="see-also"></a>Weitere Informationen
 [Erweiterbarkeit des Visual Studio-Debuggers](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
