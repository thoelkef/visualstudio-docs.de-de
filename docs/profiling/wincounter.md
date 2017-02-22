---
title: "WinCounter | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ff319ffc-f249-4c3f-9eb2-06e392e3ae80
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# WinCounter
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **WinCounter**\-Option gibt einen Leistungsindikator für Windows oder für Anwendungen an, der während der Profilausführung zu festgelegten Intervallen erfasst werden soll.  Leistungsindikatoren für Windows und Anwendungen werden in der Profilerstellungs\-Datendatei als Markierungen aufgeführt.  Sie können mehrere Leistungsindikatoren angeben, die in separaten Optionen erfasst werden sollen.  
  
 Standardmäßig werden Leistungsindikatoren alle 500 Millisekunden erfasst.  Verwenden Sie die **AutoMark**\-Option, um ein anderes Auflistungsintervall anzugeben.  
  
 Es wird nur eine **AutoMark**\-Option verwendet.  Wenn mehrere **AutoMark**\-Optionen angegeben werden, wird die zuletzt angegebene verwendet.  
  
 Die **WinCounter**\-Option kann nur in Verbindung mit der **Start**\-Option verwendet werden.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Wincounter:Path [/WinCounter:Path] [AutoMark:Milliseconds] [Options]  
```  
  
#### Parameter  
 `Path`  
 Der Windows\-Leistungsindikator im PDH\-Format für Indikatorpfade.  
  
## Erforderliche Optionen  
 Die **WinCounter**\-Option kann nur in Verbindung mit der **Start**\-Option verwendet werden.  
  
 **Start:** `Method`  
 Die **Start**\-Option initialisiert den Profiler mit der angegebenen Profilerstellungsmethode.  
  
## Exklusive Optionen  
 Die **AutoMark**\-Option kann nur in Verbindung mit der **WinCounter**\-Option verwendet werden.  
  
 **AutoMark:** `Milliseconds`  
 Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Sammlung von Windows\-Leistungsindikatordaten an.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Windows\-Leistungsindikatoren angegeben, die zu einem Intervall von 1000 Millisekunden erfasst werden sollen.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /WinCounter:"\Processor(0)\% Processor Time" /WinCounter:"\System\Context Switches/sec" /AutoMark:1000  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)