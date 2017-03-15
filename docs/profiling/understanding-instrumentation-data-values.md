---
title: "Grundlagen zu Instrumentationsdatenwerten in Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Instrumentation"
  - "Instrumentationsprofilerstellungs-Methode"
ms.assetid: 2cf94cf9-c317-4a52-bf00-670f1262165e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Grundlagen zu Instrumentationsdatenwerten in Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die *Profilerstellungsmethode Instrumentation* zeichnet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ausführliche Zeitsteuerungsinformationen für die Funktionsaufrufe, die Zeilen und die Anweisungen in der Anwendung mit Profil auf  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Die Instrumentationsmethode wird Code am Beginn und Ende von Zielfunktionen in der profilierten Binärdatei sowie vor und nach jedem Aufruf anderer Funktionen durch diese Funktionen ein.  Im eingefügten Code wird Folgendes aufgezeichnet:  
  
-   Das Intervall zwischen diesem Auflistungsereignis und dem vorherigen.  
  
-   Ob das Betriebssystem während des Intervalls eine Operation ausgeführt hat.  Das Betriebssystem könnte beispielsweise von der Festplatte lesen oder auf die Festplatte schreiben oder zwischen dem Zielthread und einem anderen Thread in einem anderen Prozess wechseln.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Für jedes Intervall rekonstruiert die Profileranalyse die Aufrufliste, die am Ende des Intervalls vorhanden war.  Eine Aufrufliste ist die Liste der Funktionen, die zu einem bestimmten Zeitpunkt auf einem Prozessor aktiv sind.  Nur eine Funktion \(die aktuelle Funktion\) führt Code aus. Die anderen Funktionen sind die Kette von Funktionsaufrufen, die zu dem Aufruf der aktuellen Funktion \(der Aufrufliste\) geführt haben.  
  
 Für jede Funktion in der Aufrufliste fügt die Profileranalyse beim Aufzeichnen des Intervalls das Intervall zu einem oder mehreren von vier Datenwerten für die Funktion hinzu.  Die Analyse fügt das Intervall einem Datenwert für eine Funktion anhand von zwei Kriterien hinzu:  
  
-   Ob das Intervall im Code der Funktion oder in einer *untergeordneten Funktion* \(einer durch die Funktion aufgerufenen Funktion\) aufgetreten ist.  
  
-   Ob ein Betriebssystemereignis im Intervall aufgetreten ist.  
  
 Die Datenwerte für ein Intervall einer Funktion oder eines Datenbereichs sind mit *Verstrichene inklusive Zeit*, *Verstrichene exklusive Zeit*, *Inklusive Anwendungszeit* und *Exklusive Anwendungszeit* benannt.  
  
-   Alle Intervalle einer Funktion werden dem Datenwert Verstrichene inklusive Zeit hinzugefügt.  
  
-   Wenn das Intervall im Code der Funktion und nicht in einer untergeordneten Funktion aufgetreten ist, wird das Intervall dem Datenwert Verstrichene exklusive Zeit der Funktion hinzugefügt.  
  
-   Wenn im Intervall kein Betriebssystemereignis aufgetreten ist, wird das Intervall dem Datenwert Inklusive Anwendungszeit hinzugefügt.  
  
-   Wenn im Intervall kein Betriebssystemereignis aufgetreten ist und das Intervall bei der direkten Ausführung des Funktionscodes, d. h. nicht in einer untergeordneten Funktion, aufgetreten ist, wird das Intervall dem Datenwert Exklusive Anwendungszeit hinzugefügt.  
  
 In den Berichten der Profilerstellungstools werden die Gesamtwerte der Funktionen in der Profilerstellungssitzung sowie die Prozesse, Threads und binären Dateien der Sitzung aggregiert.  
  
## Werte für Verstrichene inklusive Zeit  
 Die Gesamtzeit, die für die Ausführung einer Funktion und deren untergeordneter Funktionen aufgewendet wurde.  
  
 Werte für Verstrichene inklusive Zeit umfassen die Intervalle, die für die direkte Ausführung des Funktionscodes aufgewendet wurden, sowie die Intervalle für die Ausführung der untergeordneten Funktionen der Zielfunktion.  Intervalle der Funktion oder der untergeordneten Funktionen, die Wartezeit für das Betriebssystem umfassen, sind ebenfalls in Werten für Verstrichene inklusive Zeit enthalten.  
  
