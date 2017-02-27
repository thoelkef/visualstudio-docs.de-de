---
title: "Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Attach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **Attach**\-Option von "VSPerfCmd.exe" startet die Samplingprofilerstellung des laufenden Prozesses, der von der Prozess\-ID \(PID\) angegeben wurde.  
  
 Um die **Attach**\-Option verwenden zu können, müssen Sie die **Sample**\-Methode in der Start\-Option angeben.  
  
> [!NOTE]
>  Wenn die **Start**\-Option mit der **Crosssession**\-Option angegeben wurde, müssen alle Aufrufe von **VSPerfCmd \/Attach** oder **VSPerfCmd \/Detach** auch **Crosssession** angeben.  
  
## Syntax  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### Parameter  
 `ProcessID`  
 Die Prozess\-ID \(PID\) des laufenden Prozesses.  Die PID eines laufenden Prozesses ist auf der Registerkarte "Prozesse" des Windows Task\-Managers aufgeführt.  
  
## Gültige Optionen  
 Die folgenden **VSPerfCmd**\-Optionen können mit der **Attach**\-Option in einer einzelnen Befehlszeile kombiniert werden.  
  
 **Crosssession**  
 Aktiviert Profilerstellungsanwendungen in anderen Sitzungen als in der Anmeldesitzung.  Erforderlich, wenn die **Start**\-Option mit der **Crosssession**\-Option angegeben wurde.  
  
 **Start:** `Method`  
 Initialisiert die Befehlszeilen\-Profilersitzung und legt die angegebene Profilerstellungsmethode fest.  
  
 **TargetCLR**  
 Gibt die Version der .NET Framework\-CLR \(Common Language Runtime\) an, für die ein Profil erstellt werden soll, wenn in einer Profilerstellungssitzung mehr als eine Version geladen wurde.  Standardmäßig wird die zuerst geladene Version für die Profilerstellung verwendet.  
  
 **GlobalOn GlobalOff**  
 Damit wird die Profilerstellung fortgesetzt \(**GlobalOn**\) oder angehalten \(**GlobalOff**\), die Profilerstellungssitzung wird jedoch nicht beendet.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Damit wird die Profilerstellung für den angegebenen Prozess fortgesetzt \(**ProcessOn**\) oder angehalten \(**ProcessOff**\).  
  
## Intervalloptionen  
 In der Attach\-Befehlszeile kann eine der folgenden Samplingintervalloptionen angegeben werden.  Das Standardsamplingintervall beträgt 10.000.000 Prozessortaktzyklen.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**Events\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]  
 Gibt die Anzahl und den Typ des Samplingintervalls an.  
  
-   **Timer** \- Führt alle `Cycles` Prozessortaktzyklen ein Sampling durch.  Wenn `Cycles` nicht angegeben ist, werden 10.000.000 Zyklen verwendet.  
  
-   **PF** \- Führt alle `Events` Seitenfehler ein Sampling durch.  Wenn `Events` nicht angegeben ist, werden 10 Seitenfehler verwendet.  
  
-   **Sys** \- Führt alle `Events` Aufrufe des Betriebssystems ein Sampling durch.  Wenn `Events` nicht angegeben ist, werden 10 Systemaufrufe verwendet.  
  
-   **Counter** \- Führt alle `Reload` CPU\-Leistungsindikatoren, die mit `Name` angegeben sind, ein Sampling durch.  Optional kann `FriendlyName` eine Zeichenfolge angeben, die  in Profilerberichten als Spaltenüberschrift verwendet werden soll.  
  
## Beispiel  
 In diesem Beispiel wird das Anfügen einer Anwendung an eine laufende Instanz mit der Prozess\-ID 12345 veranschaulicht.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## Siehe auch  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)