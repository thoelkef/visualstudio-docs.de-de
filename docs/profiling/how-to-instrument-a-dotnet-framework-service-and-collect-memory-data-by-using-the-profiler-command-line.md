---
title: "Gewusst wie: Instrumentieren eines .NET Framework-Diensts und Sammeln von Speicherdaten &#252;ber die Profiler-Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Instrumentieren eines .NET Framework-Diensts und Sammeln von Speicherdaten &#252;ber die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools einen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Dienst instrumentieren und Daten zur Speicherauslastung sammeln können.  Sie können nur Daten zur Speicherbelegung oder Daten zur Speicherbelegung und zur Lebensdauer von Objekten sammeln.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Mit der Instrumentationsmethode kann kein Profil für einen Dienst erstellt werden, wenn der Dienst nach dem Start des Computers nicht neu gestartet werden kann, z. B. ein Dienst, der gleichzeitig mit dem Betriebssystem gestartet wird.  
>   
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Um die Profiler\-Befehlszeilentools zu verwenden, müssen Sie den Toolpfad der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Starten der Profilerstellungssitzung  
 Verwenden Sie zum Sammeln von Leistungsdaten von einem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Dienst das [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)\-Tool, um die entsprechenden Umgebungsvariablen zu initialisieren, und das [VSInstr.exe](../profiling/vsinstr.md)\-Tool, um eine instrumentierte Kopie der Binärdatei des Diensts zu erstellen.  
  
 Der Computer, auf dem der Dienst gehostet wird, muss neu gestartet werden, um ihn für die Profilerstellung zu konfigurieren.  Außerdem müssen Sie den Dienst manuell über den Dienststeuerungs\-Manager starten.  Starten Sie dann den Profiler und anschließend den [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Dienst.  
  
 Wenn die instrumentierte Komponente ausgeführt wird, werden Speicherdaten automatisch in einer Datendatei erfasst.  Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, schließen Sie den Dienst und fahren danach den Profiler selbst herunter.  In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
#### So starten Sie die Profilerstellung für einen .NET Framework\-Dienst  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Generieren Sie mit dem **VSInstr**\-Tool eine instrumentierte Version der Binärdatei des Diensts.  
  
3.  Ersetzen Sie mit dem Dienststeuerungs\-Manager die ursprüngliche Binärdatei durch die instrumentierte Version.  Stellen Sie sicher, dass der Starttyp des Diensts auf Manuell festgelegt ist.  
  
4.  Initialisieren Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv** {**\/globaltracegc** &#124; **\/globaltracegclife**}  
  
    -   **\/globaltracegc** und **\/globaltracegclife** aktivieren die Sammlung von Daten zur Speicherbelegung und zur Objektlebensdauer.  
  
        |Option|**Beschreibung**|  
        |------------|----------------------|  
        |**\/globaltracegc**|Sammelt nur Daten zur Speicherbelegung.|  
        |**\/globaltracegclife**|Sammelt Daten zur Speicherbelegung und zur Objektlebensdauer.|  
  
5.  Starten Sie den Computer neu.  
  
6.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
7.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:trace**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   Mit der **\/start: contention**\-Option wird der Profiler initialisiert.  
  
    -   Die **\/output:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:sample**\-Option verwenden.  
  
    > [!NOTE]
    >  Die **\/user**\-Option und die **\/crosssession**\-Option sind normalerweise für Dienste erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET\-Arbeitsprozesses ist.  Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.  Diese Option ist erforderlich, wenn die ASP.NET\-Anwendung in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte "Prozesse" in der Spalte "Sitzungs\-ID" des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|Gibt die Anzahl der Sekunden an, die auf die Initialisierung des Profilers gewartet werden soll, bevor ein Fehler zurückgegeben wird.  Wenn `Interval` nicht angegeben wird, wartet der Profiler unendlich lange.  Standardmäßig wird **\/start** sofort beendet.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Um den Profiler mit angehaltener Datensammlung zu starten, fügen Sie der **\/start**\-Befehlszeile die **\/globaloff**\-Option hinzu.  Mit **\/globalon** setzen Sie die Profilerstellung fort.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Sammelt Informationen aus dem in Config angegebenen Prozessorleistungsindikator.  Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
8.  Starten Sie den Dienst bei Bedarf.  
  
9. Fügen Sie den Profiler an den Dienst an.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/attach:** `PID` &#124;`ProcessName`  
  
    -   Geben Sie die Prozess\-ID oder den Prozessnamen des Diensts an.  Die Prozess\-IDs und die Namen aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
## Steuern der Datenauflistung  
 Während der Dienst ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit **VSPerfCmd.exe**\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Paare von **VSPerfCmd**\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [\/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID`  [\/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Startet \(**\/threadon**\) oder beendet \(**\/threadoff**\) die Datensammlung für den mit der Thread\-ID \(`TID`\) angegebenen Thread.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Anwendung, die die instrumentierte Komponente ausführt, und starten Sie dann die **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)\-Option, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Mit dem **VSPerfClrEnv \/globaloff**\-Befehl werden die Umgebungsvariablen für die Profilerstellung entfernt.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Beenden Sie den Dienst aus dem Dienststeuerungs\-Manager.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/shutdown**  
  
3.  Wenn Sie alle Profilerstellungsaufgaben abgeschlossen haben, entfernen Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv \/globaloff**  
  
     Ersetzen Sie das instrumentierte Modul durch das Original.  Konfigurieren Sie bei Bedarf den Starttyp des Diensts neu.  
  
4.  Starten Sie den Computer neu.  
  
## Siehe auch  
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)   
 [.NET\-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)