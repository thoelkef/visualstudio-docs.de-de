---
title: "Gewusst wie: Starten einer systemeigenen, eigenst&#228;ndigen Anwendung mit dem Profiler zum Sammeln von Parallelit&#228;tsdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5aed651-afed-4b70-9a7e-1a6032cc614f
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Starten einer systemeigenen, eigenst&#228;ndigen Anwendung mit dem Profiler zum Sammeln von Parallelit&#228;tsdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools eigenständige \(Client\-\)Anwendungen gestartet und Parallelitätsdaten zu Prozessen und Threads erfasst werden.  
  
 Eine Profilerstellungssitzung setzt sich aus folgenden Teilen zusammen:  
  
-   Starten der Anwendung mit dem Profiler  
  
-   Steuern der Datensammlung  
  
-   Beenden der Profilerstellungssitzung  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie den Profiler an einer Eingabeaufforderung verwenden können, müssen Sie der PATH\-Umgebungsvariablen in der **Eingabeaufforderung** oder dem Befehl selbst den Pfad des Tools hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Starten der Anwendung mit dem Profiler  
 Wenn Sie die Zielanwendung mit dem Profiler starten möchten, verwenden Sie die [VSPerfCmd](../profiling/vsperfcmd.md)**\/start** und **\/launch**\-Optionen, um den Profiler zu initialisieren und die Anwendung zu starten.  Sie können **\/start** und **\/launch** und ihre jeweiligen Optionen angeben.  Sie können auch die **\/globaloff**\-Option hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten.  Zum Starten der Datensammlung verwenden Sie dann das **\/globalon**\-Objekt.  
  
#### So starten Sie eine Anwendung mit dem Profiler  
  
1.  Geben Sie an einer Eingabeaufforderung folgenden Befehl ein:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der **\/start:concurrency** \-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
2.  Starten Sie die Zielanwendung, indem Sie Folgendes eingeben:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\]  
  
     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der **\/launch**\-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Gibt eine Zeichenfolge mit den Befehlszeilenargumenten an, die an die Zielanwendung übergeben werden sollen.|  
    |[\/console](../profiling/console.md)|Startet die Ziel\-Befehlszeilenanwendung in einem separaten Fenster.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `CLRVersion`|Gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn von der Anwendung mehr als eine Version der CLR geladen wird.|  
  
## Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei über VSPerfCmd.exe\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Mit den Optionspaaren in der folgenden Tabelle wird die Datensammlung gestartet und beendet.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID \(`PID`\) oder des Prozessnamens \(*ProcName*\) angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein Prozess angegeben ist\) beendet.|  
  
-   Sie können auch die [\/mark](../profiling/mark.md)\-Option von **VSPerfCmd.exe** verwenden, um eine Profilmarkierung in die Datendatei einzufügen.  Der **\/mark**\-Befehl fügt einen Bezeichner, einen Zeitstempel und eine optionale benutzerdefinierte Textzeichenfolge hinzu.  Mit Markierungen können die Daten in Profilerberichten und Datenansichten gefiltert werden.  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen.  Sie können die Erfassung von Parallelitätsdaten beenden, indem Sie die profilierte Anwendung schließen oder indem Sie die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Trennen Sie den Profiler von der Zielanwendung, indem Sie die Anwendung schließen oder an einer Eingabeaufforderung folgenden Befehl eingeben:  
  
     **VSPerfCmd \/detach**  
  
2.  Beenden Sie den Profiler, indem Sie den folgenden Befehl an der Eingabeaufforderung eingeben:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)