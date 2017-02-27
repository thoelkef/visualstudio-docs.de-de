---
title: "Gewusst wie: Debuggen eines Hochleistungsclusters | Microsoft Docs"
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
  - "Debuggen von Clustern"
  - "Leistungsstarkes Debuggen"
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Gewusst wie: Debuggen eines Hochleistungsclusters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Debuggen eines Multiprocessing\-Programms in einem Hochleistungscluster gleicht dem Debuggen eines gewöhnlichen Programms auf einem Remotecomputer.  Es müssen jedoch einige zusätzliche Aspekte berücksichtigt werden.  Allgemeine Remote\-Setupanforderungen finden Sie unter [Remotedebugging](../debugger/remote-debugging.md).  
  
 Beim Debuggen auf einem Hochleistungscluster können alle Debugfenster von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und alle Verfahren für das Remotedebuggen eingesetzt werden.  Da Sie jedoch remote debuggen, ist das externe Konsolenfenster nicht verfügbar.  
  
 Das **Threadfenster** und das **Prozessfenster** sind zum Debuggen von parallelen Anwendungen besonders nützlich.  Tipps zur Verwendung dieser Fenster finden Sie unter [How to: Use the Processes Window](http://msdn.microsoft.com/de-de/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) und [Gewusst wie: Verwenden des Fensters Threads](../debugger/how-to-use-the-threads-window.md)  
  
 In den folgenden Verfahren werden einige Techniken vorgestellt, die beim Debuggen in einem Hochleistungscluster besonders nützlich sind.  
  
 Beim Debuggen einer parallelen Anwendung kann es erforderlich sein, einen Haltepunkt für einen bestimmten Thread, Prozess oder Computer festzulegen.  Dies kann durch das Erstellen eines normalen Haltepunkts und das Hinzufügen eines Haltepunktfilters erfolgen.  
  
### So öffnen Sie das Dialogfeld Haltepunktfilter  
  
1.  Klicken Sie in einem Quellcodefenster, im **Disassemblyfenster**, im **Aufruflistenfenster** oder im **Haltpunktfenster** mit der rechten Maustaste auf ein Haltepunktsymbol.  
  
2.  Klicken Sie im Kontextmenü auf **Filter**.  Diese Option wird möglicherweise auf oberster Ebene oder im Untermenü unter **Haltepunkte** angezeigt.  
  
### So legen Sie einen Haltepunkt für einen bestimmten Computer fest  
  
1.  Entnehmen Sie dem Fenster **Prozesse** den Computernamen.  
  
2.  Wählen Sie einen Haltepunkt aus, und öffnen Sie wie in der vorigen Vorgehensweise beschrieben das Dialogfeld **Haltepunktfilter**.  
  
3.  Geben Sie im Dialogfeld **Haltepunktfilter** Folgendes ein:  
  
     Computername \=*IhrComputerName*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` \(dem Operator UND\), `||` \(dem Operator ODER\) und `!` \(dem Operator NICHT\) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
### So legen Sie einen Haltepunkt für einen bestimmten Prozess fest  
  
1.  Entnehmen Sie dem **Prozessfenster** den Prozessnamen oder die Prozess\-ID.  
  
2.  Wählen Sie einen Haltepunkt aus, und öffnen Sie wie in der ersten Vorgehensweise beschrieben das Dialogfeld **Haltepunktfilter**.  
  
3.  Geben Sie im Dialogfeld **Haltepunktfilter** Folgendes ein:  
  
     `ProcessName =`  *IhrProzessName*  
  
     – oder –  
  
     `ProcessID =` *Ihre ProzessIDNummer*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` \(dem Operator UND\), `||` \(dem Operator ODER\) und `!` \(dem Operator NICHT\) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
### So legen Sie einen Haltepunkt für einen bestimmten Thread fest  
  
1.  Entnehmen Sie dem Fenster **Threads** den Threadnamen oder die Thread\-ID.  
  
2.  Wählen Sie einen Haltepunkt aus, und öffnen Sie wie in der ersten Vorgehensweise beschrieben das Dialogfeld **Haltepunktfilter**.  
  
3.  Geben Sie im Dialogfeld **Haltepunktfilter** Folgendes ein:  
  
     `ThreadName =` *IhrThreadName*  
  
     – oder –  
  
     `ThreadID =` *IhreThreadIDNummer*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` \(dem Operator UND\), `||` \(dem Operator ODER\) und `!` \(dem Operator NICHT\) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
## Beispiel  
 Im folgenden Beispiel wird das Erstellen eines Filters für einen Haltepunkt für einen Computer mit dem Namen `marvin` und einen Thread mit dem Namen `fourier1` beschrieben.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Remotedebugging](../debugger/remote-debugging.md)   
 [How to: Use the Processes Window](http://msdn.microsoft.com/de-de/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Gewusst wie: Verwenden des Fensters Threads](../debugger/how-to-use-the-threads-window.md)   
 [Threads and Processes](http://msdn.microsoft.com/de-de/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)