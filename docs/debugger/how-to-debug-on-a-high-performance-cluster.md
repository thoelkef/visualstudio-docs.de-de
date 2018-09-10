---
title: 'Vorgehensweise: Debuggen auf einem Hochleistungscluster | Microsoft-Dokumentation'
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
ms.openlocfilehash: 9964621c216d058581d9298956ba90ac6cdbef86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280791"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Gewusst wie: Debuggen eines Hochleistungsclusters
Das Debuggen eines Multiprocessing-Programms in einem Hochleistungscluster gleicht dem Debuggen eines gewöhnlichen Programms auf einem Remotecomputer. Es müssen jedoch einige zusätzliche Aspekte berücksichtigt werden. Allgemeine remote-setupanforderungen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
 Beim Debuggen auf einem Hochleistungscluster können alle Debugfenster von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und alle Verfahren für das Remotedebuggen eingesetzt werden. Da Sie jedoch remote debuggen, ist das externe Konsolenfenster nicht verfügbar.  
  
 Die **Threads** Fenster und **Prozesse** Fenster sind besonders nützlich zum Debuggen paralleler Anwendungen. Tipps zur Verwendung dieser Fenster finden Sie [Vorgehensweise: Verwenden des Fensters Prozesse](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) und [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters Threads](../debugger/how-to-use-the-threads-window.md).  
  
 In den folgenden Verfahren werden einige Techniken vorgestellt, die beim Debuggen in einem Hochleistungscluster besonders nützlich sind.  
  
 Beim Debuggen einer parallelen Anwendung kann es erforderlich sein, einen Haltepunkt für einen bestimmten Thread, Prozess oder Computer festzulegen. Dies kann durch das Erstellen eines normalen Haltepunkts und das Hinzufügen eines Haltepunktfilters erfolgen.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>So öffnen Sie das Dialogfeld Haltepunktfilter  
  
1.  Mit der rechten Maustaste ein Haltepunktsymbol in einem Quellcodefenster den **Disassembly** Fenster die **Aufrufliste** Fenster oder der **Haltepunkte** Fenster.  
  
2.  Klicken Sie im Kontextmenü auf **Filter**. Diese Option kann am Anfang angezeigt, Ebene oder im Untermenü unter **Haltepunkte**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>So legen Sie einen Haltepunkt für einen bestimmten Computer fest  
  
1.  Rufen Sie den Computernamen aus der **Prozesse** Fenster.  
  
2.  Wählen Sie einen Haltepunkt, und Öffnen der **Haltepunktfilter** wie im vorherigen Verfahren beschrieben das Dialogfeld.  
  
3.  In der **Haltepunktfilter** (Dialogfeld), Typ:  
  
     MachineName =*IhrComputername*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>So legen Sie einen Haltepunkt für einen bestimmten Prozess fest  
  
1.  Den Prozessnamen oder Prozess-ID. die **Prozesse** Fenster.  
  
2.  Wählen Sie einen Haltepunkt, und Öffnen der **Haltepunktfilter** Dialogfeld wie in der ersten Prozedur.  
  
3.  In der **Haltepunktfilter** (Dialogfeld), Typ:  
  
     `ProcessName =`  *yourprocessname*  
  
     – oder –  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>So legen Sie einen Haltepunkt für einen bestimmten Thread fest  
  
1.  Rufen Sie den Threadnamen oder thread-ID. die **Threads** Fenster.  
  
2.  Wählen Sie einen Haltepunkt, und Öffnen der **Haltepunktfilter** wie in der ersten Vorgehensweise beschrieben das Dialogfeld.  
  
3.  In der **Haltepunktfilter** (Dialogfeld), Typ:  
  
     `ThreadName =` *yourthreadname*  
  
     – oder –  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Zum Erstellen eines komplexeren Filters können Sie Klauseln mit `&` (dem Operator UND), `||` (dem Operator ODER) und `!` (dem Operator NICHT) und Klammern kombinieren.  
  
4.  Klicken Sie auf **OK**.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird das Erstellen eines Filters für einen Haltepunkt für einen Computer mit dem Namen `marvin` und einen Thread mit dem Namen `fourier1` beschrieben.  
  
`(MachineName = marvin) & (ThreadName = fourier1)`  

  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)   
 [Vorgehensweise: Verwenden des Prozessfensters](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))   
 [Erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Threads und Prozessen](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))   
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)