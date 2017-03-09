---
title: "Analysieren von Codeabdeckung in Build&#252;berpr&#252;fungstests | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59c07d15-511e-4fd0-b398-bde9d5ed00d9
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "mlearned"
manager: "douge"
---
# Analysieren von Codeabdeckung in Build&#252;berpr&#252;fungstests
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Codeabdeckungsanalyse in Microsoft Visual Studio zeigt, wie viel des Codes durch automatisierte Tests ausgeführt wird.  Weitere Informationen finden Sie unter [Bestimmen des Umfangs des zu testenden Codes mithilfe von Codeabdeckung](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 Wenn Sie in den Code überprüfen, werden die Tests auf dem Buildserver, zusammen mit allen anderen Tests von anderen Teammitgliedern ausgeführt. \(Wenn noch dieses aufgestellt haben, finden Sie unter [Ausführen von Testläufen im Buildprozess](../Topic/Run%20tests%20in%20your%20build%20process.md).\) Es ist nützlich, Codeabdeckung für den Builddienst zu analysieren, weil das das aktuellste und umfassendsten Bild der Codeabdeckung im gesamte bereitstellt.  Es schließt auch automatisierte Systemtests und andere codierte Tests ein, die normalerweise nicht auf die Entwicklungscomputer ausführen.  
  
1.  Öffnen Sie im Team Explorer **Builds** und fügen Sie dann eine Builddefinition hinzu oder bearbeiten Sie sie.  
  
2.  Auf der Seite **Prozess** erweitern, **Testquelle**, **TestlaufeinstellungenAutomatisierte Tests**.  **Typ der Testlaufeinstellungen\-DateiCodeabdeckung aktiviert** fest.  
  
     Wenn mehrere Test\-Quelldefinition haben, wiederholen Sie diesen Schritt für jedes.  
  
    -   *Es gibt kein Feld, das den Namen **Typ der Testlaufeinstellungen\-Datei** trägt.*  
  
         Wählen Sie unter **Automatisierte TestsTestassembly** aus, und wählen Sie die Schaltfläche mit den Auslassungspunkten **\[...\]** am Ende der Zeile aus.  Im Dialogfeld **Testlauf hinzufügen\/bearbeiten** unter **Test Runner**, wählen Sie **Visual Studio Test Runner** aus.  
  
 ![Festlegen der Builddefinition für Codeabdeckung](../test/media/codecoverage-plaincc.png "CodeCoverage\-plainCC")  
  
 Nachdem der Build ausgeführt wird, werden die Ergebnisse in der Buildzusammenfassung.  
  
## Siehe auch  
 [Bestimmen des Umfangs des zu testenden Codes mithilfe von Codeabdeckung](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)