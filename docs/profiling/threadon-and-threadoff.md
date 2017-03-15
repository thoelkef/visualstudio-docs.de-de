---
title: "ThreadOn und ThreadOff | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5cd5a695-0a14-484a-8952-ed47e13d8e92
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ThreadOn und ThreadOff
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der VSPerfCmd.exe **ThreadOff**\-Unterbefehl und **ThreadOn**\-Unterbefehl sind nur in Befehlszeilenprofilerstellungssitzungen verfügbar, die die Instrumentationsmethode verwenden.  **ThreadOff** und **ThreadOn** halten die Profilerstellung für den angegebenen Thread an und setzen sie fort.  **ThreadOff** beendet die Profilerstellung des Threads, und **ThreadOn** startet die Profilerstellung des Threads.  
  
 In den meisten Fällen geben Sie **ThreadOn** oder **ThreadOff** als einzige Option in einer VSPerfCmd.exe\-Befehlszeile an. Sie können jedoch auch mit den Unterbefehlen **GlobalOn**, **GlobalOff**, **ProcessOn** und **ProcessOff** kombiniert werden.  
  
 Der **ThreadOn**\-Unterbefehl und der **ThreadOff**\-Unterbefehl interagieren mit dem **GlobalOn**\-Unterbefehl und dem **GlobalOff**\-Unterbefehl, mit denen die Datensammlung für alle Prozesse in einer Profilerstellungssitzung über eine Befehlszeile gesteuert wird, und dem **ProcessOn**\-Unterbefehl sowie dem **ProcessOff**\-Unterbefehl, mit denen die Datensammlung für einen angegebenen Prozess gesteuert wird.  
  
 Die Unterbefehle **ThreadOff** und **ThreadOn** wirken sich auch auf die Start\/Stop\-Anzahl von Threads aus, die von den API\-Funktionen des Profilers bearbeitet wird.  
  
-   **ThreadOff** legt die Start\/Stop\-Anzahl von Threads sofort auf "0" fest und hält daher die Profilerstellung an.  
  
-   **ThreadOn** legt die globale Start\/Stop\-Anzahl von Threads sofort auf "1" fest und nimmt die Profilerstellung daher wieder auf.  
  
 Weitere Informationen finden Sie unter [APIs für Profilerstellungstools](../profiling/profiling-tools-apis.md).  
  
## Syntax  
  
```  
VSPerfCmd.exe /{ThreadOff|ThreadOn}:TID [Options]  
  
```  
  
#### Parameter  
 `TID`  
 Der ganzzahlige Bezeichner des Threads zum Starten oder Anhalten.  
  
## Gültige Optionen  
 **ThreadOn** und **ThreadOff** können in Befehlszeilen angegeben werden, die auch die folgenden Unterbefehle enthalten.  
  
 **Start:** `Method`  
 Initialisiert die Befehlszeilen\-Profilersitzung und legt die angegebene Profilerstellungsmethode fest.  
  
 **GlobalOff**&#124;**GlobalOn**  
 Hält die Profilerstellung für alle Prozesse in einer Profilerstellungssitzung über die Befehlszeile an oder startet sie.  
  
 {**ProcessOff**&#124;**ProcessOn**}**:**`TID`  
 Hält die Profilerstellung für den angegebenen Prozess an oder startet sie.  
  
## Beispiel  
 In diesem Beispiel wird der **ThreadOff**\-Unterbefehl verwendet, um das Sammeln von Profilerstellungsdaten anzuhalten, sodass nur Anwendungsstartdaten gesammelt werden.  
  
```  
; Initialize the profiler.  
VSPerfCmd.exe /Start:Trace /Output:Instrument.vsp   
; Start the instrumented application.  
; Stop profiling the thread after startup.  
VSPerfCmd.exe /ThreadOff:12345  
; Shut down the target application.  
; Close the profiler.  
VSPerfCmd /Shutdown  
  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)