---
title: "Vorgehensweise: Instrumentieren einer statisch kompilierten ASP.NET-Webanwendung und Sammeln von Speicherdaten über die Profiler-Befehlszeile | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea1dcb7c-1dc3-49ff-9418-8795b5b3d3bc
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5a35d15fc4d0859ca005cff96aab51f9c5fbd277
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line"></a>Gewusst wie: Instrumentieren einer statisch kompilierten ASP.NET-Webanwendung und Sammeln von Speicherdaten über die Profiler-Befehlszeile
In diesem Thema wird beschrieben, wie die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools verwendet werden, um eine vorkompilierte [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webkomponente oder -Website zu instrumentieren und Daten zur .NET-Speicherbelegung und zur Objektlebensdauer sowie ausführliche Zeitsteuerungsdaten zu sammeln.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind 64-Bit- und 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Um Daten aus einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webkomponente mithilfe der Instrumentierungsmethode zu erfassen, generieren Sie mit dem Tool [VSInstr.exe](../profiling/vsinstr.md) eine instrumentierte Version der Komponente. Auf dem Computer, der die Komponente hostet, müssen Sie die nicht instrumentierte Version der Komponente durch die instrumentierte Version ersetzen. Mit [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) können Sie die globalen Umgebungsvariablen für die Profilerstellung initialisieren und den Hostcomputer neu starten. Starten Sie dann den Profiler.  
  
 Wenn die instrumentierte Komponente ausgeführt wird, werden Zeitsteuerungsdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  
  
 Wenn Sie eine Profilerstellungssitzung beenden möchten, schließen Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Workerprozess, der die Komponente hostet, und anschließend explizit den Profiler. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## <a name="starting-to-profile"></a>Starten der Profilerstellung  
  
#### <a name="to-instrument-an-aspnet-web-component-and-start-profiling"></a>So instrumentieren Sie eine ASP.NET-Webkomponente und starten die Profilerstellung  
  
1.  Generieren Sie mit dem Tool **VSInstr** eine instrumentierte Version der Zielanwendung. Ersetzen Sie die Anwendungsbinärdateien auf dem ASP.NET-Hostcomputer falls notwendig durch die instrumentierten Binärdateien.  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
3.  Initialisieren Sie die .NET-Umgebungsvariablen für die Profilerstellung. Geben Sie im Eingabeaufforderungsfenster Folgendes ein:  
  
     **VSPerfClrEnv /globaltracegc**  
  
     - oder -   
  
     **VSPerfClrEnv /globaltracegclife**  
  
    -   **/globaltracegc** sammelt Daten zur .NET-Speicherbelegung sowie zur Zeitsteuerung.  
  
    -   **/globaltracegclife** sammelt Daten zur .NET-Speicherbelegung, Objektlebensdauer sowie ausführliche Zeitsteuerungsdaten.  
  
4.  Starten Sie den Computer neu.  
  
5.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
6.  Starten Sie den Profiler. Geben Sie im Eingabeaufforderungsfenster Folgendes ein:  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   Mit der Option [/start](../profiling/start.md)**:trace** wird der Profiler initialisiert.  
  
    -   Die Option [/output](../profiling/output.md)**:**`OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  
  
     Sie können jede der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.  
  
    > [!NOTE]
    >  Die Optionen **/user** und **/crosssession** sind normalerweise für ASP.NET-Anwendungen erforderlich.  
  
    |Option|description|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Gibt den optionalen Domänen- und Benutzernamen des Kontos an, das Besitzer des ASP.NET-Arbeitsprozesses ist. Diese Option ist erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der mit dem angemeldeten Benutzer nicht identisch ist. Der Name wird im Windows Task-Manager auf der Registerkarte Prozesse in der Spalte Benutzername angezeigt.|  
    |[/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte „Prozesse“ in der Spalte „Sitzungs-ID“ des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Fügen Sie der Befehlszeile **/start** die Option **globaloff** hinzu, um den Profiler mit angehaltener Datensammlung zu starten. Mit**/globalon** setzen Sie die Profilerstellung fort.|  
  
7.  Öffnen Sie die Website, die die instrumentierte Komponente enthält.  
  
## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit Option **VSPerfCmd.exe** starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  
  
-   Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet (**/globalon**) oder beendet (**/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet (**/processon**) oder beendet (**/processoff**).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet (**/threadon**) oder beendet (**/threadoff**).|  
  
## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung, um eine Profilerstellungssitzung zu beenden, und verwenden Sie den **IISReset**-Befehl der Internetinformationsdienste (IIS), um den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Workerprozess zu schließen. Rufen Sie die Option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /globaloff** werden die Umgebungsvariablen für die Profilerstellung gelöscht. Sie müssen den Computer neu starten, damit die neuen Umgebungseinstellungen übernommen werden.  
  
#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  
  
1.  Schließen Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Webanwendung.  
  
2.  Schließen Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]-Arbeitsprozess. Typ:  
  
     **IISReset /stop**  
  
3.  Schließen Sie den Profiler. Typ:  
  
     **VSPerfCmd /shutdown**  
  
4.  (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:  
  
     **VSPerfCmd /globaloff**  
  
5.  Starten Sie den Computer neu. Falls erforderlich, starten Sie IIS erneut. Typ:  
  
     **IISReset /start**  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung für ASP.NET-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)