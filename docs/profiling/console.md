---
title: "Konsole | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e825ba66-1383-46ad-8712-396bc9c14036
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Konsole
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Console**\-Option von VSPerfCmd.exe startet die angegebene Anwendung in einem neuen Eingabeaufforderungsfenster.  **Console** kann nur in Verbindung mit der **Launch**\-Option von VSPerfCmd verwendet werden.  Wenn es sich bei der Anwendung nicht um eine Befehlszeilenanwendung handelt, hat die **Console**\-Option keine Auswirkungen.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Launch:AppName /Console  
```  
  
#### Parameter  
 Kein  
  
## Erforderliche Optionen  
 Die **Console**\-Option kann nur in einer Befehlszeile angegeben werden, die auch die **Launch**\-Option enthält.  
  
 **Launch:** `AppName`  
 Startet den Profiler und die mit `AppName` angegebene Anwendung.  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)