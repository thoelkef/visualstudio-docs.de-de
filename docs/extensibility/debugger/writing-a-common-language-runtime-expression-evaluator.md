---
title: "Schreiben Sie eine Common Language Runtime-Ausdrucksauswerter | Microsoft Docs"
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
  - "Ausdrucks-Auswerter, Lernprogramm"
  - "Auswertung von Ausdrücken, Beispiele"
  - "Debuggen [Debugging-SDK] Ausdruck Bewerter-Lernprogramm"
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Schreiben Sie eine Common Language Runtime-Ausdrucksauswerter
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Die Auswertung eines Ausdrucks \(EE\) ist der Teil des Debugmoduls \(DE\), die behandelt die Syntax und Semantik der Programmiersprache, die den gedebuggten Code erzeugt. Ausdrücke müssen innerhalb des Kontexts einer Programmiersprache ausgewertet werden. In einigen Sprachen, z. B. der Ausdruck "A \+ B" bedeutet "die Summe von A und b." In anderen Sprachen kann derselbe Ausdruck "A oder b" bedeuten. Daher muss ein separates EE für jede Programmiersprache geschrieben werden, das zu debuggende Objektcode in Visual Studio\-IDE generiert.  
  
 Einige Aspekte von Visual Studio\-Debug\-Paket müssen den Code im Kontext der Programmiersprache interpretiert werden. Z. B. wenn die Ausführung hält an einem Haltepunkt, alle Ausdrücke, die der Benutzer, in eingegeben hat einem **Überwachen** Fenster ausgewertet und angezeigt werden. Darüber hinaus kann der Benutzer den Wert einer lokalen Variablen ändern, durch Eingabe eines Ausdrucks in einen **Überwachen** Fenster oder in der **sofort** Fenster.  
  
## In diesem Abschnitt  
 [Common Language Runtime und die Auswertung von Ausdrücken](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Erläutert, dass beim Integrieren von proprietären Programmiersprache, in der Visual Studio\-IDE schreiben eine EE Auswerten von Ausdrücken im Kontext der proprietäre Sprache kann Microsoft intermediate Language \(MSIL\) kompiliert werden, ohne ein Debugmodul schreiben kann.  
  
 [Expression Evaluator\-Architektur](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Erläutert, wie die erforderlichen EE\-Schnittstellen implementieren, und rufen Sie die common Language Runtime Symbol Dienstanbieter \(SP\) und Binder\-Schnittstellen.  
  
 [Registrieren eine Auswertung eines Ausdrucks](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Bemerkt, dass die EE Form einer Klassenfactory mit der common Language Runtime und die Common Language Runtime\-Umgebung von Visual Studio registriert werden muss.  
  
 [Implementieren eine Auswertung eines Ausdrucks](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Beschreibt, wie der Prozess der Auswertung eines Ausdrucks die Debugging\-Modul \(DE\), den Symbol\-Anbieter \(SP\), der Binder\-Objekt und der Auswertung eines Ausdrucks \(EE\) umfasst.  
  
 [Anzeigen von lokalen Variablen](../../extensibility/debugger/displaying-locals.md)  
 Beschreibt, wie, wenn die Ausführung angehalten wird, das debugpaket DE zum Abrufen einer Liste von lokalen Variablen und Argumenten aufruft.  
  
 [Evaluieren einen Überwachungsausdruck\-Fenster](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Beschreibt, wie das Visual Studio\-Paket Debuggen DE zum Bestimmen des aktuellen Werts jedes Ausdrucks in seine Beobachtungsliste aufruft.  
  
 [Ändern des Werts von einer lokalen](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Erläutert, dass in den Wert eines lokalen ändern, jede Zeile des Fensters "lokal" ein zugeordnetes Objekt aufweist, das den Namen, den Typ und den aktuellen Wert eines lokalen bereitstellt.  
  
 [Implementieren von Typ Schnellansichten und benutzerdefinierten Viewer](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Erklärt, welche Schnittstelle muss von der Komponente zur Unterstützung von Typ Schnellansichten und benutzerdefinierten Viewer implementiert werden.  
  
## Siehe auch  
 [Visual Studio\-Debugger\-Erweiterbarkeit](../../extensibility/debugger/visual-studio-debugger-extensibility.md)