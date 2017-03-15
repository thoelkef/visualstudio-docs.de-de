---
title: "Gewusst wie: Anf&#252;gen des Profilers an eine eigenst&#228;ndige .NET Framework-Anwendung und Sammeln von Anwendungsdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
caps.latest.revision: 34
caps.handback.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an eine eigenst&#228;ndige .NET Framework-Anwendung und Sammeln von Anwendungsdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools verwendet werden, um den Profiler an eine aktive eigenständige .NET Framework\-\(Client\-\)Anwendung anzufügen und mithilfe der Samplingmethode Leistungsstatistikdaten zu sammeln.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools.  Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Um Leistungsdaten von einer .NET Framework\-Anwendung zu erfassen, müssen Sie vor dem Starten der Zielanwendung die entsprechenden Umgebungsvariablen initialisieren.  Wenn der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden.  In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Profilerstellungssitzung zu entfernen.  
  
## Anfügen des Profilers  
  
#### So fügen Sie den Profiler an eine aktive .NET Framework\-Anwendung an  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Initialisieren Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv \/sampleon** \[**\/samplelineoff**\]  
  
    -   Die **\/samplelineoff**\-Option deaktiviert die Auflistung der Quellcode\-Zeilennummerndaten.  
  
3.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   Mit der [\/start](../profiling/start.md)**:sample**\-Option wird der Profiler initialisiert.  
  
    -   Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:sample**\-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die optionale Domäne und den Benutzernamen des Kontos an, das den profilierten Prozess besitzt.  Diese Option ist nur erforderlich, wenn die profilierte Anwendung mit einem anderen Benutzer als dem angemeldeten Benutzer gestartet wurde.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.  Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
4.  Starten Sie die Zielanwendung in der üblichen Weise falls notwendig.  
  
5.  Fügen Sie den Profiler an die Zielanwendung an.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/attach:**{`PID`&#124;`ProcessName`} \[`Sample Event`\] \[**\/targetclr:**`Version`\]  
  
    -   `PID` gibt die Prozess\-ID der Zielanwendung an.  `ProcessName` gibt den Namen des Prozesses an.  Beachten Sie, dass unvorhersehbare Ergebnissen ausgegeben werden können, wenn Sie `ProcessName` angeben und mehrere Prozesse mit dem gleichen Namen ausgeführt werden.  Die Prozess\-IDs aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn in einer Anwendung mehrere Laufzeitversionen geladen wurden.  Optional.  
  
    -   Standardmäßig wird alle 10.000.000 nicht angehaltene Prozessortaktzyklen ein Sampling der Leistungsdaten durchgeführt.  Dies entspricht bei einem 1\-GHz\-Prozessor etwa einem Mal alle 10 Sekunden.  Sie können eine der folgenden Optionen angeben, um das Taktzyklusintervall zu ändern oder ein anderes Samplingereignis anzugeben.[\/targetclr](../profiling/targetclr.md)**:**`Version` gibt die Version der CLR für die Profilerstellung an, wenn in einer Anwendung mehrere Laufzeitversionen geladen wurden.  Optional.  
  
    |||  
    |-|-|  
    |Samplingereignis|**Beschreibung**|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Ändert das Samplingintervall auf die Anzahl der mit `Interval` angegebenen nicht angehaltenen Taktzyklen.|  
    |[\/pf](../profiling/pf.md) \[**:**`Interval`\]|Ändert das Samplingereignis in Seitenfehler.  Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Seitenfehler zwischen den Samplings angegeben.  Der Standardwert ist 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|Ändert das Samplingereignis in Systemaufrufe des Prozesses an den Betriebssystem\-Kernel \(syscalls\).  Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Aufrufe zwischen den Samplings angegeben.  Der Standardwert ist 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Ändert das Samplingereignis auf den Prozessorleistungsindikator und das Samplingintervall in das in `Config` angegebene Intervall.|  
  
## Steuern der Datenauflistung  
 Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Profiler\-Datendatei mit **VSPerfCmd.exe**\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den über die `PID` angegebenen Prozess.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der `PID` oder des Prozessnamens \(ProcName\) angegeben wurde.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist\) beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Prozessen getrennt und explizit beendet werden.  Den Profiler können Sie von einer Anwendung trennen, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie die Anwendung schließen oder die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Mit dem **VSPerfClrEnv \/off**\-Befehl werden die Umgebungsvariablen für die Profilerstellung gelöscht.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Geben Sie **VSPerfCmd \/detach** ein.  
  
         \- oder \-  
  
    -   Schließen Sie die Zielanwendung.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
3.  \(Optional\) Löschen Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv \/off**  
  
## Siehe auch  
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)