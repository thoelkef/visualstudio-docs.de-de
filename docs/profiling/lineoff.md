---
title: "LineOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# LineOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Standardmäßig sammelt der Profiler bei Verwendung der Samplingprofilerstellungsmethode die Quellcodezeilennummer und die Zeilennummer\-Offsetdaten.  Die VSPerfCmd **LineOff**\-Option deaktiviert die Datensammlung der Zeilennummer, wenn VSPerfCmd verwendet wird, um die Anwendung zu starten.  Profilerstellungsdaten werden auf der Funktionsebene erfasst, wenn **LineOff** angegeben wird.  
  
 Sie können **LineOff** nur mit der **Launch**\-Option verwenden, und nur, wenn der Profiler mithilfe der **Start**:**Sample**\-Option für Sampling initialisiert wurde.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Launch:AppName /LineOff [Options]  
```  
  
#### Parameter  
 Kein  
  
## Erforderliche Optionen  
 Die **LineOff**\-Option kann nur in einer Befehlszeile verwendet werden, die auch die **Launch**\-Option enthält.  
  
 **Launch:** `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
## Beispiel  
 In diesem Beispiel werden die Anwendung und der Profiler gestartet und Sampling auf Zeilenebene deaktiviert.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /LineOff  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)