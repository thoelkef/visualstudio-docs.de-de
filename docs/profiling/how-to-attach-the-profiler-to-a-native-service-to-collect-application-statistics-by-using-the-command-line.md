---
title: "Gewusst wie: Anf&#252;gen des Profilers an einen systemeigenen Dienst zum Sammeln von Anwendungsstatistiken &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an einen systemeigenen Dienst zum Sammeln von Anwendungsstatistiken &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie der Profiler mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools an einen systemeigenen Dienst angefügt wird und wie Sie mit der Samplingmethode Leistungsstatistiken sammeln können.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Um die Profiler\-Befehlszeilentools zu verwenden, müssen Sie den Toolpfad der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Während der Profiler an den Dienst angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler vom Dienst getrennt und explizit beendet werden.  
  
## Starten der Anwendung mit dem Profiler  
 Wenn Sie den Profiler an einen systemeigenen Dienst anfügen möchten, verwenden Sie die Optionen  **VSPerfCmd.exe** [\/start](../profiling/start.md) und [\/attach](../profiling/attach.md), um den Profiler zu initialisieren und an die Zielanwendung anzufügen.  Sie können **\/start** und **\/attach** sowie die zugehörigen Optionen in einer einzigen Befehlszeile angeben.  Sie können auch die [\/globaloff](../profiling/globalon-and-globaloff.md)\-Option hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten.  Anschließend können Sie die Datensammlung mithilfe der [\/globalon](../profiling/globalon-and-globaloff.md)\-Option beginnen.  
  
#### So fügen Sie den Profiler an einen systemeigenen Dienst an  
  
1.  Starten Sie den Dienst bei Bedarf.  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
3.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/start:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   Mit der **\/start:sample**\-Option wird der Profiler initialisiert.  
  
    -   Die **\/output:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:sample**\-Option verwenden.  
  
    > [!NOTE]
    >  Die **\/user**\-Option und die **\/crosssession**\-Option sind normalerweise für Dienste erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist.  Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen.  Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte "Prozesse" in der Spalte "Sitzungs\-ID" des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
4.  Fügen Sie den Profiler an den Dienst an.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/attach:** `PID` \[`Sample Event`\]  
  
     `PID` gibt die Prozess\-ID der Zielanwendung an.  Die Prozess\-IDs aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
     Standardmäßig wird alle 10.000.000 nicht angehaltene Prozessortaktzyklen ein Sampling der Leistungsdaten durchgeführt.  Dies entspricht ca. 10 Sekunden auf einem 1\-GHz\-Prozessor.  Sie können eine der folgenden Optionen angeben, um das Taktzyklusintervall zu ändern oder ein anderes Samplingereignis anzugeben.  
  
    |Samplingereignis|**Beschreibung**|  
    |----------------------|----------------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Ändert das Samplingintervall in die Anzahl der mit `Interval` angegebenen nicht angehaltenen Taktzyklen.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Ändert das Samplingereignis in Seitenfehler.  Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Seitenfehler zwischen den Samplings angegeben.  Der Standardwert ist 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|Ändert das Samplingereignis in Systemaufrufe des Prozesses an den Betriebssystem\-Kernel \(syscalls\).  Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Aufrufe zwischen den Samplings angegeben.  Der Standardwert ist 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Ändert das Samplingereignis in den Prozessorleistungsindikator und das Samplingintervall in das in `Config` angegebene Intervall.|  
  
## Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie mit **VSPerfCmd.exe**\-Optionen das Schreiben der Daten in die Profiler\-Datendatei starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Paare von **VSPerfCmd**\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |**\/attach:** {`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID oder des Prozessnamens angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein Prozess angegeben ist\) beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler vom Dienst getrennt und dann explizit beendet werden.  Sie können einen systemeigenen Dienst trennen, für den mithilfe der Samplingmethode ein Profil erstellt wurde, indem Sie den Dienst beenden oder indem Sie die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Beenden Sie den Dienst.  
  
         \- oder \-  
  
    -   Geben Sie **VSPerfCmd \/detach** ein.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/shutdown**  
  
## Siehe auch  
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)   
 [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)