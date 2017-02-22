---
title: "Gewusst wie: Sammeln von Samplingdaten auf Zeilenebene | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Leistungstools, Sampling auf Zeilenebene"
ms.assetid: 44803aad-dd39-4c2e-9209-d35185d44983
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Sammeln von Samplingdaten auf Zeilenebene
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch das Sampling auf Zeilenebene stellt der Profiler fest, an welcher Stelle im Code einer rechenintensiven Funktion, z. B. einer Funktion mit hohem Maß an exklusiven Samplings, die meiste Prozessorzeit aufgewendet wird.  
  
## Übersicht  
 Beim Sampling auf Zeilenebene durchläuft der Profiler die Programmaufrufliste in bestimmten Abständen und aggregiert die Ergebnisse.  Diese Ergebnisse zeigen an, welche Anweisungen vom Prozessor zum Zeitpunkt des Samplings ausgeführt wurden.  Die über exklusive Samplings erfassten Daten werden anschließend analysiert, um die Codezeilen und Anweisungszeiger \(IP\) zu ermitteln.  
  
 Das Sampling auf Zeilenebene funktioniert sowohl mit verwaltetem als auch mit systemeigenem Code.  Zu den Leistungsberichten, in denen diese Daten angezeigt werden, gehören die Zeilenansicht und die Modulansicht.  
  
 Informationen zu Zeichenanfang und Zeichenende sind für systemeigenen Code nicht verfügbar.  Bei mehrzeiligen Anweisungen sind Informationen zum Zeilenanfang für systemeigenen Code nicht verfügbar, sondern nur Informationen zum Zeilenende.  
  
### Verfügbare Daten  
 Für das Sampling auf Zeilenebene sind folgende Daten verfügbar:  
  
-   Funktionsname.  
  
-   Funktionsadresse.  
  
-   Zeilenanfang – Zeilennummer des Samplingcodes.  
  
-   Zeilenende – Nummer der End\-Quellcodezeile.  Diese ist normalerweise identisch mit den "Zeilenanfangs"\-Daten, außer in dem Fall, in dem sich eine Programmanweisung über mehrere Quellcodezeilen erstreckt.  
  
-   Zeichenanfang – Anfangsspalte des Aggregatsamplings.  Dies ist im Allgemeinen 0, außer wenn eine einzelne Zeile mehrere Programmanweisungen enthält.  
  
-   Zeichenende – Endspalte des Aggregatsamplings.  
  
-   IP – Adresse, an der Aggregatsampling durchgeführt wurde \(nur IP\-Ansicht\).  
  
 Wenn eine Funktion über Statistikdaten auf Zeilenebene verfügt, werden die Statistikdaten in der **Modulansicht** unter den einzelnen Funktionen geschachtelt.  Zusätzlich werden Statistikdaten auf IP\-Ebene unter jeder dargestellten Zeile geschachtelt.  
  
### Deaktivieren des Samplings auf Zeilenebene für verwalteten Code  
 Das Sampling auf Zeilenebene ist standardmäßig aktiviert.  Sie können die Datenerfassung auf Zeilenebene für verwalteten Code deaktivieren, indem Sie einen der folgenden Schritte ausführen:  
  
-   Geben Sie vor der Profilerstellung VSPerfCLREnv \/samplelineoff ein.  Dies gilt sowohl für Anwendungen als auch für Dienste.  
  
     – oder –  
  
-   Wenn Sie eine Anwendung starten, geben Sie VSPerfCmd \/lineoff \<weitere Argumente\>ein.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)   
 [Analysieren der durch Profilerstellungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)