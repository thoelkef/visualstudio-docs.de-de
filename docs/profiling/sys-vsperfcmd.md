---
title: "Sys (VSPerfCmd) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 294a6f9e-b49f-4c83-b322-5ac5411b66fb
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sys (VSPerfCmd)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Sys**\-Option von "VSPerfCmd.exe" legt das Profilerstellungsereignis, für das ein Sampling ausgeführt wird, auf Systemaufrufereignisse \(Funktionsaufrufe von der profilierten Anwendung an das Betriebssystem\) fest und bestimmt optional eine andere Standardeinstellung als "10" für die Anzahl der Systemaufrufe in einem Samplingintervall.  
  
 **Sys** kann nur in einer Befehlszeile verwendet werden, die auch die **Launch**\-Option oder die **Attach**\-Option enthält.  
  
 Standardmäßig wird das Samplingereignis des Profilers auf Prozessortaktzyklen und das Samplingintervall auf 10.000.000 festgelegt.  Mit den Optionen **Timer**, **PF**, **Sys** und **Counter** können Sie das Samplingereignis und das Samplingintervall festlegen.  Die **GC**\-Option erfasst bei jedem Belegungs\- und Garbage Collection\-Ereignis .NET\-Arbeitsspeicherdaten.  In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.  
  
 Das Samplingereignis und das Samplingintervall können nur in der ersten Befehlszeile mit einer **Launch**\-Option oder einer **Attach**\-Option festgelegt werden.  
  
## Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName|Attach:PID} /Sys[:Events] [Options]  
```  
  
#### Parameter  
 `Events`  
 Ein ganzzahliger Wert, der die Anzahl von Systemaufrufereignissen in einem Samplingintervall angibt.  Wenn `Events` nicht angegeben ist, wird das Intervall standardmäßig auf 10 festgelegt.  
  
## Erforderliche Optionen  
 Die **Sys**\-Option erfordert eine der folgenden Optionen.  
  
 **Launch:** `AppName`  
 Startet den Profiler und die mit `AppName` angegebene Anwendung.  
  
 **Attach:** `PID`  
 Fügt den Profiler an den Prozess an, der von `PID` angegeben wurde.  
  
## Ungültige Optionen  
 Die folgenden Optionen können nicht in der gleichen Befehlszeile wie **Sys** angegeben werden.  
  
 **PF**\[**:**`Events`\]  
 Legt das Samplingereignis auf Seitenfehler fest und das Samplingintervall optional auf `Events`.  Standard\-PF ist 10.  
  
 **Timer**\[**:**`Cycles`\]  
 Legt das Samplingereignis auf Prozessortaktzyklen und das Samplingintervall optional auf `Cycles` fest.  Standard\-Zeitgeberintervall ist 10.000.000.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Legt das Samplingereignis auf den mit `Name` angegebenen CPU\-Leistungsindikator und das Samplingintervall auf `Reload` fest.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Sammelt .NET\-Arbeitsspeicherdaten.  Standardmäßig \(**Allocation**\) werden Daten bei jeder Speicherbelegung gesammelt.  Wenn der **Lifetime**\-Parameter angegeben wird, werden Daten auch bei jedem Garbage Collection\-Ereignis erfasst.  
  
## Beispiel  
 In diesem Beispiel wird veranschaulicht, wie das Profiler\-Samplingereignis auf Systemaufrufe festgelegt wird und als Samplingintervall 20 Aufrufe pro Sampling angegeben werden.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Sys:20  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)