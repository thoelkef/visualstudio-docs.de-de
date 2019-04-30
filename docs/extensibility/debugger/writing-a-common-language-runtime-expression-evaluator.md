---
title: Schreiben eine Common Language Runtime-Ausdrucksauswertung | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c7ec2b6313ee27fc46c778f8b19e104b169273
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421469"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Schreiben Sie eine common Language Runtime-ausdrucksauswertung
> [!IMPORTANT]
> In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Die ausdrucksauswertung (EE) ist der Teil einer Debug-Engine (DE), die behandelt die Syntax und Semantik der Programmiersprache, die der gerade gedebuggten Code erstellt. Ausdrücke müssen innerhalb des Kontexts einer Programmiersprache ausgewertet werden. In einigen Sprachen können beispielsweise der Ausdruck "A + B" bedeutet "die Summe von A und b." In anderen Sprachen kann der gleiche Ausdruck "A oder b" bedeuten. Daher muss ein separates EE für jede Programmiersprache geschrieben werden, die zu debuggende Objektcode in Visual Studio-IDE generiert.

 Einige Aspekte der Visual Studio-Paket debuggen, müssen den Code im Kontext der Programmiersprache interpretiert. Z. B. wenn die Ausführung angehalten wird an einem Haltepunkt any-Ausdrücke, die in der Benutzer eingegeben hat eine **Watch** Fenster ausgewertet und angezeigt werden muss. Der Benutzer kann den Wert einer lokalen Variablen ändern, durch Eingabe eines Ausdrucks in einer **Watch** Fenster oder in der **direkt** Fenster.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Common Language Runtime und Ausdruck Auswertung](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) erklärt wird, wenn Sie in der Visual Studio-IDE, schreiben eine Auswertung von Ausdrücken innerhalb des Kontexts der proprietäre Sprache kann EE proprietäre Programmiersprache integrieren ermöglicht Ihnen, eine Microsoft intermediate Language (MSIL) kompiliert werden, ohne das Schreiben einer Debug-Engine.

 [Architektur der ausdrucksauswertung](../../extensibility/debugger/expression-evaluator-architecture.md) wird erläutert, wie die erforderlichen EE-Schnittstellen implementieren, und rufen Sie die common Language Runtime-Symbol-Dienstanbieter (SP) und den Binder-Schnittstellen.

 [Registrieren eine ausdrucksauswertung](../../extensibility/debugger/registering-an-expression-evaluator.md) berücksichtigt, dass die EE selbst als eine Klassenfactory mit der common Language Runtime und die Visual Studio-Laufzeitumgebungen registrieren muss.

 [Implementieren eine ausdrucksauswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md) wird beschrieben, wie der Prozess der Auswertung eines Ausdrucks für die Debug-Engine (DE), die Symbol-Dienstanbieter (SP), das binderobjekt und die ausdrucksauswertung (EE) enthält.

 [Anzeigen von "lokal"](../../extensibility/debugger/displaying-locals.md) wird beschrieben, wie, wenn die Ausführung angehalten wird, das debugpaket die DE zum Abrufen einer Liste von lokalen Variablen und Argumenten aufruft.

 [Auswerten ein überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md) dokumentiert, wie der Visual Studio-Paket Debuggen die DE zum Bestimmen des aktuellen Werts des jeder Ausdruck in der Liste sehen Sie sich aufruft.

 [Ändern Sie den Wert einer lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md) wird erklärt, dass in den Wert eines lokalen Elements ändern, jede Zeile des Fensters "lokal" ein zugeordnetes Objekt verfügt, die die Namen, Typ und aktuellen Wert eines lokalen Elements bereitstellt.

 [Implementieren von typschnellansichten und benutzerdefinierten Viewern](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) erklärt, welche Schnittstelle muss von der Komponente zur Unterstützung von typschnellansichten und benutzerdefinierten Viewern implementiert werden.

## <a name="see-also"></a>Siehe auch
 [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)