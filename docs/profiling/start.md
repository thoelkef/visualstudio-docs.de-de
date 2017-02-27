---
title: "Starten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Starten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Start**\-Option ist eine VSPerfCmd.exe\-Option, die den Profiler mit der angegebenen Profilerstellungsmethode initialisiert.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Parameter  
 `Method`  
 Muss eines der folgenden Schlüsselwörter sein:  
  
-   **TRACE** \- Gibt die Instrumentationsmethode an.  
  
-   **SAMPLE**\- Gibt die Samplingmethode an.  
  
-   **COVERAGE**\- Gibt die Codeabdeckung an.  
  
-   **CONCURRENCY** \- Gibt die Ressourcenkonfliktmethode an.  
  
## Erforderliche Optionen  
 Die **Output**\-Option muss angegeben werden, wenn **Start** in der Befehlszeile angegeben wird.  
  
 **Output:** `filename`  
 Gibt den Ausgabedateinamen an.  
  
## Exklusive Optionen  
 Die folgenden Optionen können nur mit der **Start**\-Option in einer Befehlszeile verwendet werden.  
  
 **CrossSession**&#124;**CS**  
 Aktiviert die prozessübergreifende Profilerstellung.  Die Optionsnamen **CrossSession** und **CS** werden beide unterstützt.  
  
 **User:**\[`domain\`\]`username`  
 Ermöglicht den Clientzugriff auf den Monitor über das angegebene Konto.  
  
 **WinCounter:** `Path` \[**Automark**:`n`\]  
 **WinCounter** gibt ein Windows\-Leistungsindikatorereignis an, das als Markierung in die Profilmarkierungsdaten aufgenommen werden soll.  **AutoMark** gibt in Millisekunden das Intervall zwischen Auflistungen der Datendatei an.  
  
## Ungültige Optionen  
 Die folgenden Optionen können nicht mit der **Start**\-Option in einer Befehlszeile verwendet werden.  
  
 **Status**  
 **Status** gilt für profilierte Prozesse.  Im Status werden Prozesse und Threads und der zugehörige aktuelle Profilzustand \(On\/Off\) aufgeführt.  Wenn ein Prozess z. B. beendet wurde, gibt **Status** dies nicht im Bericht an.  **Status** zeigt an, ob für den Prozess ein Profil erstellt wird.  
  
 **Shutdown**\[**:**`Timeout`\]  
 Deaktiviert den Profiler.  
  
## Beispiel  
 Im folgenden Beispiel wird gezeigt, wie die **Start**\-Option von VSPerfCmd.exe zum Initialisieren des Profilers verwendet wird.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)