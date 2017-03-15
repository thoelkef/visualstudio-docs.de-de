---
title: "Z&#228;hler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aa4b4cdb-e6ea-433a-9579-56f3785e1385
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Z&#228;hler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der **Counter**\-Option werden Daten von Prozessor\-\(Hardware\-\)Leistungsindikatoren erfasst.  
  
-   Wenn Sie die Samplingprofilerstellungsmethode verwenden, gibt **Counter** den Chipleistungsindikator und die Anzahl der Leistungsindikatorereignisse an, die als Samplingintervall verwendet werden sollen.  Beim Verwenden von Sampling können Sie nur einen Leistungsindikator angeben.  
  
-   Wenn Sie die Instrumentations\-Profilerstellungsmethode verwenden, wird die Anzahl von Leistungsindikatorereignissen, die im Intervall zwischen den vorherigen und aktuellen Auflistungsereignissen aufgetreten sind, als separate Felder in Profilerberichten aufgeführt.  Beim Verwenden der Instrumentation können mehrere **Counter**\-Optionen angegeben werden.  
  
 Jeder Prozessortyp hat einen eigenen Satz von Hardwareleistungsindikatoren.  Der Profiler definiert einen Satz von generischen Leistungsindikatoren, der fast allen Prozessoren gemeinsam sind.  Um die generischen und prozessorspezifischen Leistungsindikatoren auf dem Computer aufzuführen, verwenden Sie den **QueryCounters**\-Befehl von VSPerfCmd.  
  
## Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName | /Attach PID} /Counter:Name[,Reload[,FriendlyName]] [Options]  
```  
  
```  
VSPerfCmd.exe /Start:Method /Counter:Name[,Reload[,FriendlyName]] [/Counter:Name[,Reload[,FriendlyName]]] [Options]  
```  
  
#### Parameter  
 `Name`  
 Der Name des Indikators.  Verwenden Sie die **\/QueryCounters**\-Option von VSPerfCmd.exe, um die Namen verfügbarer Leistungsindikatoren auf dem Computer aufzuführen.  
  
 `Reload`  
 Die Anzahl der Leistungsindikatorereignisse im Samplingintervall.  Verwenden Sie den Parameter nicht mit der Instrumentationsmethode.  
  
 `FriendlyName`  
 \(Optional\) Die Zeichenfolge, die anstelle von `Name` in den Spaltenheadern von Profilerberichten und Ansichten verwendet werden soll.  
  
## Erforderliche Optionen  
 Die Counter\-Option kann nur mit einer der folgenden Optionen verwendet werden:  
  
 **Start:** `Trace`  
 Initialisiert den Profiler, damit er die Instrumentationsmethode verwenden kann.  
  
 **Launch:** `AppName`  
 Startet die angegebene Anwendung und den Profiler.  Der Profiler muss initialisiert werden, damit er die Samplingmethode verwenden kann.  
  
 **Attach:** `PID`  
 Startet den Profiler und fügt ihn an den Prozess an, der von der Prozess\-ID angegeben wird.  Der Profiler muss initialisiert werden, damit er die Samplingmethode verwenden kann.  
  
## Beispiel  
 Im Samplingmethodenbeispiel wird veranschaulicht, wie ein Sampling für eine Anwendung bei jedem 1000. Vorkommen des generischen Profilerleistungsindikators "NonHaltedCycles" ausgeführt wird.  
  
 Im Instrumentationsmethodenbeispiel wird veranschaulicht, wie der Profiler initialisiert wird, um L2InstructionFetches\-Leistungsindikatorereignisse zu sammeln.  Der L2InstructionFetches\-Leistungsindikatorname ist für den Prozessor spezifisch.  
  
```  
; Sample Method Example  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Counter:NonHaltedCycles,1000,"Non-Halted Cycles"  
  
;INSTRUMENTATION METHOD EXAMPLE  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /Counter:L2InstructionFetches,,"L2 Cache Instruction Fetches"  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)