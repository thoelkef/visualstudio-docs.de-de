---
title: "Gewusst wie: Ausschlie&#223;en oder Einschlie&#223;en kurzer Funktionen in die Instrumentation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Instrumentationsereignisse"
  - "Profilerstellungstools, Einschließen von kurzen Funktionen"
  - "Profilerstellungstools, Ausschließen von kurzen Funktionen"
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Gewusst wie: Ausschlie&#223;en oder Einschlie&#223;en kurzer Funktionen in die Instrumentation
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Kleine Funktionen* werden standardmäßig aus der Instrumentation ausgeschlossen.  Kleine Funktionen sind kurze Funktionen, die keine Funktionsaufrufe ausführen.  Bei Ausschluss kleinen Funktionen verringert sich der Instrumentation\-Mehraufwand, was zu einer verbesserten Instrumentationsgeschwindigkeit führt.  Durch den Ausschluss kleiner Funktionen wird auch die Größe der VSP\-Datendatei für die Erstellung von Leistungsprofilen sowie die für die Analyse erforderliche Zeit reduziert.  Wenn kleine Funktionen ausgeschlossen werden, wird die in den kleinen Funktionen aufgewendete Zeit auf die exklusive und inklusive Zeit der übergeordneten Funktionen angerechnet.  Kleine Funktionen können, wie im folgenden Verfahren beschrieben, in die Instrumentation eingeschlossen oder daraus ausgeschlossen werden.  
  
### So schließen Sie kurze Funktionen in die Instrumentation ein oder davon aus  
  
1.  Wählen Sie im **Leistungs\-Explorer** die Option **Leistungssitzung**, klicken Sie dann mit der rechten Maustaste, und wählen Sie **Eigenschaften** aus.  
  
     Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.  
  
2.  Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaft **Instrumentation**.  
  
3.  Um kurze Funktionen aus der Instrumentation auszuschließen, aktivieren Sie **Kurze Funktionen aus Instrumentation ausschließen**.  Dies ist die Standardeinstellung.  
  
     \- oder \-  
  
     Um kurze Funktionen in die Instrumentation einzuschließen, deaktivieren Sie **Kurze Funktionen aus Instrumentation ausschließen**.  
  
4.  Klicken Sie auf **OK**.  
  
## Siehe auch  
 [Steuern der Datensammlung](../profiling/controlling-data-collection.md)   
 [Eigenschaften von Leistungssitzungen](../profiling/performance-session-properties.md)