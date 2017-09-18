---
title: "Gewusst wie: Anf&#252;gen des Profilers an einen .NET-Dienst zum Sammeln von Anwendungsstatistiken &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an einen .NET-Dienst zum Sammeln von Anwendungsstatistiken &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie der Profiler mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools an einen .NET Framework\-Dienst angefügt wird und wie Sie mit der Samplingmethode Leistungsstatistiken sammeln können.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Um die Profiler\-Befehlszeilentools zu verwenden, müssen Sie den Toolpfad der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools.  Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Wenn Sie Leistungsdaten von einem .NET Framework\-Dienst erfassen möchten, müssen Sie das Tool [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) verwenden, um die entsprechenden Umgebungsvariablen zu initialisieren.  Sie müssen dann den Computer neu starten, der den Dienst hostet, und diesen Computer zur Profilerstellung konfigurieren.  Sie fügen dann den Profiler an den Dienstprozess an.  Während der Profiler an den Dienst angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler vom Dienst getrennt und explizit beendet werden.  In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## Anfügen des Profilers  
  
#### So fügen Sie den Profiler an einen .NET Framework\-Dienst an  
  
1.  Installieren Sie den Dienst.  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
3.  Initialisieren Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv \/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** aktiviert das Sampling.  
  
    -   **\/samplelineoff** deaktiviert die Zuweisung gesammelter Daten zu bestimmten Quellcodezeilen.  Wenn diese Option angegeben wird, werden Daten nur Funktionen zugewiesen.  
  
4.  Starten Sie den Computer neu.  
  
5.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
6.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   Mit der **\/start:sample**\-Option wird der Profiler initialisiert.  
  
    -   Die **\/output:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:sample**\-Option verwenden.  
  
    > [!NOTE]
    >  Die **\/user**\-Option und die **\/crosssession**\-Option sind normalerweise für Dienste erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist.  Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen.  Diese Option ist erforderlich, wenn der Dienst in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte "Prozesse" in der Spalte "Sitzungs\-ID" des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
7.  Starten Sie den Dienst bei Bedarf.  
  
8.  Fügen Sie den Profiler an den Dienst an.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} \[`Sample Event`\] \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   Geben Sie die Prozess\-ID \(`PID`\) oder den Prozessnamen \(ProcName\) des Diensts an.  Die Prozess\-IDs und die Namen aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
     Standardmäßig wird alle 10.000.000 nicht angehaltene Prozessortaktzyklen ein Sampling der Leistungsdaten durchgeführt.  Bei einem 1\-GHz\-Prozessor entspricht dies etwa 100 Samplings pro Sekunde.  Sie können eine der folgenden Optionen angeben, um das Taktzyklusintervall zu ändern oder ein anderes Samplingereignis anzugeben.  
  
    |Samplingereignis|**Beschreibung**|  
    |----------------------|----------------------|  
    |[\/timer](../profiling/timer.md) **:** `Interval`|Ändert das Samplingintervall in die Anzahl der mit `Interval` angegebenen nicht angehaltenen Taktzyklen.|  
    |[\/pf](../profiling/pf.md)\[**:**`Interval`\]|Ändert das Samplingereignis in Seitenfehler.  Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Seitenfehler zwischen den Samplings angegeben.  Der Standardwert ist 10.|  
    |[\/sys](../profiling/sys-vsperfcmd.md)\[`:``Interval`\]|Ändert das Samplingereignis in Systemaufrufe des Prozesses an den Betriebssystem\-Kernel \(syscalls\).  Wenn `Interval` angegeben wird, wird dadurch die Anzahl der Aufrufe zwischen den Samplings angegeben.  Der Standardwert ist 10.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Ändert das Samplingereignis in den Prozessorleistungsindikator und das Samplingintervall in das in `Config` angegebene Intervall.|  
  
    -   **targetclr:** `Version` gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn mehr als eine Laufzeitversion in eine Anwendung geladen wird.  Optional.  
  
## Steuern der Datenauflistung  
 Wenn der Dienst ausgeführt wird, können Sie die **VSPerfCmd.exe**\-Optionen verwenden, um das Schreiben der Daten in die Profilerdatendatei zu starten und zu beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Paare von **VSPerfCmd**\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID oder des Prozessnamens angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist\) beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Prozessen getrennt und explizit beendet werden.  Sie können den Profiler von einer mit der Samplingmethode profilierten Anwendung trennen, indem Sie die Anwendung schließen oder die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  
  
 Der **VSPerfClrEnv \/globaloff**\-Befehl löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Beenden Sie den Dienst.  
  
         \- oder \-  
  
    -   Geben Sie **VSPerfCmd \/detach** ein.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Optional\) Löschen Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv \/globaloff**  
  
4.  Starten Sie den Computer neu.  
  
## Siehe auch  
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)   
 [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)