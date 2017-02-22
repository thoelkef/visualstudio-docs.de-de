---
title: "GlobalOn und GlobalOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 24b0ed68-d19e-473e-9af3-252c11d82bcf
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GlobalOn und GlobalOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit den Optionen **GlobalOff** und **GlobalOn** von "VSPerfCmd.exe" wird die Profilerstellung für alle Prozesse und Threads in einer Profilerstellungssitzung über die Befehlszeile angehalten und wieder fortgeführt.  
  
 Sie können **GlobalOn** und **GlobalOff** als einzige Optionen in einer VSPerfCmd.exe\-Befehlszeile angeben oder sie in Befehlszeilen aufnehmen, die auch die Optionen **Start**, **Launch** oder **Attach** enthalten.  
  
 **GlobalOn** und **GlobalOff** können auch mit den Optionen **ProcessOn**, **ProcessOff**, **ThreadOn** und **ThreadOff** kombiniert werden.  
  
 Die Optionen **GlobalOn** und **GlobalOff** interagieren mit den Optionen **ProcessOn** und **ProcessOff**, mit denen die Datensammlung für einen angegebenen Prozess gesteuert wird, und mit den Optionen **ThreadOn** und **ThreadOff**, mit denen die Datensammlung für einen angegebenen Thread gesteuert wird.  
  
 Die Optionen **GlobalOff** und **GlobalOn** wirken sich auch auf die globale Start\/Stop\-Anzahl aus, die von den API\-Funktionen des Profilers bearbeitet wird.  
  
-   **GlobalOff** legt die globale Start\/Stop\-Anzahl sofort auf "0" fest und hält daher die Profilerstellung an.  
  
-   **GlobalOn** legt die globale Start\/Stop\-Anzahl sofort auf "1" fest und nimmt die Profilerstellung daher wieder auf.  
  
 Weitere Informationen finden Sie unter [APIs für Profilerstellungstools](../profiling/profiling-tools-apis.md).  
  
## Syntax  
  
```  
VSPerfCmd.exe /{GlobalOff|GlobalOn}  
  
VSPerfCmd.exe /Start:Method /{GlobalOff|GlobalOn} [Options]  
  
VSPerfCmd.exe {Launch:AppName|Attach:PID} /{GlobalOff|GlobalOn} [Options]  
```  
  
#### Parameter  
 Kein  
  
## Gültige Optionen  
 **GlobalOn** und **GlobalOff** können in Befehlszeilen angegeben werden, die auch die folgenden Optionen enthalten.  
  
 **Start:** `Method`  
 Initialisiert die Befehlszeilen\-Profilersitzung und legt die angegebene Profilerstellungsmethode fest.  
  
 **Launch:** `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
 **Attach:** `PID`  
 Startet die Profilerstellung für den angegebenen Prozess.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`PID`  
 Hält die Profilerstellung für den angegebenen Prozess an oder startet sie.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Hält die Profilerstellung für den angegebenen Prozess an oder startet sie \(nur Instrumentationsmethode\).  
  
## Beispiel  
 In diesem Beispiel werden die **GlobalOff**\-Option und die **GlobalOn**\-Option verwendet, um das Sammeln von Profilerstellungsdaten für das Starten und Herunterfahren der Anwendung zu verhindern.  
  
```  
; Initialize the profiler with profiling stopped.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp /GlobalOff  
; Start an instrumented application and wait for it to warm up.  
; Start profiling.  
VSPerfCmd.exe /GlobalOn  
; Exercise the application functionality that you want to profile.  
; Stop profiling.  
VSPerfCmd.exe /GlobalOff  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)