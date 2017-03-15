---
title: "Zeitgeber | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1971868e-89fa-4452-8ee7-76e4daf31b66
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Zeitgeber
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Option VSPerfCmd.exe **Timer** legt das Profilerstellungsereignis fest, das für Prozessortaktzyklen gesampelt wird, und optional wird die Anzahl der Zyklen in einem Sample vom Standard 10.000.000 auf einen anderen Wert geändert.  Auf einen 1\-GHz\-Prozessor \(ein Gigahertz\) entsprechen 10.000.000 Prozessortaktzyklen ungefähr 100 Samples pro Sekunde.  Die Mindestanzahl an Zyklen, die sich festlegen lässt, ist 50.000.  
  
 **Timer** lässt sich nur verwenden, wenn man die Sampling\-Methode der Profilerstellung verwendet und der Einsatz ist nur in einer Befehlszeile möglich, die außerdem die Option **Launch** oder **Attach** enthält.  
  
 Standardmäßig ist das Profiler\-Samplingereignis auf Prozessortaktzyklen eingestellt und das Samplingintervall beträgt 10.000.000.  Die Optionen **Timer**, **PF**, **Sys** und **Counter** ermöglichen das Festlegen des Samplingereignisses und \-intervalls.  Die Option **GC** sammelt die .NET\-Speicherdaten bei jedem Belegungs\- und Garbage Collection\-Ereignis.  In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.  
  
 Das Samplingereignis und \-invtervall können nur in der ersten Befehlszeile festgelegt werden, die eine Option **Launch** oder **Attach** enthält.  
  
## Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /Timer[:Cycles] [Options]  
```  
  
#### Parameter  
 `Cycles`  
 Ein Ganzzahlwert, der die Anzahl der Prozessortaktzyklen in einem Samplingintervall festlegt.  Wenn `Cycles` nicht festgelegt wurde, wird das Intervall auf 10.000.000 gesetzt.  Geben Sie den Wert ohne Kommas an.  
  
## Erforderliche Optionen  
 **Timer** lassen sich nur in einer Befehlszeile festlegen, die eine der folgenden Optionen enthält.  
  
 **Launch:** `AppName`  
 Startet den Profiler und die von `AppName` festgelegten Anwendungen.  
  
 **Attach:** `PID`  
 Fügt den Profiler dem von der Prozess\-ID \(`PID`\) festgelegten Prozess an.  
  
## Ungültige Optionen  
 Das folgenden Optionen können nicht in derselben Befehlszeile wie **Timer** festgelegt werden.  
  
 **PF**\[**:**`Events`\]  
 Legt die Seitenstandards für das Samplingereignis fest und optional das Samplingintervall auf `Events`.  Das standardmäßige PF\-Intervall beträgt 10.  
  
 **Sys**\[**:**`Events`\]  
 Legt die Betriebssystemaufrufe für das Samplingereignis fest und optional das Samplingintervall auf `Events`.  Das standardmäßige Sys\-Intervall beträgt 10.  
  
 **Counter**\[**:**`Name,Reload,FriendlyName`\]  
 Legt das Samplingereignis auf den von `Name` festgelegten CPU\-Leistungsindikator fest und das Samplingintervall auf `Reload`.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Sammelt .NET\-Speicherdaten.  Standardmäßig \(**Allocation**\) werden Daten bei jedem Speicherbelegungsereignisse gesammelt.  Wenn der **Lifetime**\-Parameter festgelegt wird, werden die Daten auch bei jedem Garbage Collection\-Ereignis gesammelt.  
  
## Beispiel  
 Dieses Beispiel zeigt, wie das Profiler\-Samplingintervall auf 1.000.000 Prozessortaktzyklen festgelegt wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /Timer:1000000  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)