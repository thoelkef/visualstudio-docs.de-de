---
title: Schreiben eine Common Language Runtime-Ausdrucksauswertung | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3ff2189bd80d2c5bbbc5253763e2ba07ef917d19
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135843"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Schreiben Sie eine Common Language Runtime-Ausdrucksauswertung
> [!IMPORTANT]
>  In Visual Studio 2015 wird diese Möglichkeit zum Implementieren von ausdruckauswertung veraltet. Informationen zu CLR-ausdrucksauswertungen implementieren, finden Sie unter [CLR-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die ausdrucksauswertung (EE) ist der Teil einer Debugging-Modul (DE), die behandelt die Syntax und Semantik von der Programmiersprache ab, die den Code, der debuggt wird erstellt. Ausdrücke müssen innerhalb des Kontexts einer Programmiersprache Ihrer Wahl ausgewertet werden. In einigen Sprachen können beispielsweise der Ausdruck "A + B" bedeutet "die Summe von A und b." In anderen Sprachen kann die gleiche Ausdruck "A oder b" bedeuten. Daher muss ein separates EE für jede Programmiersprache geschrieben werden, die zu debuggende Objektcode in der Visual Studio-IDE generiert.  
  
 Einige Aspekte von Visual Studio-debugpaket müssen den Code im Kontext der Programmiersprache interpretiert werden. Z. B. wenn die Ausführung hält an einem Haltepunkt, alle Ausdrücke, die der Benutzer, in eingegeben hat einem **Überwachen** Fenster ausgewertet und angezeigt werden muss. Darüber hinaus kann der Benutzer den Wert einer lokalen Variablen ändern, durch Eingabe eines Ausdrucks in einer **Überwachen** Fenster oder in der **Direktfenster** Fenster.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Common Language Runtime und Ausdrucksauswertung](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Zeigt an, dass beim Integrieren von proprietären Programmiersprache, in der Visual Studio-IDE Schreiben einer EE Auswerten von Ausdrücken innerhalb des Kontexts der proprietäre Sprache kann Microsoft intermediate Language (MSIL) kompiliert Sie können ohne das Schreiben von Debugging-Modul.  
  
 [Architektur der Ausdrucksauswertung](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Erläutert, wie die erforderlichen EE Schnittstellen implementieren, und rufen Sie die common Language Runtime Symbol Dienstanbieter (SP) und den Binder-Schnittstellen.  
  
 [Registrieren einer Ausdrucksauswertung](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Anmerkungen dieser, dass die EE als Klassenfactory mit der common Language Runtime und die Laufzeitumgebungen für Visual Studio registriert werden muss.  
  
 [Implementieren einer Ausdrucksauswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Beschreibt, wie der Prozess der Auswertung eines Ausdrucks die Debugging-Modul (DE), den Symbol-Anbieter (SP), das binderobjekt und die ausdrucksauswertung (EE) umfasst.  
  
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)  
 Beschreibt, wie, wenn die Ausführung angehalten wird, das debugpaket DE zum Abrufen einer Liste von lokalen Variablen und Argumenten aufruft.  
  
 [Auswerten eines Überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Beschreibt, wie das debugpaket Visual Studio die DE, um zu bestimmen, den aktuellen Wert der jeder Ausdruck in der Überwachungsliste aufruft.  
  
 [Ändern des Werts eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Erläutert, dass in den Wert eines lokalen ändern, jede Zeile des Fensters "lokal" ein zugeordnetes Objekt aufweist, das Name, der Typ und der aktuelle Wert von einem lokalen bereitstellt.  
  
 [Implementieren von Typschnellansichten und benutzerdefinierten Viewern](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Erläutert, welche Schnittstelle muss von der Komponente zur Unterstützung von Typ-Schnellansichten und benutzerdefinierten Viewer implementiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)