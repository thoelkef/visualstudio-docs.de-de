---
title: "Aufrufer-/Aufgerufener-Ansicht - Profiler-Konfliktdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aufrufer-/Aufgerufener-Ansicht"
ms.assetid: a18a1b1b-9b39-43c7-b1f3-708fd20376f6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Aufrufer-/Aufgerufener-Ansicht - Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Aufrufer\-\/Aufgerufener\-Ansicht werden Konfliktinformationen für eine ausgewählte Funktion und die übergeordneten und untergeordneten Funktionen angezeigt.  Die Aufrufer\-\/Aufgerufener\-Ansicht enthält drei Raster.  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und zeigt Konfliktinformationen für die ausgewählte Funktion an.  Die Werte enthalten alle blockierenden Konflikte für die Funktion.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und zeigt die einzelnen Beiträge der \(übergeordneten\) Aufruferfunktion zu den Werten der ausgewählten \(aktuellen\) Funktion an.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** werden im untersten Raster angezeigt und zeigen Profilerstellungsinformationen für die aufgerufenen \(untergeordneten\) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Typ**|Der Kontext der Funktion:<br /><br /> -   **0** – die aktuelle Funktion<br />-   **1** – eine Funktion, die die aktuelle Funktion aufruft<br />-   **2** – eine Funktion, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Exklusive blockierte Zeit**|-   Bei der aktuellen Funktion die Zeit, in der diese Funktion für die Ausführung von Code im Funktionstext blockiert war.  Blockierte Zeiten in Funktionen, die von der Funktion aufgerufen wurden, sind nicht eingeschlossen.<br />-   Bei einer Aufruferfunktion ist dies der Anteil der exklusiven blockierten Zeit der aktuellen Funktion, die aufgetreten ist, als die Funktion die aktuelle Funktion aufgerufen hat.<br />-   Bei einer aufgerufenen Funktion ist dies die Zeit, in der diese Funktion davon abgehalten wurde, eigenen Code auszuführen, als diese Funktion von der aktuellen Funktion aufgerufen wurde.  Blockierte Zeit in untergeordneten Funktionen, die von der aufgerufenen Funktion aufgerufen wurden, ist nicht eingeschlossen.|  
|**Exklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, der auf die exklusive blockierte Zeit für diese Funktion in diesem Kontext entfällt.|  
|**Exklusive Konflikte**|-   Bei der aktuellen Funktion gibt dies an, wie oft die Funktion davon abgehalten wurde, Code im Funktionstext auszuführen.  Konflikte in Funktionen, die von der Funktion aufgerufen wurden, sind nicht eingeschlossen.<br />-   Bei einer Aufruferfunktion die Anzahl von exklusiven Konflikten der aktuellen Funktion, die aufgetreten sind, als diese Funktion die aktuelle Funktion aufgerufen hat.<br />-   Bei einer aufgerufenen Funktion die Häufigkeit, mit der diese Funktion davon abgehalten wurde, Code im Funktionstext auszuführen, als diese Funktion von der aktuellen Funktion aufgerufen wurde.  Konflikte in Funktionen, die von der aufgerufenen Funktion aufgerufen wurden, sind nicht eingeschlossen.|  
|**Exklusive Konflikte %**|Der Prozentsatz aller Konflikte während der Profilerstellung, der auf exklusive Konflikte für diese Funktion in diesem Kontext entfällt.|  
|**Function Address**|Die Funktionsadresse oder das Token.|  
|**Function Name**|Der vollqualifizierte Name der Funktion.|  
|**Inklusive blockierte Zeit**|-   Bei der aktuellen Funktion die Zeit, in der diese Funktion oder eine der Funktionen, die von dieser Funktion angerufen wurde, vom Ausführen abgehalten wurde.  Blockierte Zeit in Funktionen, die von der aktuellen Funktion aufgerufen wurden, ist eingeschlossen.<br />-   Bei einer Aufruferfunktion ist dies der Anteil der inklusiven blockierten Zeit der aktuellen Funktion, die aufgetreten ist, als die Funktion die aktuelle Funktion aufgerufen hat.<br />-   Bei einer aufgerufenen Funktion die Zeit, in der diese Funktion oder eine der Funktionen, die von der Funktion aufgerufen wurde, davon abgehalten wurde, Code auszuführen, als diese Funktion von der aktuellen Funktion aufgerufen wurde.  Blockierte Zeit in Funktionen, die von der aufgerufenen Funktion aufgerufen wurden, ist eingeschlossen.|  
|**Inklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, der auf die inklusive blockierte Zeit für diese Funktion in diesem Kontext entfällt.|  
|**Inklusive Konflikte**|-   Bei der aktuellen Funktion die Häufigkeit, mit der diese Funktion oder eine der Funktionen, die von der Funktion aufgerufen wurde, vom Ausführen abgehalten wurde.  Konflikte in Funktionen, die von der Funktion aufgerufen wurden, sind eingeschlossen.<br />-   Bei einer Aufruferfunktion die Anzahl von inklusiven Konflikten der aktuellen Funktion, die aufgetreten sind, als diese Funktion die aktuelle Funktion aufgerufen hat.<br />-   Bei einer aufgerufenen Funktion die Häufigkeit, mit der diese Funktion oder eine der Funktionen, die von der Funktion aufgerufen wurde, davon abgehalten wurde, Code auszuführen, als diese Funktion von der aktuellen Funktion aufgerufen wurde.  Konflikte in Funktionen, die von der aufgerufenen Funktion aufgerufen wurden, sind eingeschlossen.|  
|**Inklusive Konflikte %**|Der Prozentsatz aller Konflikte während der Profilerstellung, der auf exklusive Konflikte für diese Funktion in diesem Kontext entfällt.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) des Prozesses, in dem die Konflikte aufgetreten sind.|  
|**Prozessname**|Der Prozessname.|  
|**Name der Stammfunktion**|Der Name der aktuellen Funktion.  Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Sampling](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-instrumentation-data.md)