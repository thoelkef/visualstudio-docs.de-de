---
title: "Shutdown | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a1e37500-4ad1-4670-9737-3d9a20536386
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Shutdown
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Shutdown**\-Option wartet darauf, dass ein profilierter Prozess endet oder getrennt wird, und deaktiviert den Profiler dann und schließt die Profilerstellungs\-Datendatei.  Die **Shutdown**\-Option muss der letzte Befehl einer Profilerstellungsausführung sein.  
  
 Wenn kein Timeoutparameter angegeben ist, wartet die **Shutdown**\-Option unbegrenzt.  Wenn ein Timeoutparameter angegeben ist, gibt die Option nach der angegebenen Anzahl von Sekunden einen Wert zurück, ohne den Profiler deaktiviert oder die Datendatei geschlossen zu haben.  
  
 Außer der **Shutdown**\-Option dürfen keine anderen Optionen in der Befehlszeile angegeben werden.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Shutdown[:Timeout]  
```  
  
#### Parameter  
 `Timeout`  
 -   \(Optional\) Wenn ein Timeoutparameter angegeben ist, gibt die Option nach der angegebenen Anzahl von Sekunden einen Wert zurück, ohne den Profiler deaktiviert oder die Profilerstellungs\-Datendatei geschlossen zu haben.  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)