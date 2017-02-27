---
title: "QueryCounters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8059d4b2-af61-4a47-a6c2-8da5c0741c74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# QueryCounters
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **QueryCounters**\-Option führt die CPU \(Hardware\)\-Leistungsindikatoren auf, die auf dem Computer verfügbar sind.  
  
 **QueryCounters** muss die einzige Option in der Befehlszeile sein.  
  
## Syntax  
  
```  
VSPerfCmd.exe /QueryCounters  
```  
  
#### Parameter  
 Kein  
  
## Hinweise  
 Wenn Sie die Instrumentationsmethode verwenden, kann der Profiler die Werte von einem oder mehreren CPU\-Leistungsindikatoren für jedes Datensammlungsereignis sammeln.  Wenn Sie die Samplingmethode bei der Profilerstellung verwenden, können Sie ein Leistungsindikatorereignis und die Anzahl der auftretenden Ereignisse angeben, die als Samplingintervall verwendet werden sollen.  
  
 Andere Prozessoren stellen andere CPU\-Leistungsindikatoren zur Verfügung.  Der Profiler definiert einen Satz von generischen Leistungsindikatoren, der auf fast allen Prozessoren verwendet werden kann.  Die **QueryCounters**\-Option führt die Namen der generischen Leistungsindikatoren und die Namen der Leistungsindikatoren, die für den Prozessor spezifisch sind, auf.  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)