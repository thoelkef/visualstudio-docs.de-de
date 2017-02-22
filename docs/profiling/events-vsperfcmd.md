---
title: "Events (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Events (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Events**\-Option von VSPerfCmd.exe steuert die ETW\-Protokollierung \(Ereignisablaufverfolgung für Windows\).  ETW\-Daten werden in einer ETL\-Datei gespeichert, die von der Profiler\-Datendatei getrennt ist.  Die Daten können mithilfe des Befehls [VSPerfReport](../profiling/vsperfreport.md) \/summary:etw in einem Bericht angezeigt werden.  
  
 Die **Events**\-Option kann jederzeit aufgerufen werden, bevor der VSPerfCmd\-Befehl **Shutdown** zum Beenden der Profilerstellung aufgerufen wird.  
  
## Syntax  
  
```  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### Parameter  
 **On**&#124;**Off**  
 Startet oder beendet das Sammeln von Ereignisdaten.  
  
 `Guid`  
 Die GUID des Anbietersteuerelements.  
  
 `ProviderName`  
 Der Name des Anbieters, der bei WMI \(Windows\-Verwaltungsinstrumentation\) registriert ist.  
  
 `Flags`  
 Ein hexadezimaler Flagwert mit vorangestelltem "0x", der vom Ereignisanbieter definiert wurde.  
  
 `Level`  
 Gibt die Menge der gesammelten Daten an.  `Level` wird vom Ereignisanbieter definiert.  
  
 Die **Events**\-Option fasst die folgenden Kernelschlüsselwörter als Anbieternamen auf:  
  
 **Process**  
 Prozessereignisse  
  
 **Thread**  
 Threadereignisse  
  
 **Image**  
 Abbildlade\- und Abbildentladereignisse  
  
 **Disk**  
 Datenträger\-E\/A\-Ereignisse  
  
 **File**  
 Datei\-E\/A\-Ereignisse  
  
 **Hardfault**  
 Hardwareseitenfehler  
  
 **Pagefault**  
 Softwareseitenfehler  
  
 **Network**  
 Netzwerkereignisse  
  
 **Registry**  
 Registrierungszugriffsereignisse  
  
 Beachten Sie, dass der Kernelanbieter nur aktiviert werden kann.  Er kann erst deaktiviert und die zugehörigen Flags können erst bearbeitet werden, wenn der Monitor heruntergefahren ist.  
  
## Hinweise  
  
> [!NOTE]
>  Wenn CLR\-ETW\-Ereignisse aktiviert sind, werden zusätzliche Startdaten auch im Ablaufverfolgungsansichtsbericht erfasst.  Verwenden Sie den folgenden Befehl, um Startereignisse von der Anzeige im Bericht auszuschließen:  
  
```  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Wenn Sie die Startereignisse nicht ausschließen, da diese Ereignisse nicht in der MOF\-Datei \(Managed Object Format\) angezeigt werden, werden sie im Bericht als GUIDs angezeigt.  Weitere Informationen finden Sie auf der folgenden Seite: [Beispiel\-ManagedObject Format \(MOF\)\- Datei](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)