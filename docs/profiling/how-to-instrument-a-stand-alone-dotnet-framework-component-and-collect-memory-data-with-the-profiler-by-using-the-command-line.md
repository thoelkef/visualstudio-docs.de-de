---
title: "Gewusst wie: Instrumentieren einer eigenst&#228;ndigen .NET Framework-Komponente und Sammeln von Speicherdaten &#252;ber die Befehlszeile mit dem Profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d09cc46a-70f5-48f9-aa24-89913e67b359
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Instrumentieren einer eigenst&#228;ndigen .NET Framework-Komponente und Sammeln von Speicherdaten &#252;ber die Befehlszeile mit dem Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools eine .NET Framework\-Komponente einer eigenständigen Anwendung wie eine EXE\- oder eine DLL\-Datei instrumentiert wird und wie Arbeitsspeicherinformationen mit dem Profiler gesammelt werden.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des Visual Studio\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Um Arbeitsspeicherdaten einer .NET Framework\-Komponente mit der Instrumentationsmethode zu erfassen, verwenden Sie das Tool [VSInstr.exe](../profiling/vsinstr.md), um eine instrumentierte Version der Komponente und des [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)\-Tools zu generieren und Profilerstellungs\-Umgebungsvariablen zu initialisieren.  Danach starten Sie den Profiler mit dem Tool **VSPerfCmd.exe**.  
  
 Wenn die instrumentierte Komponente ausgeführt wird, werden Speicherdaten automatisch in einer Datendatei erfasst.  Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Zielanwendung, und schließen Sie danach den Profiler.  In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## Starten der Anwendung mit dem Profiler  
  
#### So fügen Sie den Profiler an eine aktive .NET Framework\-Anwendung an  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Generieren Sie mit dem **VSInstr**\-Tool eine instrumentierte Version der Zielanwendung.  
  
3.  Initialisieren Sie die .NET Framework\-Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv** {**\/tracegc** &#124; **\/tracegclife**}  
  
    -   Mit der **\/tracegc**\-Option und der **\/tracegclife**\-Option werden die Umgebungsvariablen so initialisiert, dass entweder nur Daten zur Speicherbelegung oder Daten zur Speicherbelegung und der Objektlebensdauer gesammelt werden.  
  
        |Option|**Beschreibung**|  
        |------------|----------------------|  
        |**\/tracegc**|Aktiviert die Sammlung von Daten zur Speicherbelegung.|  
        |**\/tracegclife**|Aktiviert die Sammlung von Daten zur Speicherbelegung und zur Objektlebensdauer.|  
  
4.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   Mit der [\/start](../profiling/start.md)**:trace**\-Option wird der Profiler initialisiert.  
  
    -   Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:trace**\-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist.  Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen.  Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs\-ID des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Um den Profiler mit angehaltener Datensammlung zu starten, fügen Sie der **\/start**\-Befehlszeile die **\/globaloff**\-Option hinzu.  Mit **\/globalon** setzen Sie die Profilerstellung fort.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Sammelt Informationen aus dem in Config angegebenen Prozessorleistungsindikator.  Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden.|  
    |[events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
5.  Starten Sie die Zielanwendung über das Eingabeaufforderungsfenster.  
  
## Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit **VSPerfCmd.exe**\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Paare von **VSPerfCmd**\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon](../profiling/globalon-and-globaloff.md) [\/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den über die Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Startet \(**\/threadon**\) oder beendet \(**\/threadoff**\) die Datensammlung für den mit der Thread\-ID \(`TID`\) angegebenen Thread.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Anwendung, die die instrumentierte Komponente ausführt, und rufen Sie dann die **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Mit dem **VSPerfClrEnv \/off**\-Befehl werden die Umgebungsvariablen für die Profilerstellung gelöscht.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Schließen Sie die Zielanwendung.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Optional\) Löschen Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/off**  
  
## Siehe auch  
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET\-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)