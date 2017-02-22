---
title: "CrossSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CrossSession
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **CrossSession**\-Option von VSPerfCmd.exe aktiviert den Profiler zum Sammeln von Daten aus einer Konsolensitzung.  Die **CrossSession**\-Option muss zusammen mit der **Start**\-Option verwendet werden.  
  
 Sie können die Abkürzung **CS** anstelle von **CrossSession** verwenden.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Start:Method /CrossSession [Options]  
```  
  
#### Parameter  
 Kein  
  
## Gültige Optionen  
 Um Profilerstellung in einer anderen Sitzung zu aktivieren, muss die **CrossSession**\-Option mit der **Start**\-Option angegeben werden.  **CrossSession** muss auch in jedem nachfolgenden **VSPerfCmd Attach** und **Detach**\-Befehl angegeben werden.  
  
 **Start:** `Method`  
 Die **Start**\-Option initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.  
  
 **Attach:** *PID*\[**,***PID*\]  
 Startet die Profilerstellung für die angegebenen Prozesse.  
  
 **Detach**\[**:***PID*\[,*PID*\]\]  
 Beendet die Profilerstellung für die angegebenen Prozesse.  
  
## Beispiel  
 In diesem Beispiel wird die **CrossSession**\-Option für das Anfügen an eine Anwendung verwendet, die in einer anderen Konsolensitzung gestartet wurde.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession  
VSPerfCmd.exe /Attach:12345 /CS  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)