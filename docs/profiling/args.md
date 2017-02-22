---
title: "Args | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Args
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Args**\-Option von "VSPerfCmd.exe" gibt eine Liste mit Argumenten an, die an die Zielanwendung des **Launch**\-Unterbefehls übergeben werden.  
  
 **Args** kann nur verwendet werden, wenn auch **Launch** in der Befehlszeile angegeben wird.  **Args** ist optional, wenn **Launch** angegeben ist.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]  
```  
  
#### Parameter  
 `Arguments`  
 Eine Liste der Argumente für die Zielanwendung des **Launch**\-Befehls.  
  
## Erforderliche Optionen  
 **Launch:** `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
## Beispiel  
 Das folgende Beispiel übergibt Argumente mithilfe der **Args**\-Option an TestApp.exe.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)