---
title: "Aufrufer-/Aufgerufener-Ansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.callercallee"
helpviewer_keywords: 
  - "Profilerstellungstools, Berichte, Aufrufer-/Aufgerufener-Ansicht"
  - "Profilerstellungstools, Aufrufer-/Aufgerufener-Ansicht"
  - "Leistungsberichte, Aufrufer-/Aufgerufener-Ansicht"
  - "Aufrufer-/Aufgerufener-Ansicht"
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 32
caps.handback.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aufrufer-/Aufgerufener-Ansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Aufrufer\-\/Aufgerufener\-Ansicht werden Profilerstellungsinformationen für eine ausgewählte Funktion und die übergeordneten und untergeordneten Funktionen angezeigt.  Die Aufrufer\-\/Aufgerufener\-Ansicht enthält drei Raster:  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und zeigt Profilerstellungsinformationen für die ausgewählte Funktion an.  Die Werte beinhalten aller gesammelten Aufrufe der Funktion während der Profilerstellungsausführung.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und zeigt die Anzahl der Werte der ausgewählten \(aktuellen\) Funktion an, die durch Aufrufe der \(übergeordneten\) Aufruferfunktion generiert wurden.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und zeigt Profilerstellungsinformationen für die aufgerufenen \(untergeordneten\) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
 Welche Spalten in der Aufrufer\-\/Aufgerufener\-Ansicht verfügbar sind, ist abhängig von der Profilerstellungsmethode \(Sampling oder Instrumentation\), die zum Sammeln der Daten verwendet wurde, und davon, ob .NET\-Arbeitsspeicherdaten in der Profilerstellungsausführung gesammelt wurden.  
  
 Im mittleren Bereich der Berichtsansicht können Sie eine andere Funktion als aktuelle Funktion auswählen, indem Sie in einem der anderen beiden Bereiche der Ansicht auf die gewünschte Funktion doppelklicken.  Die Berichtsansicht wird automatisch aktualisiert, um die Änderungen wiederzugeben.  
  
 Sie können die Daten durch Klicken auf die Spaltennamen sortieren.  Der Aufrufer\-\/Aufgerufener\-Ansicht können zusätzliche Spalten hinzugefügt werden.  Weitere Informationen finden Sie unter [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md).  
  
## Siehe auch  
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-instrumentation-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Sampling](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-contention-data.md)