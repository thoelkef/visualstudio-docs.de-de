---
title: "ProcessOn und ProcessOff | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3dc6a7e-bc0f-48a6-a4ec-f386348bb296
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ProcessOn und ProcessOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem **ProcessOff**\-Unterbefehl und dem **ProcessOn**\-Unterbefehl von VSPerfCmd.exe wird die Profilerstellung für den angegebenen Prozess in einer Profilerstellungssitzung über die Befehlszeile angehalten und wieder fortgesetzt.  **ProcessOff** beendet die Profilerstellung des Prozesses, und **ProcessOn** startet die Profilerstellung des Prozesses.  
  
 In den meisten Fällen geben Sie **ProcessOn** oder **ProcessOff** als einzige Option in einer VSPerfCmd.exe\-Befehlszeile an. Sie können jedoch auch mit den Unterbefehlen **GlobalOn**, **GlobalOff**, **ThreadOn** und **ThreadOff** kombiniert werden.  
  
 Der **ProcessOn**\-Unterbefehl und der **ProcessOff**\-Unterbefehl interagieren mit dem **GlobalOn**\-Unterbefehl und dem **GlobalOff**\-Unterbefehl, mit denen die Datensammlung für alle Prozesse in einer Profilerstellungssitzung über eine Befehlszeile gesteuert wird, und dem **ThreadOn**\-Unterbefehl sowie dem **ThreadOff**\-Unterbefehl, mit denen die Datensammlung für einen angegebenen Thread gesteuert wird.  
  
 Die Unterbefehle **ProcessOff** und **ProcessOn** wirken sich auch auf die Start\/Stop\-Anzahl von Prozessen aus, die von den API\-Funktionen des Profilers bearbeitet wird.  
  
-   **ProcessOff** legt die Start\/Stop\-Anzahl eines Prozesses sofort auf "0" fest und hält daher die Profilerstellung an.  
  
-   **ProcessOn** legt die Start\/Stop\-Anzahl eines Prozesses sofort auf "1" fest und nimmt die Profilerstellung daher wieder auf.  
  
 Weitere Informationen finden Sie unter [APIs für Profilerstellungstools](../profiling/profiling-tools-apis.md).  
  
## Syntax  
  
```  
VSPerfCmd.exe /{ProcessOff|ProcessOn}:PID [Options]  
  
```  
  
#### Parameter  
 `PID`  
 Der ganzzahlige Bezeichner des Prozesses, der gestartet oder angehalten werden soll.  Die Prozess\-IDs werden im Windows Task\-Manager auf der Registerkarte Prozess aufgeführt.  
  
## Erforderliche Unterbefehle  
 Kein  
  
## Gültige Unterbefehle  
 **ProcessOn** und **ProcessOff** können in Befehlszeilen angegeben werden, die auch die folgenden Unterbefehle enthalten.  
  
 **Start:** `Method`  
 Initialisiert die Befehlszeilen\-Profilersitzung und legt die angegebene Profilerstellungsmethode fest.  
  
 **Launch:** `AppName`  
 Startet die angegebene Anwendung und beginnt die Profilerstellung mit der Samplingmethode.  
  
 **Attach:** `PID`  
 Startet die Profilerstellung für den angegebenen Prozess.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Hält die Profilerstellung für alle Prozesse in einer Profilerstellungssitzung über die Befehlszeile an oder startet sie.  
  
 {**ThreadOff**&#124;**ThreadOn**}**:**`TID`  
 Hält die Profilerstellung für den angegebenen Thread an oder startet sie \(nur Instrumentationsmethode\).  
  
## Beispiel  
 In diesem Beispiel wird der **ProcessOff**\-Unterbefehl verwendet, um Profilerstellungsdaten für den Anwendungsstart zu erfassen.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the process after startup.  
VSPerfCmd.exe /ProcessOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)