## Werte für Verstrichene exklusive Zeit  
 Die Zeit, die für die Ausführung einer Funktion aufgewendet wurde, ausschließlich der für untergeordnete Funktionen aufgewendeten Zeit.  
  
 Werte für Verstrichene exklusive Zeit umfassen die Intervalle, die für die direkte Ausführung des Funktionscodes aufgewendet wurden, und zwar unabhängig davon, ob im Intervall ein Betriebssystemereignis eingetreten ist.  Alle für untergeordnete Funktionen, die von der Zielfunktion aufgerufen wurden, aufgewendeten Intervalle sind nicht in Werten für Verstrichene exklusive Zeit enthalten.  
  
## Werte für Inklusive Anwendungszeit  
 Die Zeit, die für die Ausführung einer Funktion und der untergeordneten Funktionen aufgewendet wurde, ausschließlich der für Betriebssystemereignisse aufgewendeten Zeit.  
  
 Werte für Inklusive Anwendungszeit schließen keine Intervalle ein, die Betriebssystemereignisse enthalten.  Werte für Inklusive Anwendungszeit umfassen alle anderen Intervalle, die für Ausführung einer Funktion aufgewendet wurden, und zwar unabhängig davon, ob das Intervall für die direkte Ausführung des Funktionscodes oder für untergeordnete Funktionen der Zielfunktion aufgewendet wurde.  
  
## Werte für Exklusive Anwendungszeit  
 Die Zeit, die für die Ausführung einer Funktion aufgewendet wurde, ausschließlich der für untergeordnete Funktionen und Betriebssystemereignisse aufgewendeten Zeit.  
  
 Werte für Exklusive Anwendungszeit umfassen keine Intervalle, die Betriebssystemereignisse enthalten, oder Intervalle für die Ausführung von durch die Funktion aufgerufenen Funktionen.  Werte für Exklusive Anwendungszeit umfassen nur die Intervalle, die für die direkte Ausführung des Funktionscodes aufgewendet wurden und die kein Betriebssystemereignis enthalten.  
  
## Prozentsatz für Verstrichene inklusive Zeit  
 Der Prozentsatz der Gesamtwerte für Verstrichene inklusive Zeit der Profilerstellungssitzung, die Werte für Verstrichene inklusive Zeit der Funktion, des Modul, des Threads oder Prozesses waren.  
  
 100 \* Funktion Verstrichene inklusive Zeit \/ Sitzung Verstrichene inklusive Zeit  
  
## Prozentsatz für Verstrichene exklusive Zeit  
 Der Prozentsatz der Gesamtwerte für Verstrichene inklusive Zeit der Profilerstellungssitzung, die Werte für Verstrichene exklusive Zeit der Funktion, des Modul, des Threads oder Prozesses waren.  
  
 100 \* Funktion Verstrichene exklusive Zeit \/ Sitzung Verstrichene inklusive Zeit  
  
## Prozentsatz Inklusive Anwendungszeit  
 Der Prozentsatz der Gesamtwerte für Inklusive Anwendungszeit der Profilerstellungssitzung, die Werte für Inklusive Anwendungszeit der Funktion, des Modul, des Threads oder Prozesses waren.  
  
 100 \* Funktion Inklusive Anwendungszeit \/ Sitzung Inklusive Anwendungszeit  
  
## Prozentsatz Exklusive Anwendungszeit  
 Der Prozentsatz der Gesamtwerte für Inklusive Anwendungszeit der Profilerstellungssitzung, die Intervalle für Exklusive Anwendungszeit der Funktion, des Modul, des Threads oder Prozesses waren.  
  
 100 \* Funktion Exklusive Anwendungszeit \/ Sitzung Inklusive Anwendungszeit  
  
## Siehe auch  
 [Analysieren der durch Profilerstellungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)   
 [Gewusst wie: Auswählen von Sammlungsmethoden](../profiling/how-to-choose-collection-methods.md)