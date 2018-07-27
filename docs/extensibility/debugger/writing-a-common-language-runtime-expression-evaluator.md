---
title: Schreiben eine Common Language Runtime-Ausdrucksauswertung | Microsoft-Dokumentation
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
ms.openlocfilehash: 9d93299702db0c56963eb8f404d05e8e67ab08b0
ms.sourcegitcommit: 8d38d5d2f2b75fc1563952c0d6de0fe43af12766
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39276818"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Schreiben Sie eine common Language Runtime-ausdrucksauswertung
> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen zum Implementieren von CLR-ausdrucksauswertungen finden Sie unter [CLR ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Auswertung (Beispiel) verwaltete Ausdruck](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die ausdrucksauswertung (EE) ist der Teil einer Debug-Engine (DE), die behandelt die Syntax und Semantik der Programmiersprache, die der gerade gedebuggten Code erstellt. Ausdrücke müssen innerhalb des Kontexts einer Programmiersprache ausgewertet werden. In einigen Sprachen können beispielsweise der Ausdruck "A + B" bedeutet "die Summe von A und b." In anderen Sprachen kann der gleiche Ausdruck "A oder b" bedeuten. Daher muss ein separates EE für jede Programmiersprache geschrieben werden, die zu debuggende Objektcode in Visual Studio-IDE generiert.  
  
 Einige Aspekte der Visual Studio-Paket debuggen, müssen den Code im Kontext der Programmiersprache interpretiert. Z. B. wenn die Ausführung angehalten wird an einem Haltepunkt any-Ausdrücke, die in der Benutzer eingegeben hat eine **Watch** Fenster ausgewertet und angezeigt werden muss. Der Benutzer kann den Wert einer lokalen Variablen ändern, durch Eingabe eines Ausdrucks in einer **Watch** Fenster oder in der **direkt** Fenster.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Common Language Runtime und Ausdruck-Evaluierung](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Erklärt, dass beim Integrieren von proprietären Programmiersprache in Visual Studio-IDE, schreiben eine EE Auswerten von Ausdrücken innerhalb des Kontexts der proprietäre Sprache kann in einer Microsoft intermediate Language (MSIL) kompiliert wird, Sie können ohne das Schreiben einer Debug-Engine.  
  
 [Architektur der ausdrucksauswertung](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Erläutert, wie die erforderlichen EE-Schnittstellen zu implementieren, und rufen Sie die common Language Runtime-Symbol-Dienstanbieter (SP) und den Binder-Schnittstellen.  
  
 [Registrieren einer ausdrucksauswertung](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Anmerkungen dieser, dass die EE selbst als eine Klassenfactory mit der common Language Runtime und die Visual Studio-Laufzeitumgebungen registrieren muss.  
  
 [Implementieren einer ausdrucksauswertung](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Beschreibt, wie der Prozess der Auswertung eines Ausdrucks für die Debug-Engine (DE), die Symbol-Dienstanbieter (SP), das binderobjekt und die ausdrucksauswertung (EE) enthält.  
  
 [Anzeige "lokal"](../../extensibility/debugger/displaying-locals.md)  
 Beschreibt, wie, wenn die Ausführung angehalten wird, das debugpaket die DE zum Abrufen einer Liste von lokalen Variablen und Argumenten aufruft.  
  
 [Auswerten eines überwachungsfensterausdrucks](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Beschreibt, wie der Visual Studio-Paket Debuggen die DE zum Bestimmen des aktuellen Werts des jeder Ausdruck in der Liste sehen Sie sich aufruft.  
  
 [Ändern Sie den Wert eines lokalen Elements](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Erklärt, dass in den Wert eines lokalen Elements ändern, jede Zeile des Fensters "lokal" ein zugeordnetes Objekt verfügt, das die Namen, Typ und aktuellen Wert eines lokalen Elements bereitstellt.  
  
 [Implementieren von typschnellansichten und benutzerdefinierten Viewern](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Erklärt, welche Schnittstelle muss von der Komponente zur Unterstützung von typschnellansichten und benutzerdefinierten Viewern implementiert werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Visual Studio-Debugger-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)