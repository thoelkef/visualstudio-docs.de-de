---
title: "Ausgabe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5e286e61-4548-42cf-a635-e608c5edbe2b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Ausgabe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Output**\-Option gibt den Namen der Profilerstellungs\-Datendatei für die Leistungssitzung an.  **Output** muss zusammen mit der **Start**\-Option verwendet werden.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Parameter  
 `FileName`  
 Der Name der Datendatei.  Es werden vollständige und partielle Pfade angenommen.  Wenn kein Pfad angegeben ist, wird die Datei im aktuellen Verzeichnis erstellt.  
  
## Erforderliche Optionen  
 Die **Output**\-Option muss zusammen mit der **Start**\-Option verwendet werden.  
  
 **Start:** `Method`  
 Gibt den Ausgabedateinamen an.  
  
## Beispiel  
 Im folgenden Beispiel wird die Profilerstellungs\-Datendatei im aktuellen Verzeichnis erstellt.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)