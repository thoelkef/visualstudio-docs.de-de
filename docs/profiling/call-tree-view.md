---
title: "Aufrufstrukturansicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.calltree"
helpviewer_keywords: 
  - "Aufrufstrukturansicht"
  - "Leistungsberichte, Aufrufstrukturansicht"
  - "Berichte für Profilerstellungstools, Aufrufstrukturansicht"
  - "Profilerstellungstools, Aufrufstrukturansicht"
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Aufrufstrukturansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Aufrufstrukturansicht zeigt die Funktionsausführungspfade an, die in der profilierten Anwendung durchlaufen wurden.  Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente.  Jeder Funktionsknoten führt alle Funktionen, die er aufgerufen hat, sowie Leistungsdaten über diese Funktionsaufrufe auf.  
  
 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad einer Funktion markieren, die die meiste Zeit in Anspruch genommen hat oder für die am häufigsten ein Sampling ausgeführt wurde.  Um den leistungsintensivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  
  
 Jeder Prozess in der Profilerstellungsausführung wird als Stammknoten angezeigt.  Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.  
  
 Durch Festlegen des Stammknotens verhindern Sie, dass alle anderen Einträge außer der Teilstruktur des ausgewählten Knotens in der Ansicht angezeigt werden.  Sie können den Stammknoten wieder auf den zuvor angezeigten Knoten zurücksetzen.  Klicken Sie in der Aufrufstrukturansicht mit der rechten Maustaste, und wählen Sie dann **Stamm zurücksetzen** aus.  
  
 Die Aufrufstrukturansicht kann angepasst werden, indem Spalten hinzugefügt bzw. entfernt werden.  Klicken Sie mit der rechten Maustaste auf die **Titelleiste der Spalte**, und wählen Sie dann **Spalten hinzufügen\/entfernen** aus.  
  
 Die Aufrufstrukturansicht kann für die Rauschunterdrückung konfiguriert werden, indem die dargestellte Datenmenge beschränkt wird.  Durch die Rauschunterdrückung werden Leistungsprobleme in der Ansicht besser erkennbar.  Durch besser identifizierbare Leistungsprobleme wird die Analyse vereinfacht.  Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren der Rauschunterdrückung in Berichtsansichten](../profiling/how-to-configure-noise-reduction-in-report-views.md).  
  
> [!NOTE]
>  Wenn die Rauschunterdrückung für die Anzeige einer Warnung konfiguriert ist, sobald sie aktiviert ist, wird eine Informationsleiste im Bericht angezeigt.  
  
 Weitere Informationen zu Definitionen für Spalten in der Aufrufstrukturansicht finden Sie unter folgender Adresse:  
  
 [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)  
  
 [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)  
  
 [Aufrufstrukturansicht \- Sampling](../profiling/call-tree-view-dotnet-memory-sampling-data.md)  
  
 [Aufrufstrukturansicht](../profiling/call-tree-view-contention-data.md)  
  
## Siehe auch  
 [Berichtsansichten für Profilerstellungstools](../profiling/performance-report-views.md)   
 [Grundlagen zu Instrumentationsdatenwerten](../profiling/understanding-instrumentation-data-values.md)   
 [Grundlagen zu Samplingdatenwerten](../profiling/understanding-sampling-data-values.md)