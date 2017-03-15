---
title: "Gewusst wie: Verwenden des parallelen &#220;berwachungsfensters | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.parallelwatch"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debugger, Paralleles Überwachungsfenster"
ms.assetid: 28004d9b-420c-48f7-b80e-ab1519802558
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Verwenden des parallelen &#220;berwachungsfensters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Im parallelen Überwachungsfenster können Sie gleichzeitig die Werte anzeigen, die ein Ausdruck auf mehreren Threads enthält.  Jede Zeile stellt einen Thread in einer Anwendung ausgeführten dar. Allerdings wird ein Thread möglicherweise in mehreren Zeilen angezeigt werden.  Genauer gesagt stellt jede Zeile einen Funktionsaufruf dar, dessen Funktionssignatur der Funktion auf dem aktuellen Stapelrahmen entspricht.  Sie können die Elemente in den Spalten sortieren, neu anordnen, entfernen und gruppieren.  Sie können Threads kennzeichnen bzw. die Kennzeichnung aufheben, ihn einfrieren \(anhalten\) und reaktivieren \(fortsetzen\).  Die folgenden Spalten werden im Fenster **Parallele Überwachung** angezeigt:  
  
-   Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.  
  
-   Die Framespalte, in der ein Pfeil den ausgewählten Frame angibt.  
  
-   Eine konfigurierbare Spalte, in der der Computer, der Prozess, die Kachel, die Aufgabe und der Thread angezeigt werden können.  
  
    > [!TIP]
    >  Sie müssen das Fenster **Parallele Aufgabe** öffnen, um die Aufgabeninformationen im Fenster **Parallele Überwachung** anzuzeigen.  
  
-   Die Spalte **\<Überwachung hinzufügen\>**, in der Ausdrücke zur Überwachung eingeben werden können.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### So zeigen Sie das parallele Überwachungsfenster an  
  
1.  Legen Sie einen Haltepunkt im Code fest.  
  
2.  Klicken Sie in der Menüleiste auf **Debuggen** und dann auf **Debuggen starten**.  Warten Sie, bis die Anwendung den Haltepunkt erreicht hat.  
  
3.  Klicken Sie in der Menüleiste auf **Debuggen**, **Fenster**, **Parallele Überwachung**, und wählen Sie dann ein Überwachungsfenster aus.  Sie können bis zu vier Fenster öffnen.  
  
### So fügen Sie einen Überwachungsausdruck hinzu  
  
-   Wählen Sie **\<Überwachung hinzufügen\>** aus, und geben Sie einen Überwachungsausdruck an.  
  
### So Kennzeichnen Sie einen Thread bzw. haben die Kennzeichnung auf  
  
-   Wählen Sie die Spalte zur Kennzeichnung für die Zeile aus, oder öffnen Sie das Kontextmenü für den Thread, und wählen Sie **Flag entfernen** oder **Flag** aus.  
  
### So zeigen Sie nur gekennzeichnete Threads an  
  
-   Klicken Sie auf die Schaltfläche "Nur gekennzeichnete Threads anzeigen" in der linken oberen Ecke des Fensters **Parallele Überwachung** aus.  
  
### So wechseln Sie Frames  
  
-   Doppelklicken Sie auf die Framespalte. \(Tastatur: Wählen Sie die Zeile aus, und drücken Sie EINGABETASTE.\)  
  
### So sortieren Sie eine Spalte  
  
-   Wählen Sie Spaltenüberschrift aus.  
  
### So gruppieren Sie Threads  
  
-   Öffnen Sie das Kontextmenü für das parallele Überwachungsfenster, wählen Sie die Option **Gruppieren nach** aus, und wählen Sie dann das entsprechende Untermenüelement aus.  
  
### So frieren Sie Threads ein oder reaktivieren sie  
  
-   Öffnen Sie das Kontextmenü für die Zeile, und wählen Sie dann **Einfrieren** oder **Entsperren** aus.  
  
### So exportieren Sie Daten in das parallele Überwachungsfenster  
  
-   Wählen Sie die Schaltfläche **In Excel öffnen** aus, und wählen Sie dann **Exportieren nach CSV** oder **In Excel öffnen** aus.  
  
### So filtern Sie nach einem booleschen Ausdruck  
  
-   Geben Sie im Feld **Nach booleschem Ausdruck filtern** einen booleschen Ausdruck ein.  Vom Debugger wird der Ausdruck für jeden Threadkontext ausgewertet.  Nur Zeilen mit einem Wert von `true` werden angezeigt.  
  
## Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Verwenden des Fensters "GPU\-Threads"](../debugger/how-to-use-the-gpu-threads-window.md)   
 [Exemplarische Vorgehensweise: Debuggen einer C\+\+ AMP\-Anwendung](../Topic/Walkthrough:%20Debugging%20a%20C++%20AMP%20Application.md)