---
title: "User (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee1a478e-374d-4f30-ae28-d260b9d4723a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# User (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **User**\-Option gibt die Domäne und den Benutzernamen des Kontos an, das den profilierten Prozess besitzt.  Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.  
  
 Die **User**\-Option kann nur in einer Befehlszeile angegeben werden, die auch die **Start**\-Option enthält.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName /User:[Domain\]UserName [Options]  
```  
  
#### Parameter  
 `Domain`  
 Der Name der Benutzerdomäne.  
  
 `UserName`  
 Der Name des Benutzers.  
  
## Erforderliche Optionen  
 Die **User**\-Option kann nur in Verbindung mit der **Start**\-Option  verwendet werden.  
  
 **Start:** `Method`  
 Initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.  
  
## Beispiel  
 Das folgende Beispiel veranschaulicht die Verwendung der **User**\-Option.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /User:SYSTEM  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)