---
title: "Gewusst wie: Instrumentieren einer statisch kompilierten ASP.NET-Webanwendung und Sammeln ausf&#252;hrlicher Zeitsteuerungsdaten &#252;ber die Profiler-Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b260ce68-76e6-4c3b-8062-3c00bd5cf7b8
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Instrumentieren einer statisch kompilierten ASP.NET-Webanwendung und Sammeln ausf&#252;hrlicher Zeitsteuerungsdaten &#252;ber die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools verwendet werden, um eine vorkompilierte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webkomponente oder \-Website zu instrumentieren und ausführliche Zeitsteuerungsdaten zu erfassen.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools.  Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Um ausführliche Zeitsteuerungsdaten aus einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webkomponente mithilfe der Instrumentationsmethode zu erfassen, können Sie mit dem [VSInstr.exe](../profiling/vsinstr.md)\-Tool eine instrumentierte Version der Komponente generieren.  Auf dem Computer, der die Komponente hostet, müssen Sie die nicht instrumentierte Version der Komponente durch die instrumentierte Version ersetzen.  Verwenden Sie anschließend das [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)\-Tool, um die globalen Umgebungsvariablen für die Profilerstellung zu initialisieren und dann den Hostcomputer neu zu starten.  Starten Sie dann den Profiler.  
  
 Wenn die instrumentierte Komponente ausgeführt wird, werden Zeitsteuerungsdaten automatisch in einer Datendatei erfasst.  Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  
  
 Wenn Sie eine Profilerstellungssitzung beenden möchten, müssen Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess schließen, der die Komponente hostet, und dann den Profiler explizit beenden.  In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## Starten der Profilerstellung  
  
#### So instrumentieren Sie eine ASP.NET\-Webkomponente und starten die Profilerstellung  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Generieren Sie mit dem **VSInstr**\-Tool eine instrumentierte Version der Zielanwendung.  Ersetzen Sie die Anwendungsbinärdateien auf dem ASP.NET\-Hostcomputer falls notwendig durch die instrumentierten Binärdateien.  
  
3.  Initialisieren Sie die .NET\-Umgebungsvariablen für die Profilerstellung.  Geben Sie im Fenster Eingabeaufforderung Folgendes ein:  
  
     **VSPerfClrEnv \/globaltraceon**  
  
4.  Starten Sie den Computer neu.  
  
5.  Öffnen Sie ein Eingabeaufforderungsfenster.  Legen Sie den Toolpfad für den Profiler fest, falls notwendig.  
  
6.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   Mit der [\/start](../profiling/start.md)**:trace**\-Option wird der Profiler initialisiert.  
  
    -   Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:trace**\-Option verwenden.  
  
    > [!NOTE]
    >  Die **\/user**\-Option und die **\/crosssession**\-Option sind normalerweise für ASP.NET\-Anwendungen erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET\-Arbeitsprozesses ist.  Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.  Diese Option ist erforderlich, wenn die ASP.NET\-Anwendung in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs\-ID des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Um den Profiler mit angehaltener Datensammlung zu starten, fügen Sie der **\/start**\-Befehlszeile die **\/globaloff**\-Option hinzu.  Mit **\/globalon** setzen Sie die Profilerstellung fort.|  
  
7.  Öffnen Sie die Website, die die instrumentierte Komponente enthält.  
  
## Steuern der Datenauflistung  
 Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit **VSPerfCmd.exe**\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Startet \(**\/threadon**\) oder beendet \(**\/threadoff**\) die Datensammlung für den mit der Thread\-ID \(`TID`\) angegebenen Thread.|  
  
## Beenden der Profilerstellungssitzung  
 Wenn Sie eine Profilerstellungssitzung beenden möchten, schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung, und verwenden Sie den **IISReset**\-Befehl der Internetinformationsdienste \(IIS\), um den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess zu schließen.  Rufen Sie die **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  
  
 Mit dem **VSPerfClrEnv \/globaloff**\-Befehl werden die Umgebungsvariablen für die Profilerstellung entfernt.  Sie müssen den Computer neu starten, damit die neuen Umgebungseinstellungen übernommen werden.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung.  
  
2.  Schließen Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess.  Geben Sie Folgendes ein:  
  
     **IISReset \/stop**  
  
3.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/shutdown**  
  
4.  \(Optional\)  Löschen Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/globaloff**  
  
5.  Starten Sie den Computer neu.  
  
## Siehe auch  
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Instrumentationsmethoden\-Datenansichten](../profiling/instrumentation-method-data-views.md)