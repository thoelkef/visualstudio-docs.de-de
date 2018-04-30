---
title: 'Vorgehensweise: Instrumentieren einer dynamisch kompilierten ASP.NET-Webanwendung und Sammeln ausführlicher Zeitdaten über die Profiler-Befehlszeile | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 7c1f3073b1b3ebeb142805e5d34097c82e038e67
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line"></a>Gewusst wie: Instrumentieren einer dynamisch kompilierten ASP.NET-Webanwendung und Sammeln ausführlicher Zeitsteuerungsdaten über die Profiler-Befehlszeile

In diesem Artikel erfahren Sie, wie Sie Befehlszeilentools der Visual Studio-Profilerstellungstools verwenden können, um mithilfe der Instrumentierungsprofilerstellungsmethode ausführliche Zeitdaten für eine dynamisch kompilierte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Anwendung zu erfassen.

> [!NOTE]
> Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).

Wenn Sie Leistungsdaten aus einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung erfassen möchten, müssen Sie die web.config-Datei der Zielanwendung bearbeiten, um das [VSInstr.exe](../profiling/vsinstr.md)-Tool zu aktivieren, damit die Dateien der dynamisch kompilierten Anwendung instrumentiert werden können. Verwenden Sie anschließend das [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)-Tool, um auf dem Webserver passende Umgebungsvariablen festzulegen, über die die Profilerstellung aktiviert werden kann. Starten Sie den Computer anschließend neu.

Starten Sie den Profiler, und führen Sie dann die Zielanwendung aus. Während der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen. Wenn Sie die Profilerstellung abgeschlossen haben, schließen Sie die Anwendung und den Workerprozess für Internetinformationsdienste (Internet Information Services, IIS). Fahren Sie anschließend den Profiler herunter. Wenn Sie die Profilerstellung abgeschlossen haben, stellen Sie den ursprünglichen Zustand der web.config-Datei und des Webservers wieder her.

## <a name="configuring-the-aspnet-web-application-and-the-web-server"></a>Konfigurieren der ASP-NET-Webanwendungen und des Webservers

1. Bearbeiten Sie die web.config-Datei der Zielanwendung. Weitere Informationen finden Sie unter [Vorgehensweise: Bearbeiten von web.config-Dateien zur Instrumentierung und Profilerstellung für dynamisch kompilierte ASP.NET-Webanwendungen](../profiling/how-to-modify-web-config-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications.md).

2. Öffnen Sie ein Eingabeaufforderungsfenster.

3. Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:

     **VSPerfClrEnv /globaltraceon**

    - **/globaltraceon** aktiviert die Profilerstellung mithilfe der Instrumentierungsmethode.

4. Starten Sie den Computer neu.

## <a name="running-the-profiling-session"></a>Ausführen der Profilerstellungssitzung

1. Öffnen Sie ein Eingabeaufforderungsfenster.

2. Starten Sie den Profiler. Typ:

     **VSPerfCmd** [/start](../profiling/start.md) **:trace** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]

    - Mit der Option **/start:trace** wird der Profiler initialisiert.

    - Die Option **/output:**`OutputFile` ist für **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.

     Sie können jede der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.

    > [!NOTE]
    > Die Optionen **/user** und **/crosssession** sind normalerweise für ASP.NET-Anwendungen erforderlich.

    |Option|description|
    |------------|-----------------|
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET-Arbeitsprozesses ist. Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.|
    |[/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen. Diese Option ist erforderlich, wenn die ASP.NET-Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte „Prozesse“ in der Spalte „Sitzungs-ID“ des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden.|
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Startet den Profiler mit angehaltener Datensammlung. Mit[/globalon](../profiling/globalon-and-globaloff.md) setzen Sie die Profilerstellung fort.|
    |[/counter](../profiling/counter.md) **:** `Config`|Sammelt Informationen aus dem in `Config` angegebenen Prozessorleistungsindikator. Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden.|
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.|
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|

3. Starten Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung auf die gewohnte Weise.

## <a name="controlling-data-collection"></a>Steuern der Datenauflistung

Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Profiler-Datendatei mit **VSPerfCmd.exe**-Optionen starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.

- Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.

    |Option|description|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet (**/globalon**) oder beendet (**/globaloff**).|
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet (**/processon**) oder beendet (**/processoff**).|
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet (**/threadon**) oder beendet (**/threadoff**).|

- Sie können auch die Option **VSPerfCmd.exe**[/mark](../profiling/mark.md) verwenden, um eine Profilmarkierung in die Datendatei einzufügen. Der Befehl **/mark** fügt einen Bezeichner, einen Zeitstempel und eine optionale benutzerdefinierte Textzeichenfolge hinzu. Mit Markierungen können die Daten in Profilerberichten und Datenansichten gefiltert werden.

## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung

Wenn Sie eine Profilerstellungssitzung beenden möchten, schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Zielwebanwendung, und setzen Sie die IIS zurück, um den Profilerstellungsprozess zu beenden. Fahren Sie anschließend den Profiler herunter.

1. Schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung.

2. Schließen Sie den Workerprozess [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], indem Sie die IIS zurücksetzen. Typ:

     **IISReset /stop**

3. Schließen Sie den Profiler. Typ:

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)

4. Starten Sie die IIS neu. Typ:

     **IISReset /start**

## <a name="restoring-the-application-and-computer-configuration"></a>Wiederherstellen der Anwendungs- und Computerkonfiguration

Wenn Sie die Profilerstellung abgeschlossen haben, ersetzen Sie die web.config-Datei, löschen Sie die Umgebungsvariablen für die Profilerstellung, und starten Sie den Computer neu, um den ursprünglichen Zustand (Zustand vor der Profilerstellung) der Anwendung und des Servers wiederherzustellen.

1. Ersetzen Sie die web.config-Datei durch eine Kopie der ursprünglichen Datei.

2. Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:

     **VSPerfCmd /globaloff**

3. Starten Sie den Computer neu.

## <a name="see-also"></a>Siehe auch

[Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
[Datenansichten der Instrumentierungsmethode](../profiling/instrumentation-method-data-views.md)