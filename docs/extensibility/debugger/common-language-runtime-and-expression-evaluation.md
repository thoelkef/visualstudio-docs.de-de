---
title: "Common Language Runtime und die Auswertung von Ausdr&#252;cken | Microsoft Docs"
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
  - "Debuggen die Auswertung von Ausdrücken [Debuggen SDK]"
  - "Auswertung von Ausdrücken und common Language runtime"
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Common Language Runtime und die Auswertung von Ausdr&#252;cken
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  In Visual Studio 2015 ist diese Art der Implementierung von ausdrucksauswertungen veraltet. Informationen über das Implementieren von CLR\-ausdrucksauswertungen finden Sie unter [CLR\-Ausdrucksauswertungen](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) und [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compiler, kompiliert z. B. Visual Basic und c\# \(ausgesprochen als C\-Sharp\), die die Common Language Runtime \(CLR\) abzielen, Microsoft Intermediate Language \(MSIL\), erzeugen, die später in systemeigenen Code. Die CLR bietet eine Debugging\-Modul \(DE\), den resultierenden Code zu debuggen. Wenn Sie beabsichtigen, Ihre proprietäre Programmiersprache in Visual Studio\-IDE integriert, Sie können auch zu MSIL kompiliert und daher keine eigene DE schreiben. Sie müssen jedoch eine Auswertung eines Ausdrucks \(EE\) schreiben, der das Auswerten von Ausdrücken im Kontext der Programmiersprache kann.  
  
## Diskussion  
 Computer Ausdrücke werden im Allgemeinen analysiert, um einen Satz von Objekten und einen Satz von Operatoren verwendet werden, um sie bearbeiten zu erzeugen. Objekte z. B. der Ausdruck "A \+ B" analysiert werden, möglicherweise um den Additionsoperator \(\+\) gelten für die Daten, "A" und "B", was möglicherweise zu einem anderen Datenobjekt. Als eine Struktur mit den Operatoren auf den Knoten der Struktur und die Datenobjekte Zweigstellen, die in einem Programm werden am häufigsten die Gesamtmenge Datenobjekte, Operatoren und ihre Zuordnungen dargestellt. Ein Ausdruck, der in Strukturansicht aufgeteilt wurde wird eine analysierte Struktur häufig aufgerufen werden.  
  
 Nachdem ein Ausdruck analysiert wurde, wird ein Symbol\-Anbieter \(SP\) aufgerufen, um jedes Datenobjekt zu bewerten. Beispielsweise, wenn "A" definiert ist, sowohl in mehr als eine Methode, und klicken Sie dann auf die Frage "Welche A?" muss beantwortet werden, bevor der Wert von A ermittelt werden kann. Die Antwort des SP ist so etwas wie "Das dritte Element im fünften Stapelrahmen" oder "A, die 50 Bytes hinter dem Anfang der statischen Speicher ist für diese Methode belegt."  
  
 Neben MSIL für die Anwendung selbst erstellt, können CLR\-Compiler außerdem sehr aussagekräftig Debuginformationen zu erstellen, die in einer Programmdatenbankdatei \(.pdb\)\-Datei geschrieben wird. Solange ein proprietäre Sprache\-Compiler Debuginformationen in das gleiche Format wie die CLR\-Compiler erstellt, ist die CLR SP zu erkennen, dass der Sprache Datenobjekte benannt. Nachdem ein benanntes Objekt identifiziert wurde, verwendet die EE Binder\-Objekt das Datenobjekt zuordnen \(oder Bindung\), um den Speicherbereich, der den Wert des Objekts enthält. Die DE kann dann abrufen oder einen neuen Wert für das Objekt festlegen.  
  
 Ein proprietärer Compiler bietet CLR\-Debug\-Informationen durch Aufrufen der `ISymbolWriter` Schnittstelle \(definiert in .NET Framework im Namespace `System.Diagnostics.SymbolStore`\). Kompilieren in MSIL und Debuginformationen über diese Schnittstellen schreiben, kann ein proprietärer Compiler die CLR DE und SP verwenden. Dies vereinfacht eine proprietäre Sprache in Visual Studio\-IDE integrieren.  
  
 Wenn die CLR DE die proprietäre EE zum Auswerten eines Ausdrucks aufruft, stellt die DE die EE mit Schnittstellen ein SP und ein binderobjekt. Daher ist das Schreiben einer CLR\-basierten Debug\-Modul bedeutet, dass es nur erforderlich, um die entsprechenden Expression Evaluator Schnittstellen implementieren. die CLR übernimmt die Bindung und das Symbol für Sie.  
  
## Siehe auch  
 [Schreiben Sie eine CLR\-Ausdrucksauswerter](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)