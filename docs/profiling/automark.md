---
title: "AutoMark | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4de965e-0364-4f78-9936-1f509e85df74
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# AutoMark
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Option **AutoMark** gibt die Anzahl von Millisekunden zwischen dem Erfassen von Leistungsindikatorereignissen für Windows\-Software an.  Windows\-Leistungsindikatoren werden in der **WinCounter**\-Option angegeben.  
  
 Es kann nur eine **AutoMark**\-Option in der Befehlszeile angegeben werden.  Beachten Sie, dass das **WinCounter**\-Samplingintervall, das durch **AutoMark** festgelegt wird, vom Hauptsamplingintervall unabhängig ist.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Start:Method /WinCounter:Path /AutoMark:Milliseconds  
```  
  
#### Parameter  
 `Milliseconds`  
 Gibt die Anzahl von Millisekunden zwischen dem Erfassen von Windows\-Leistungsindikatorereignissen an.  
  
## Erforderliche Optionen  
 **WinCounter:** `Path`  
 Gibt den zu erfassenden Windows\-Leistungsindikator an.  Wenn Sie die Instrumentationsmethode verwenden, können mehrere Windows\-Leistungsindikatoren angegeben werden.  Wenn Sie die Samplingmethode verwenden, kann nur ein Softwareleistungsindikator angegeben werden.  Die **WinCounter**\-Option muss in einer Befehlszeile angegeben werden, die die **Start**\-Option enthält.  
  
## Beispiel  
 In diesem Beispiel wird ein Samplingintervall von 1000 Millisekunden für zwei Windows\-Leistungsindikatoren festgelegt.  
  
```  
VSPerfCmd.exe /Start:Trace /Output:TestApp.exe.vsp /WinCounter:"\Process(*)\% Processor Time" /WinCounter:"\ASP.NET\Pages/sec" /AutoMark:1000  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)