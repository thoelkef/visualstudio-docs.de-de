---
title: "Gewusst wie: Anf&#252;gen des Profilers an eine systemeigene, eigenst&#228;ndige .NET Framework-Anwendung und Sammeln von Anwendungsdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df44fe42-281b-4398-b3fc-277b62ae41f1
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an eine systemeigene, eigenst&#228;ndige .NET Framework-Anwendung und Sammeln von Anwendungsdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools verwendet werden, um den Profiler an eine ausgeführte eigenständige und systemeigene .NET Framework\-\(Client\-\)Anwendung anzufügen und Leistungsstatistik mithilfe der Samplingmethode zu sammeln.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Wenn der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden.  
  
## Anfügen des Profilers  
 Verwenden Sie zum Anfügen des Profilers an eine Zielanwendung mit dem Profiler die **VSPerfCmd**\-Optionen **\/start** und **\/attach**, um den Profiler zu initialisieren und an die Zielanwendung anzufügen.  Sie können **\/start** und **\/attach** sowie die zugehörigen Optionen in einer einzigen Befehlszeile angeben.  Sie können auch die **\/globaloff**\-Option hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten.  Dann starten Sie die Datensammlung mit **\/globalon**.  
  
#### So fügen Sie den Profiler an eine aktive .NET Framework\-Anwendung an  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   Mit der [\/start](../profiling/start.md)**:sample** \-Option wird der Profiler initialisiert.  
  
    -   Die Option [\/output](../profiling/output.md)**:**`OutputFile` ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:sample** \-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist.  Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen.  Diese Option ist erforderlich, wenn die ASP.NET\-Anwendung in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs\-ID des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
3.  Fügen Sie den Profiler an die Zielanwendung an.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[`Sample Event`\]  
  
     `PID` gibt die Prozess\-ID der Zielanwendung an.  `ProcessName` gibt den Namen des Prozesses an.  Beachten Sie, dass unvorhersehbare Ergebnissen ausgegeben werden können, wenn Sie `ProcessName` angeben und mehrere Prozesse mit dem gleichen Namen ausgeführt werden.  Die Prozess\-IDs aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
     Standardmäßig wird alle 10.000.000 nicht angehaltene Prozessortaktzyklen ein Sampling der Leistungsdaten durchgeführt.  Bei einem 1\-GHz\-Prozessor entspricht dies etwa 100 Mal pro Sekunde.  Sie können eine der folgenden Optionen angeben, um das Taktzyklusintervall zu ändern oder ein anderes Samplingereignis anzugeben.  
  
    |Samplingereignis|**Beschreibung**|  
    |----------------------|----------------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Ändert das Samplingintervall auf die Anzahl der mit `Interval` angegebenen nicht angehaltenen Taktzyklen.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Ändert das Samplingereignis in Seitenfehler.  Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Seitenfehler zwischen den Samplings angegeben.  Der Standardwert ist 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md) \[**:**`Interval`\]|Ändert das Samplingereignis in Systemaufrufe des Prozesses an den Betriebssystem\-Kernel \(syscalls\).  Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Aufrufe zwischen den Samplings angegeben.  Der Standardwert ist 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Ändert das Samplingereignis auf den Prozessorleistungsindikator und das Samplingintervall in das in `Config` angegebene Intervall.|  
  
## Steuern der Datenauflistung  
 Wenn die Zielanwendung ausgeführt wird, können Sie mit VSPerfCmd.exe\-Optionen das Schreiben der Daten in die Profilerdatendatei starten und beenden.  Durch die Steuerung der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Paare von **VSPerfCmd**\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den über die `PID` angegebenen Prozess.|  
    |[\/attach](../profiling/attach.md) **:** `PID` [\/detach](../profiling/detach.md)|Mit **\/attach** wird die Datensammlung für den über die `PID` \(Prozess\-ID\) angegebenen Prozess gestartet.  Mit **\/detach** wird die Datensammlung für alle Prozesse beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Prozessen getrennt und explizit beendet werden.  Den Profiler können Sie von einer Anwendung trennen, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie die Anwendung schließen oder die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Mit dem **VSPerfClrEnv \/off**\-Befehl werden die Umgebungsvariablen für die Profilerstellung gelöscht.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen.  
  
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