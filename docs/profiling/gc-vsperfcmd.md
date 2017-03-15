---
title: "GC (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# GC (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch die **GC**\-Option wird die Sammlung von Daten zur .NET Framework\-Speicherbelegung und zur Objektlebensdauer aktiviert.  Die **GC**\-Option kann nur bei der Samplingprofilerstellungsmethode und nur der **Launch**\-Option verwendet werden.  
  
 Wenn Sie die **GC**\-Option verwenden, ist der VSPerfClrEnv\-**\/sampleon**\-Befehl nicht erforderlich.  
  
 Wenn keine Parameter angegeben werden, oder wenn der **Allocation**\-Parameter angegeben wird, werden nur .NET Framework\-Speicherbelegungsdaten erfasst.  Wenn der **Lifetime**\-Parameter angegeben wird, werden sowohl Daten für die .NET Framework\-Speicherbelegung als auch für die .NET Framework\-Objektlebensdauer gesammelt.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### Parameter  
 **Allocation**  
 Standard  Erfasst .NET Framework\-Speicherbelegungsdaten.  
  
 **Lifetime**  
 Erfasst sowohl .NET\-Speicherbelegungsinformationen als auch Daten zur .NET Framework\-Objektlebensdauer.  
  
## Erforderliche Optionen  
 Die **GC**\-Option kann nur in Verbindung mit der **Launch**\-Option verwendet werden.  
  
 **Launch:** `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Anwendung gestartet, und es werden .NET Framework\-Speicherbelegungsdaten erfasst.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)