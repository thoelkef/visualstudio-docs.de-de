---
title: "VSPerfMon | Microsoft Docs"
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
  - "VSPerfMon-Tool"
  - "Befehlszeile, Tools"
  - "Befehlszeilentools, VSPerfMon-Tool"
  - "Daten [Visual Studio ALM] VSPerfMon-Tool"
  - "Leistungsdaten, VSPerfMon-Tool"
  - "Leistungstools, VSPerfMon-Tool"
  - "Profilerstellungstools, VSPerfCmd"
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfMon
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können das Tool VSPerfMon verwenden, um Leistungsdaten für eine Anwendung zu sammeln. In der Regel wird dieses Tool von VSPerfCmd.exe gestartet.  VSPerfMon zeigt zusätzliche Informationen zum Anfügen und Trennen von Prozessen an, die mit dem Tool VSPerfCmd nicht verfügbar sind.  Öffnen Sie VSPerfMon in einem separaten Fenster, um diese Informationen anzuzeigen.  Rufen Sie VSPerfMon mithilfe der folgenden Syntax auf:  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 In der folgenden Tabelle werden die Optionen des VSPerfMon\-Tools beschrieben:  
  
|Optionen|**Beschreibung**|  
|--------------|----------------------|  
|**U**|Umgeleitete Konsolenausgaben sind als Unicode geschrieben.  Dies muss die erste angegebene Option sein.|  
|**OUTPUT:** `<` *file name* `>`|Leitet die Ausgabe in die Datei mit dem angegebenen Dateinamen um.|  
|**TRACE**|Startet Leistungsmonitor für instrumentierte Profilerstellung.|  
|**SAMPLE**|Startet Leistungsmonitor für Sampling\-Profilerstellung.|  
|**COVERAGE**|Startet Leistungsmonitor für Codeabdeckungsauflistung.|  
|**CONCURRENCY**|Stellt den Systemmonitor für Ressourcenkonflikt\-Profilerstellung an.|  
|**USER:** `[` *domain* `\]` *username*|Ermöglicht Clientzugriff auf den Leistungsmonitor über das angegebene Konto.|  
|**CROSSSESSION**|Aktiviert die sitzungsübergreifende Profilerstellung.|  
|**COUNTER** `:cfg`|Wenn die Instrumentationsmethode \(TRACE\) für die Profilerstellung verwendet wird, gibt diese einen CPU\-Indikator an, der an jedem Instrumentationspunkt aufzulisten ist.  Sie können mehrere Indikatordaten sammeln, indem Sie mehrere Indikatoroptionen angeben.<br /><br /> Verwenden Sie die folgende Syntax, um den Wert \(*cfg*\) Daten anzugeben:<br /><br /> CounterName\[**,**Reload\[,FriendlyName\]\]<br /><br /> -   CounterName ist der Name eines Indikators, der durch den VSPerfCmd \/QueryCounters\-Befehl zurückgegeben wird.<br />-   Reload gibt das Samplingintervall des Zählerereignisses an.  Verwenden Sie nicht *Reload* mit der Instrumentationsmethode.<br />-   Wenn angegeben, ersetzt FriendlyName CounterName in den Berichtsspaltennamen der Profilerstellungstools.|  
|**WINCOUNTER** `:path`|Gibt einen Windows\-Leistungsindikator an, der in die Markierungsdaten aufgenommen werden soll.  `path` ist eine Windows\-Leistungsindikator\-Zeichenfolge im PDH\-Format für Indikatorpfade.  Beispiel:<br /><br /> \\Processor\(0\)\\% Processor Time<br /><br /> \\System\\Context Switches\/sec|  
|**AUTOMARK** `:n`|Gibt das Zeitintervall \(in Millisekunden\) zwischen automatischen Markierungen an, wenn \/WINCOUNTER verwendet wird.  Wird auf die nächsten 500 ms gerundet.<br /><br /> Mit 0 deaktivieren Sie automatische Markierungen. \(Standard\=500 ms, falls nicht angegeben\)|  
  
## Siehe auch  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Berichtsansichten für Profilerstellungstools](../profiling/performance-report-views.md)