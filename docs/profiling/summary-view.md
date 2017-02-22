---
title: "Zusammenfassungsansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.summary"
helpviewer_keywords: 
  - "Leistungsberichte, Zusammenfassungsansicht"
  - "Berichte für Profilerstellungstools, Zusammenfassungsansicht"
  - "Profilerstellungstools, Zusammenfassungsansicht"
  - "Zusammenfassungsansicht"
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zusammenfassungsansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Zusammenfassungsansicht zeigt Informationen zu den leistungsintensivsten Funktionen oder Objekten während einer Profilerstellung an.  Diese Ansicht stellt ein Zeitachsendiagramm und mindestens zwei Listen der teuersten Funktionen oder Objekte auf Grundlage der Leistungsmetrik der Profilerstellungsmethode bereit.  Die Daten in dieser Ansicht sind von der verwendeten Profilerstellungsmethode \(Sampling, Instrumentation oder Gleichzeitigkeit\) und davon abhängig, ob die .NET\-Speicherbelegung gesammelt wurde.  
  
 Für alle Zusammenfassungsansichten außer der Zusammenfassungsansicht für Parallelitätsdaten zeigt das Zeitachsendiagramm in der Zusammenfassungsansicht die CPU\-Auslastung \(Prozessorauslastung\) der profilierten Anwendung über den Zeitraum der Profilerstellung an.  
  
-   Wenn Sie auf dem Diagramm ein Zeitsegment angeben, können Sie Daten für dieses Segment neu analysieren oder die Zeitachsenanzeige vergrößern, um das angegebene Segment anzuzeigen.  Weitere Informationen finden Sie unter [Gewusst wie: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
-   Sie können auf eine Funktion in einer Zusammenfassungsansichtsliste klicken, um die Funktionsdetailansicht für die Funktion zu öffnen.  Sie können auch mit der rechten Maustaste auf die Funktion klicken, um andere Ansichtsoptionen anzuzeigen.  
  
-   Um die Anzahl der in den Zusammenfassungsansichtslisten aufgeführten Elementen zu ändern, öffnen Sie das Menü **Extras**, zeigen Sie auf **Optionen**, und klicken Sie dann auf **Leistungstools**.  Ändern Sie unter **Allgemeine Einstellungen** die Einstellung **Anzahl der Funktionen in der Zusammenfassungsansicht**.  
  
## Benachrichtigungslinks  
 Sie können in der Benachrichtigungsliste auf Links klicken, um Anzeigeoptionen für den Bericht festzulegen.  Die Liste befindet sich rechts neben dem Zeitachsendiagramm.  
  
|||  
|-|-|  
|**Anzeigen von nicht benutzerbezogenem Code**<br /><br /> **Nur eigenen Code anzeigen**|Nicht verfügbar für systemeigenen Code oder für Profilerstellungsdaten, die mit der Instrumentationsmethode gesammelt wurden.  chaltet zwischen der ausschließlichen Anzeige von Daten aus Benutzercode \(**Nur eigenen Code anzeigen**\) und der Anzeige des gesamten Codes \(einschließlich Systemcode, **Nichtbenutzercode anzeigen**\) um.  Standardmäßig sind Daten auf Benutzercode beschränkt.  Informationen zum Ändern der Einstellung finden Sie unter [Gewusst wie: Filtern der Berichtsansichten, um nur eigenen Code anzuzeigen](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Leitfaden anzeigen**|Zeigt Leistungsregelwarnungen im Fenster **Fehlerliste** an.  Weitere Informationen finden Sie unter [Verwenden von Leistungsregeln zur Analyse von Daten](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## Bericht  
 Sie können in der Berichtsliste auf Links klicken, um andere Ansichten zu öffnen und den Bericht zu vergleichen, zu speichern oder zu filtern.  Die Liste befindet sich rechts neben dem Zeitachsendiagramm.  
  
|||  
|-|-|  
|**Anzeigen von abgeschnittener Aufrufstruktur**|Zeigt die teuersten Ausführungspfade in der Aufrufstrukturansicht an.  Weitere Informationen finden Sie unter [Aufrufstrukturansicht](../profiling/call-tree-view.md).|  
|**Anzeigen von Direktleitungen**|Nicht verfügbar für Profilerstellungsdaten, die mithilfe der Instrumentationsmethode erfasst wurden.  Zeigt die teuersten Quellcodezeilen in der Zeilenansicht an.  Weitere Informationen finden Sie unter [Zeilenansicht](../profiling/lines-view.md).|  
|**Vergleichen von Berichten**|Zeigt das Dialogfeld **Analysedateien für Vergleich auswählen** an, wo Sie eine andere Profilerstellungs\-Datendatei angeben können, die mit der aktuellen Datei verglichen werden soll.  Weitere Informationen finden Sie unter [Vergleichen der durch Profilerstellungstools erstellten Datendateien](../profiling/comparing-performance-data-files.md).|  
|**Berichtdaten exportieren**|Zeigt das Dialogfeld **Bericht exportieren** an, in dem Sie eine oder mehrere Berichtansichten zum Speichern als durch Trennzeichen getrennten Wert \(.csv\) oder XML\-Dateien angeben können.  Weitere Informationen finden Sie unter [How to: Export Profiling Tools Reports](http://msdn.microsoft.com/de-de/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Speichern des analysierten Berichts**|Speichert die aktuelle Profilerstellungsdatendatei als VSPS\-Datei, die in der Schnittstelle für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] schneller geöffnet wird.  Weitere Informationen finden Sie unter [How to: Save Analyzed Profiling Data Files](http://msdn.microsoft.com/de-de/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtern von Berichtsdaten**|Zeigt den Berichtsfilterbereich für Profilerstellung an, in dem Sie Kriterien angeben können, um die Daten in der Berichtsansicht einzuschränken.  Weitere Informationen finden Sie unter [Filter für die Berichtsansicht der Profilerstellungstools](../profiling/performance-report-view-filter.md)|  
|**Vollbild umschalten**|Schaltet den Vollbildmodus für die Berichtsansicht um.|  
  
## Siehe auch  
 [Zusammenfassungsansicht](../profiling/summary-view-sampling-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-instrumentation-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-dotnet-memory-data.md)