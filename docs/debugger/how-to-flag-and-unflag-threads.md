---
title: "Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Threads, Wechsel [Debuggen]"
ms.assetid: 952d579d-6911-413e-b3e5-54e7e797e70c
caps.latest.revision: 33
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 33
---
# Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können einen Thread, dem Sie besondere Aufmerksamkeit widmen möchten, kennzeichnen, indem Sie es in den Fenstern **Threads**, **Parallele Stapel**, **Parallele Überwachung** und **GPU\-Threads** mit einem Symbol versehen.  Anhand dieses Symbols können Sie gekennzeichnete Threads von anderen Threads unterscheiden.  
  
 Gekennzeichnete Threads werden auch in der Liste **Thread** auf der Symbolleiste **Debugspeicherort** gesondert behandelt.  In dieser Liste können alle Threads oder nur gekennzeichnete Threads aufgeführt werden.  Beim Kennzeichnen eines Threads wird die Anzeige der Liste **Thread** automatisch zu den gekennzeichneten Threads umgeschaltet. Bei Bedarf können Sie in der Anzeige jedoch zurückwechseln, sodass alle Threads angezeigt werden.  
  
### So können Sie einen Thread mithilfe des Fensters Threads kennzeichnen oder seine Kennzeichnung aufheben  
  
-   Suchen Sie im Fenster **Threads** den gewünschten Thread, und klicken Sie auf das Flagsymbol, um das Flag auszuwählen oder zu löschen.  
  
### So heben Sie die Kennzeichnung aller Threads auf  
  
-   Klicken Sie im Fenster **Threads** mit der rechten Maustaste auf einen Thread, und klicken Sie anschließend auf **Kennzeichnung aller Threads aufheben**.  
  
### So zeigen Sie nur gekennzeichnete Threads an  
  
-   Wählen Sie im Fenster "Debuggen" die Schaltfläche "Kennzeichnen" aus.  
  
### So kennzeichnen Sie nur eigenen Code  
  
1.  Klicken Sie auf der Symbolleiste am oberen Rand des Fensters **Threads** auf das Kennzeichnungssymbol.  
  
2.  Klicken Sie in der Dropdownliste auf **Nur eigenen Code kennzeichnen**.  
  
### So kennzeichnen Sie Threads, die ausgewählten Modulen zugeordnet sind  
  
1.  Klicken Sie auf der Symbolleiste des Fensters **Threads** auf das Kennzeichnungssymbol.  
  
2.  Klicken Sie in der Dropdownliste auf **Benutzerdefinierte Modulauswahl kennzeichnen**.  
  
3.  Wählen Sie im Dialogfeld **Module auswählen** die gewünschten Module aus.  
  
4.  \(Optional\) Geben Sie Im Feld **Suchen** eine Suchzeichenfolge für bestimmte Module ein.  
  
5.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md)