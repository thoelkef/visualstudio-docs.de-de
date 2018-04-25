---
title: 'Vorgehensweise: Debuggen auf einem Hochleistungscluster | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97e692d4d376473f3eaf283a53117d0bf343ea71
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Gewusst wie: Debuggen eines Hochleistungsclusters
Das Debuggen eines Multiprocessing-Programms in einem Hochleistungscluster gleicht dem Debuggen eines gewöhnlichen Programms auf einem Remotecomputer. Es müssen jedoch einige zusätzliche Aspekte berücksichtigt werden. Allgemeine remote Installationsanforderungen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
 Beim Debuggen auf einem Hochleistungscluster können alle Debugfenster von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und alle Verfahren für das Remotedebuggen eingesetzt werden. Da Sie jedoch remote debuggen, ist das externe Konsolenfenster nicht verfügbar.  
  
 Die **Threads** Fenster und **Prozesse** Fenster sind besonders nützlich zum Debuggen von parallelen Anwendungen. Tipps zur Verwendung dieser Fenster finden Sie unter [wie: Verwenden des Fensters Prozesse](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) und [Exemplarische Vorgehensweise: Debuggen über das Fenster "Threads"](../debugger/how-to-use-the-threads-window.md).  
  
 In den folgenden Verfahren werden einige Techniken vorgestellt, die beim Debuggen in einem Hochleistungscluster besonders nützlich sind.  
  
 Beim Debuggen einer parallelen Anwendung kann es erforderlich sein, einen Haltepunkt für einen bestimmten Thread, Prozess oder Computer festzulegen. Dies kann durch das Erstellen eines normalen Haltepunkts und das Hinzufügen eines Haltepunktfilters erfolgen.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>So öffnen Sie das Dialogfeld Haltepunktfilter  
  
1.  Mit der rechten Maustaste ein Haltepunktsymbol in einem Quellcodefenster angezeigt, die **Disassembly** Fenster die **Aufrufliste** Fenster, oder die **Haltepunkte** Fenster.  
  
2.  Klicken Sie im Kontextmenü auf **Filter**. Diese Option kann am oberen angezeigt, Ebene oder im Untermenü unter **Haltepunkte**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>So legen Sie einen Haltepunkt für einen bestimmten Computer fest  
  
1.  Ruft den Computernamen aus der **Prozesse** Fenster.  
  
2.  Wählen Sie einen Haltepunkt aus, und öffnen Sie die **Haltepunktfilter** (Dialogfeld), wie im vorherigen Verfahren beschrieben.  
  
3.  In der **Haltepunktfilter** (Dialogfeld), Typ:  
  
     Computername =*IhrComputername*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>So legen Sie einen Haltepunkt für einen bestimmten Prozess fest  
  
1.  Abrufen von den Prozessnamen oder Prozess-ID. die **Prozesse** Fenster.  
  
2.  Wählen Sie einen Haltepunkt aus, und öffnen Sie die **Haltepunktfilter** (Dialogfeld), wie in der ersten Prozedur.  
  
3.  In der **Haltepunktfilter** (Dialogfeld), Typ:  
  
     `ProcessName =`  *yourprocessname*  
  
     – oder –  
  
     `ProcessID =` *Ihre Prozessidnummer*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>So legen Sie einen Haltepunkt für einen bestimmten Thread fest  
  
1.  Ruft den Threadnamen, oder thread-ID. die **Threads** Fenster.  
  
2.  Wählen Sie einen Haltepunkt aus, und öffnen Sie die **Haltepunktfilter** wie in der ersten Vorgehensweise beschrieben das Dialogfeld.  
  
3.  In der **Haltepunktfilter** (Dialogfeld), Typ:  
  
     `ThreadName =` *yourthreadname*  
  
     – oder –  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Erstellen eines Filters für einen Haltepunkt für einen Computer mit dem Namen `marvin` und einen Thread mit dem Namen `fourier1` beschrieben.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)   
 [Vorgehensweise: Verwenden des Prozessfensters](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Threads und Prozessen](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)