---
title: Schreiben eine Common Language Runtime-Ausdrucksauswertung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2db9290f35c2b12469ecf96633967c2979b370e5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956579"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Schreiben einer Ausdrucksauswertung für die Common Language Runtime
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die ausdrucksauswertung (EE) ist der Teil einer Debug-Engine (DE), die behandelt die Syntax und Semantik der Programmiersprache, die der gerade gedebuggten Code erstellt. Ausdrücke müssen innerhalb des Kontexts einer Programmiersprache ausgewertet werden. In einigen Sprachen können beispielsweise der Ausdruck "A + B" bedeutet "die Summe von A und b." In anderen Sprachen kann der gleiche Ausdruck "A oder b" bedeuten. Daher muss ein separates EE für jede Programmiersprache geschrieben werden, die zu debuggende Objektcode in Visual Studio-IDE generiert.  
  
 Einige Aspekte der Visual Studio-Paket debuggen, müssen den Code im Kontext der Programmiersprache interpretiert. Z. B. wenn die Ausführung angehalten wird an einem Haltepunkt any-Ausdrücke, die in der Benutzer eingegeben hat eine **Watch** Fenster ausgewertet und angezeigt werden muss. Darüber hinaus kann der Benutzer den Wert einer lokalen Variablen ändern, durch Eingabe eines Ausdrucks in einer **Watch** Fenster oder in der **direkt** Fenster.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Common Language Runtime und Ausdrucksauswertung](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Erklärt, dass beim Integrieren von proprietären Programmiersprache in Visual Studio-IDE, schreiben eine EE Auswerten von Ausdrücken innerhalb des Kontexts der proprietäre Sprache kann in einer Microsoft intermediate Language (MSIL) kompiliert wird, Sie können ohne das Schreiben einer Debug-Engine.  
  
 [Architektur der Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Erläutert, wie die erforderlichen EE-Schnittstellen zu implementieren, und rufen Sie die common Language Runtime-Symbol-Dienstanbieter (SP) und den Binder-Schnittstellen.  
  
 [Registrieren einer Ausdrucksauswertung](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Anmerkungen dieser, dass die EE selbst als eine Klassenfactory mit der common Language Runtime und die Visual Studio-Laufzeitumgebungen registrieren muss.  
  
 [Implementieren einer Ausdrucksauswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Beschreibt, wie der Prozess der Auswertung eines Ausdrucks für die Debug-Engine (DE), die Symbol-Dienstanbieter (SP), das binderobjekt und die ausdrucksauswertung (EE) enthält.  
  
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)  
 Beschreibt, wie, wenn die Ausführung angehalten wird, das debugpaket die DE zum Abrufen einer Liste von lokalen Variablen und Argumenten aufruft.  
  
 [Auswerten eines Überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Beschreibt, wie der Visual Studio-Paket Debuggen die DE zum Bestimmen des aktuellen Werts des jeder Ausdruck in der Liste sehen Sie sich aufruft.  
  
 [Ändern des Werts eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Erklärt, dass in den Wert eines lokalen Elements ändern, jede Zeile des Fensters "lokal" ein zugeordnetes Objekt verfügt, das die Namen, Typ und aktuellen Wert eines lokalen Elements bereitstellt.  
  
 [Implementieren von Typschnellansichten und benutzerdefinierten Viewern](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Erklärt, welche Schnittstelle muss von der Komponente zur Unterstützung von typschnellansichten und benutzerdefinierten Viewern implementiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
