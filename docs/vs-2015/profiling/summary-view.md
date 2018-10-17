---
title: Zusammenfassungsansicht | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 242250476a55ce33344863003a90d9c829eaea1a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301534"
---
# <a name="summary-view"></a>Zusammenfassungsansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Zusammenfassungsansicht zeigt Informationen über die leistungsintensivsten Funktionen oder Objekte in einem Profilerstellungslauf an. In dieser Ansicht wird anhand der Leistungsmetriken der Profilerstellungsmethode ein Zeitachsendiagramm und mindestens zwei Listen mit den leistungsintensivsten Funktionen oder Objekten dargestellt. Die Daten in dieser Ansicht sind von der verwendeten Profilerstellungsmethode abhängig (Sampling, Instrumentierung oder Parallelität) und davon, ob die .NET-Speicherreservierung erfasst wurde.  
  
 Das Zeitachsendiagramm in der Zusammenfassungsansicht zeigt für alle Zusammenfassungsansichten, außer der der Parallelitätsdaten, die Auslastung des Prozessors (CPU) während der Profilerstellung durch die profilierte Anwendung an.  
  
-   Wenn Sie im Diagramm einen Zeitabschnitt angeben, können Sie die Daten für diesen Abschnitt erneut analysieren oder die Zeitachsenanzeige für diesen Abschnitt vergrößern. Weitere Informationen finden Sie unter [Vorgehensweise: Filtern von Berichtsansichten aus der Zeitachsenübersicht.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
-   Sie können in einer Zusammenfassungsansichtsliste auf eine Funktion klicken, um die Ansicht „Funktionsdetails“ für die Funktion anzuzeigen. Sie können ebenfalls mit der rechten Maustaste auf die Funktion für andere Ansichtsoptionen klicken.  
  
-   Öffnen Sie das Menü **Extras**, zeigen Sie auf **Optionen**, und klicken Sie auf **Leistungstools**, um die Anzahl der Elemente zu verändern, die in der Zusammenfassungsansicht angezeigt werden. Ändern Sie unter **Allgemeine Einstellungen** die Einstellung **Anzahl der Funktionen in der Zusammenfassungsansicht**.  
  
## <a name="notifications-links"></a>Benachrichtigungslinks  
 Sie können auf Links in der Benachrichtigungsliste klicken, um Anzeigeoptionen für den Bericht festzulegen. Sie finden die Liste rechts neben dem Zeitachsendiagramm.  
  
|||  
|-|-|  
|**Show Non-User Code** (Nicht benutzerseitigen Code anzeigen)<br /><br /> **Nur eigenen Code anzeigen**|Nicht verfügbar für nativen Code oder Profilerstellungsdaten, die über die Instrumentierungsmethode erfasst wurden. Schaltet zwischen dem Anzeigen von Daten aus dem Benutzercode (**Nur eigenen Code anzeigen**) und dem Anzeigen von Daten aus dem gesamten Code um, einschließlich des Systemcodes (**Show Non-User Code** (Nicht benutzerseitigen Code anzeigen)). Standardmäßig sind die Daten auf den Benutzercode beschränkt. Informationen zum Ändern der Einstellungen finden Sie unter [Vorgehensweise: Filtern der Berichtsansichten der Profilerstellungstools, um nur eigenen Code anzuzeigen](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Leitfaden anzeigen**|Zeigt Warnungen für Leistungsregeln im Fenster **Fehlerliste** an. Weitere Informationen finden Sie unter [Verwenden von Leistungsregeln zur Analyse von Daten.](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## <a name="report"></a>Bericht  
 Sie können auf Links in der Berichtsliste klicken, um verschiedene Ansichten zu öffnen und den Bericht zu vergleichen, speichern oder zu filtern. Sie finden die Liste rechts neben dem Zeitachsendiagramm.  
  
|||  
|-|-|  
|**Gekürzte Aufrufstruktur anzeigen**|Zeigt die leistungsintensivsten Ausführungspfade in der Aufrufstrukturansicht an. Weitere Informationen finden Sie unter [Aufrufstrukturansicht](../profiling/call-tree-view.md).|  
|**Langsamste Zeile anzeigen**|Nicht verfügbar für Profilerstellungsdaten, die über die Instrumentierungsmethode erfasst wurden. Zeigt die leistungsintensivsten Quellcodezeilen in der Zeilenansicht an. Weitere Informationen finden Sie unter [Zeilenansicht](../profiling/lines-view.md).|  
|**Berichte vergleichen**|Zeigt das Dialogfeld **Analysedateien für Vergleich auswählen** an, in dem Sie eine andere Profilerstellungs-Datendatei angeben können, um einen Vergleich mit der aktuellen Datei zu ziehen. Weitere Informationen finden Sie unter [Vergleichen von Leistungsdatendateien](../profiling/comparing-performance-data-files.md).|  
|**Berichtsdaten exportieren**|Zeigt das Dialogfeld **Exportbericht** an, in dem Sie mindestens eine Berichtsansicht angeben können, die als durch Trennzeichen getrennte (CSV) oder XML-Datei gespeichert werden soll. Weitere Informationen finden Sie unter [How to: Export Profiling Tools Reports (Vorgehensweise: Exportieren von Berichten von Profilerstellungstools).](http://msdn.microsoft.com/en-us/174b5bd3-df9b-4fd4-88d4-76032ab90451)|  
|**Analysierten Bericht speichern**|Speichert die aktuelle Profilerstellungsdatendatei als eine VSPS-Datei, die in der Schnittstelle für [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] schneller geöffnet wird. Weitere Informationen finden Sie unter [How to: Save Analyzed Profiling Data Files (Vorgehensweise: Speichern von analysierten Profilerstellungsdatendateien)](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Berichtsdaten filtern**|Zeigt den Filterbereich des Profilerstellungsberichts an, in dem Sie Kriterien für die Einschränkung der Daten in der Berichtsansicht bestimmen können. Weitere Informationen finden Sie unter [Filter für die Leistungsberichtsansicht](../profiling/performance-report-view-filter.md).|  
|**Vollbild umschalten**|Schaltet den Vollbildmodus für die Berichtsansicht ein bzw. aus.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zusammenfassungsansicht](../profiling/summary-view-sampling-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-instrumentation-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-dotnet-memory-data.md)



