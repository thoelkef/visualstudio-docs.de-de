---
title: VSPerfMon | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 35
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4a06a6632d62f853eef33cad00ad766e0d1aab87
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776052"
---
# <a name="vsperfmon"></a>VSPerfMon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können das VSPerfMon-Tool verwenden, um Leistungsdaten für eine Anwendung zu sammeln. Das Tool wird typischerweise über „VSPerfCmd.exe“ gestartet. VSPerfMon zeigt zusätzliche Informationen zum Anfügen oder Trennen eines Prozesses an, was bei Verwendung des VSPerfCmd-Tools nicht verfügbar ist. Um diese Informationen anzuzeigen, starten Sie VSPerfMon in einem separaten Fenster. Zum Aufrufen von VSPerfMon verwenden Sie die folgende Syntax:  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 In der folgenden Tabelle werden die Optionen des VSPerfMon-Tools beschrieben:  
  
|Optionen|Beschreibung|  
|-------------|-----------------|  
|**U**|Die umgeleitete Konsolenausgabe wird als Unicode geschrieben.  Dabei muss es sich um die erste angegebene Option handeln.|  
|**OUTPUT:** `<` *Dateiname* `>`|Leitet die Ausgabe zum angegebenen Dateinamen um.|  
|**TRACE**|Startet den Systemmonitor für die instrumentierte Profilerstellung.|  
|**SAMPLE**|Startet den Systemmonitor für die Sampling-Profilerstellung.|  
|**COVERAGE**|Startet den Systemmonitor für die Code Coverage-Sammlung.|  
|**CONCURRENCY**|Startet den Systemmonitor für die Ressourcenkonflikt-Profilerstellung.|  
|**USER:** `[` *Domäne* `\]` *Benutzername*|Ermöglicht dem Client Zugriff auf den Systemmonitor vom angegebenen Konto aus.|  
|**CROSSSESSION**|Ermöglicht die sitzungsübergreifende Profilerstellung.|  
|**COUNTER** `:cfg`|Wenn die Instrumentierungs-Profilerstellungsmethode (TRACE) verwendet wird, wird ein CPU-Indikator angegeben, der an jedem Instrumentierungspunkt gesammelt werden soll. Sie können mehrere Indikatordaten sammeln, indem Sie mehrere Indikatoroptionen angeben.<br /><br /> Verwenden Sie zum Angeben der Indikatordaten (*cfg*) die folgende Syntax:<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName** ist der Name eines Indikators, der durch den VSPerfCmd-Befehl „/QueryCounters“ zurückgegeben wird.<br />-   **Reload** ist das Samplingintervall des Indikatorereignisses. Verwenden Sie *Reload* nicht mit der Instrumentierungsmethode.<br />- Wenn angegeben, ersetzt **FriendlyName** **CounterName** in den Spaltennamen von Berichten der Profilerstellungstools.|  
|**WINCOUNTER** `:path`|Gibt einen Windows-Leistungsindikator an, der in Markierungsdaten enthalten sein soll. `path` ist eine Windows-Leistungsindikator-Zeichenfolge im PDH-Indikatorpfadformat. Beispiel:<br /><br /> \Processor(0)\\% Processor Time<br /><br /> \System\Context Switches/sec|  
|**AUTOMARK** `:n`|Gibt das Zeitintervall (in Millisekunden) zwischen automatischen Markierungen an, wenn Sie /WINCOUNTER verwenden. Wird auf die nächsten 500 ms gerundet.<br /><br /> Verwenden Sie 0 zum Deaktivieren von automatischen Markierungen. (Standard = 500 ms, falls nicht angegeben)|  
  
## <a name="see-also"></a>Siehe auch  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Berichtsansichten für Profilerstellungstools](../profiling/performance-report-views.md)
