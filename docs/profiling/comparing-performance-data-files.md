---
title: "Vergleichen der durch Profilerstellungstools erstellten Datendateien | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Vergleichen der durch Profilerstellungstools erstellten Berichtdateien"
  - "Berichte für Profilerstellungstools, Vergleichen"
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Vergleichen der durch Profilerstellungstools erstellten Datendateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der Funktion der Profilerstellungstools zum Vergleichen von Datendateien können Sie zwei Berichtsdateien \(VSP\- oder VSPS\-Dateien\) auswählen und einen Bericht generieren, in dem Unterschiede, Leistungsabfälle und Verbesserungen zwischen beiden Profilerstellungssitzungen angezeigt werden.  
  
 Die Ergebnisse der Analyse in einer Profilerstellungs\-Datendatei werden mithilfe eines Vergleichsberichts von Datendateien der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools mit den Ergebnissen einer Baselineanalyse in einer anderen Datendatei verglichen.  Beide Datendateien müssen mit derselben Profilerstellungsmethode generiert worden sein.  Der Bericht über die Vergleichsanalysen wird als VSPS\-Datei gespeichert.  
  
 Der Vergleichsbericht zeigt eine Tabellenansicht der geänderten Daten.  In der Tabelle wird das Delta bzw. die Abweichung von der Baseline dargestellt.  Zur Berechnung der Differenz wird der Unterschied zwischen dem alten Wert, dem Baselinewert und dem Ergebniswert aus der neuen Analyse ermittelt.  
  
 Vergleiche der Profilerdaten können auf den Funktionen im Code, den Modulen in der Anwendung, Zeilen, Anweisungszeigern \(IPs\) und Typen basieren.  
  
 Die für Vergleiche verfügbaren Profilerstellungsdaten umfassen die in den Spalten angezeigten Informationen.  Definitionen dieser Spaltennamen finden Sie unter [Berichtsansichten für Profilerstellungstools](../profiling/performance-report-views.md).  
  
 Ein Schwellenwert kann festgelegt werden, um Störungen zu reduzieren und um in der Vergleichstabelle alle Datenzeilen herauszufiltern, die einen bestimmten Differenzwert nicht übersteigen.  
  
## In diesem Abschnitt  
 [Gewusst wie: Vergleichen der Profilerdatendateien](../profiling/how-to-compare-performance-data-files.md)