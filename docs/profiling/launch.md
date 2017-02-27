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
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Starten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Launch**\-Option startet den Profiler mithilfe der Samplingmethode. Darüber hinaus startet sie auch die angegebene Anwendung.  
  
 Um die **Launch**\-Option verwenden zu können, müssen Sie die **Sample**\-Methode in der **Start**\-Option angeben.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### Parameter  
 `AppName`  
 Der Name der Anwendung, die gestartet werden soll.  Vollständige Pfade und Teilpfade vom aktuellen Verzeichnis werden unterstützt.  
  
## Gültige Optionen  
 Die folgenden VSPerfCmd\-Optionen können in Verbindung mit der **Launch**\-Option in einer einzelnen Befehlszeile kombiniert werden.  
  
 **Start:** `Method`  
 Initialisiert die Befehlszeilen\-Profilersitzung und legt die angegebene Profilerstellungsmethode fest.  
  
 **GlobalOn**und**GlobalOff**  
 Damit wird die Profilerstellung fortgesetzt \(**GlobalOn**\) oder angehalten \(**GlobalOff**\), die Profilerstellungssitzung wird jedoch nicht beendet.  
  
 **ProcessOn:** `PID` und **ProcessOff**:`PID`  
 Damit wird die Profilerstellung für den angegebenen Prozess fortgesetzt \(**ProcessOn**\) oder angehalten \(**ProcessOff**\).  
  
 **TargetCLR**  
 Gibt die Version der .NET Framework\-CLR \(Common Language Runtime\) an, für die ein Profil erstellt werden soll, wenn in einer Profilerstellungssitzung mehr als eine Version geladen wurde.  Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.  
  
## Exklusive Optionen  
 Die folgenden Optionen können nur in Verbindung mit der **Launch**\-Option verwendet werden.  
  
 **Console**  
 Startet die angegebene Befehlszeilenanwendung in einem neuen Fenster.  
  
 **Args:** `ArgList`  
 Gibt die Liste der an die Anwendung zu übergebenden Argumente an.  
  
 **LineOff**  
 Deaktiviert der Auflistung von Profilerstellungsdaten auf Zeilenebene.  
  
## Samplingoptionen  
 In der **Launch**\-Befehlszeile kann eine der folgenden Samplingintervalloptionen angegeben werden.  Das Standardsamplingintervall beträgt 10.000.000 Prozessortaktzyklen.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**`Events`\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]**GC**\[:**allocation**&#124;**lifetime**\]  
 Gibt die Anzahl und den Typ des Samplingintervalls an.  
  
-   **Timer** \- Führt alle `Cycles` nicht angehaltene Prozessortaktzyklen ein Sampling durch.  Wenn `Cycles` nicht angegeben ist, werden 10.000.000 Zyklen verwendet.  
  
-   **PF** \- Führt alle `Events` Seitenfehler ein Sampling durch.  Wenn `Events` nicht angegeben ist, werden 10 Seitenfehler verwendet.  
  
-   **Sys** \- Führt alle `Events` Aufrufe des Betriebssystems ein Sampling durch.  Wenn `Events` nicht angegeben ist, werden 10 Systemaufrufe verwendet.  
  
-   **Counter** \- Führt alle `Reload` CPU\-Leistungsindikatoren, die mit `Name` angegeben sind, ein Sampling durch.  Optional kann `FriendlyName` eine Zeichenfolge angeben, die  in Profilerberichten als Spaltenüberschrift verwendet werden soll.  
  
-   **GC** \- Sammelt .NET\-Arbeitsspeicherdaten.  Standardmäßig \(**allocation**\) werden Daten bei jeder Speicherbelegung gesammelt.  Wenn der **lifetime**\-Parameter angegeben wird, werden Daten auch bei jedem Garbage Collection\-Ereignis erfasst.  
  
## Beispiel  
 In diesem Beispiel wird die Verwendung der **Launch**\-Option zum Starten einer Anwendung veranschaulicht.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)