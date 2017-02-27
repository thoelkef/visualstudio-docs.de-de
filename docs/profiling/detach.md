---
title: "Detach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9d1b52c-7f28-467d-b1e0-512afc4e46c9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Detach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die VSPerfCmd.exe\-Option **Detach** trennt den Profiler vom angegebenen Prozess oder von allen Prozessen, wenn keine angegeben sind.  Die Profilerstellung muss mit der Samplingmethode initialisiert worden sein.  
  
 Eine Profilerstellung, die mit der **Launch**\-Option oder der **Attach**\-Optionen gestartet wurde, kann mit **Detach** getrennt werden.  Der Profiler kann mit den folgenden **Attach**\-Befehlen erneut angefügt werden.  
  
 Mit **Detach** wird die Profilerstellungs\-Datendatei nicht geschlossen.  Verwenden Sie die **Shutdown**\-Option, um die Profilerstellung zu beenden und die Datendatei zu schließen.  
  
> [!NOTE]
>  Wenn die **Start**\-Option mit der **Crosssession**\-Option angegeben wurde, müssen alle Aufrufe von **VSPerfCmd \/Attach** oder **VSPerfCmd \/Detach** auch **Crosssession** angeben.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Detach[:PIDs|ProcessNames]  
```  
  
#### Parameter  
 `PIDs|ProcessNames`  
 `PID` \- Der numerische Systembezeichner eines oder mehrerer Prozesse.  
  
 `ProcessNames` \- der Name des Prozesses.  Wenn mehrere Instanzen des genannten Prozesses ausgeführt werden, sind die Ergebnisse unvorhersehbar.  
  
 Trennen Sie mehrere Prozesse per Komma voneinander ab.  
  
 Wenn kein Prozess angegeben wird, wird der Profiler von allen profilierten Prozessen getrennt.  
  
## Gültige Optionen  
 Die folgenden **VSPerfCmd**\-Optionen können mit der **Attach**\-Option in einer einzelnen Befehlszeile kombiniert werden.  
  
 **Crosssession**  
 Aktiviert Profilerstellungsanwendungen in anderen Sitzungen als in der Anmeldesitzung.  Erforderlich, wenn die **Start**\-Option mit der **Crosssession**\-Option angegeben wurde.  
  
## Beispiel  
 In diesem Beispiel hält der **Detach**\-Befehl die Profilerstellung an, und der **Shutdown**\-Befehl schließt die Profilerdatendatei.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
;REM Excercise the application  
VSPerfCmd.exe /Detach  
VSPerfCmd.exe /Shutdown  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)