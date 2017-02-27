---
title: "PF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cdc0a094-a986-4629-bd1c-dd5fdca323dc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# PF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **PF**\-Option von "VSPerfCmd.exe" legt das Profilerstellungsereignis fest, mit dem das Sampling für die Seitenfehler ausgeführt wird, und ändert optional die Anzahl der Seitenfehler in einem Samplingintervall, die standardmäßig bei 10 liegt.  
  
> [!NOTE]
>  PF kann nicht auf 64\-Bit\-Systemen verwendet werden.  
  
 **Hinweis**  
 **PF** wird auf 64\-Bit\-Computern nicht unterstützt. **PF** kann nur in einer Befehlszeile verwendet werden, die auch die **Launch**\-Option oder die **Attach**\-Option enthält.  
  
 Standardmäßig wird das Samplingereignis auf nicht angehaltene Prozessortaktzyklen und das Samplingintervall auf 10.000.000 festgelegt.  Mit den Optionen **Timer**, **PF**, **Sys** und **Counter** können Sie das Samplingereignis und das Samplingintervall festlegen.  Die **GC**\-Option erfasst bei jedem Belegungs\- und Garbage Collection\-Ereignis .NET\-Arbeitsspeicherdaten.  In einer Befehlszeile kann nur eine dieser Optionen angegeben werden.  
  
 Das Samplingereignis und das Samplingintervall können nur in der ersten Befehlszeile mit einer **Launch**\-Option oder einer **Attach**\-Option festgelegt werden.  
  
## Syntax  
  
```  
VSPerfCmd.exe {/Launch:AppName|/Attach:PID} /PF[:Events] [Options]  
```  
  
#### Parameter  
 `Events`  
 Ein ganzzahliger Wert, der die Anzahl von Seitenfehlerereignissen in einem Samplingintervall angibt.  Wenn `Events` nicht angegeben ist, wird das Intervall standardmäßig auf 10 festgelegt.  
  
## Erforderliche Optionen  
 **PF** kann nur in einer Befehlszeile mit einer der folgenden Optionen angegeben werden.  
  
 **Launch:** `AppName`  
 Startet den Profiler und die mit AppName angegebene Anwendung.  
  
 **Attach:** `PID`  
 Fügt den Profiler an den Prozess an, der von AppName angegeben wurde.  
  
## Ungültige Optionen  
 Die folgenden Optionen können nicht in der gleichen Befehlszeile wie **PF** angegeben werden.  
  
 **Timer**\[**:**`Cycles`\]  
 Legt das Samplingereignis auf Prozessortaktzyklen und das Samplingintervall optional auf `Cycles` fest.  Standard\-Zeitgeberintervall ist 10.000.000.  
  
 **Sys**\[**:**`Events`\]  
 Legt das Samplingereignis auf Aufrufe von der profilierten Anwendung an den Betriebssystem\-Kernel \(syscalls\) fest und legt optional das Samplingintervall auf `Events` fest.  Standard\-Sys ist 10.  
  
 **Counter:** `Name`\[`,Reload`\[`,FriendlyName`\]\]  
 Legt das Samplingereignis auf den mit `Name` angegebenen CPU\-Leistungsindikator und das Samplingintervall auf `Reload` fest.  
  
 **GC**\[**:**{**Allocation**&#124;**Lifetime**}\]  
 Sammelt .NET\-Arbeitsspeicherdaten.  Standardmäßig \(**Allocation**\) werden Daten bei jeder Speicherbelegung gesammelt.  Wenn der **Lifetime**\-Parameter angegeben wird, werden Daten auch bei jedem Garbage Collection\-Ereignis erfasst.  
  
## Beispiel  
 In diesem Beispiel wird veranschaulicht, wie das Samplingereignis der Profilerstellung auf Seitenfehler und das Samplingintervall auf 20 Seitenfehler festgelegt wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe /PF:20  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)