---
title: "Gewusst wie: Starten einer eigenst&#228;ndigen .NET Framework-Anwendung mit dem Profiler zum Sammeln paralleler Daten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17a48848-bd3e-44ef-9971-e39836ff1df2
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Starten einer eigenst&#228;ndigen .NET Framework-Anwendung mit dem Profiler zum Sammeln paralleler Daten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools eigenständige .NET Framework\-\(Client\-\)Anwendungen gestartet und Parallelitätsdaten zu Prozessen und Threads erfasst werden.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Während der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden.  
  
## Starten der Anwendung mit dem Profiler  
 Um eine .NET Framework\-Zielanwendung mit dem Profiler zu starten, legen Sie die .NET Framework\-Profilerstellungsvariablen mithilfe von VSPerfClrEnv.exe fest.  Verwenden Sie daraufhin die VSPerfCmd\-Optionen **\/start** und **\/launch**, um den Profiler zu initialisieren und die Anwendung zu starten.  Sie können **\/start** und **\/launch** sowie die zugehörigen Optionen in einer einzigen Befehlszeile angeben.  Außerdem können Sie der Befehlszeile die **\/globaloff**\-Option hinzufügen, um die Datensammlung anzuhalten, wenn die Zielanwendung gestartet wird.  Verwenden Sie dann den **\/globalon**\-Befehl in einer separaten Befehlszeile, um die Datensammlung zu starten.  
  
#### So starten Sie eine Anwendung mit dem Profiler  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency**\[**,**{**ResourceOnly**&#124;**ThreadOnly**}\] **\/output:**`OutputFile` \[`Options`\]  
  
    -   Mit der [\/start](../profiling/start.md)\-Option wird der Profiler initialisiert.  
  
        |||  
        |-|-|  
        |**\/start:concurrency**|Aktiviert das Sammeln von Ressourcenkonflikt\- und Threadausführungsdaten.|  
        |**\/start:concurrency,resourceonly**|Aktiviert nur das Sammeln von Ressourcenkonfliktdaten.|  
        |**\/start:concurrency,threadonly**|Aktiviert nur das Sammeln von Threadausführungsdaten.|  
  
    -   Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:concurrency** \-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`domain\`\]`username`|Gibt den optionalen Domänen\- und Benutzernamen des Kontos an, dem Zugriff auf den Profiler gewährt werden soll.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
3.  Starten Sie die Zielanwendung.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `AppName` \[`Options`\] \[`Sample Event`\]  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/launch**\-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Gibt eine Zeichenfolge mit den Befehlszeilenargumenten an, die an die Zielanwendung übergeben werden sollen.|  
    |[\/console](../profiling/console.md)|Startet die Ziel\-Befehlszeilenanwendung in einem separaten Fenster.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn mehr als eine Laufzeitversion in eine Anwendung geladen wird.|  
  
## Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit VSPerfCmd.exe\-Optionen starten und beenden.  Durch die Steuerung der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
1.  Mit den folgenden VSPerfCmd.exe\-Optionspaaren wird die Datensammlung gestartet und beendet.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID \(`PID`\) oder des Prozessnamens \("ProcName"\) angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist\) beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen.  Sie können die Erfassung von Parallelitätsdaten beenden, indem Sie die profilierte Anwendung schließen oder indem Sie die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Mit dem **VSPerfClrEnv \/off**\-Befehl werden die Umgebungsvariablen für die Profilerstellung gelöscht.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Schließen Sie die Zielanwendung.  
  
         \- oder \-  
  
    -   Geben Sie **VSPerfCmd \/detach** ein.  
  
2.  Schließen Sie den Profiler.  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Siehe auch  
 [Sammeln von Parallelitätsdaten](../profiling/collecting-concurrency-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)