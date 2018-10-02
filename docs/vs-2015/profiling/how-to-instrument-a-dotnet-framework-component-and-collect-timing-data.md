---
title: 'Vorgehensweise: Instrumentieren einer eigenständigen .NET Framework-Komponente und Sammeln von Zeitdaten über die Befehlszeile mit dem Profiler | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d9c7083b46b6f59d28c56724722b2ea591e971b
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590507"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Gewusst wie: Instrumentieren einer eigenständigen .NET Framework-Komponente und Sammeln von Zeitsteuerungsdaten über die Befehlszeile mit dem Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Instrumentieren einer eigenständigen .NET Framework-Komponente und Sammeln von Zeitsteuerungsdaten über die Profiler über die Befehlszeile](https://docs.microsoft.com/visualstudio/profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line).  
  
In diesem Artikel wird beschrieben, wie die zu den [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools gehörenden Befehlszeilentools zum Instrumentieren einer .NET Framework-Komponente (z.B. eine EXE- oder DLL-Datei) verwendet und ausführliche Zeiterfassungsdaten gesammelt werden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools. Informationen hierzu finden Sie unter [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Wenn Sie ausführliche Zeitdaten einer .NET Framework-Komponente mit der Instrumentierungsmethode erfassen möchten, verwenden Sie das Tool [VSInstr.exe](../profiling/vsinstr.md), um eine instrumentierte Version der Komponente und des [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)-Tools zu generieren und Umgebungsvariablen für die Profilerstellung zu initialisieren. Starten Sie dann den Profiler.  
  
 Wenn die instrumentierte Komponente ausgeführt wird, werden Zeitsteuerungsdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Zielanwendung, und schließen Sie danach den Profiler. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## <a name="starting-the-profiling-session"></a>Starten der Profilerstellungssitzung  
  
#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>So starten Sie die Profilerstellung mit der Instrumentationsmethode  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster. Fügen Sie der PATH-Umgebungsvariable das Profiler-Toolsverzeichnis falls notwendig hinzu. Der Pfad wird bei der Installation nicht hinzugefügt.  
  
2.  Generieren Sie mit dem Tool **VSInstr** eine instrumentierte Version der Zielanwendung.  
  
3.  Initialisieren Sie die .NET Framework-Umgebungsvariablen für die Profilerstellung. Typ:  
  
     **VSPerfClrEnv /traceon**  
  
4.  Starten Sie den Profiler. Typ:  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   Mit der Option [/start](../profiling/start.md)**:trace** wird der Profiler initialisiert.  
  
    -   Die Option [/output](../profiling/output.md)**:**`OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  
  
     Sie können jede der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.  
  
    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.|  
    |[/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die ASP.NET-Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs-ID des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Startet den Profiler mit angehaltener Datensammlung. Mit[/globalon](../profiling/globalon-and-globaloff.md) setzen Sie die Profilerstellung fort.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Sammelt Informationen aus dem in `Config` angegebenen Prozessorleistungsindikator. Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|  
  
5.  Starten Sie die Zielanwendung über das Eingabeaufforderungsfenster.  
  
## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Profiler-Datendatei mit Optionen **VSPerfCmd.exe** starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  
  
-   Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet (**/globalon**) oder beendet (**/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet (**/processon**) oder beendet (**/processoff**).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet (**/threadon**) oder beendet (**/threadoff**).|  
  
## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Anwendung, die die instrumentierte Komponente ausführt. Rufen Sie die Option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /off** werden die Umgebungsvariablen für die Profilerstellung gelöscht.  
  
#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  
  
1.  Schließen Sie die Zielanwendung.  
  
2.  Schließen Sie den Profiler. Typ:  
  
     **VSPerfCmd /shutdown**  
  
3.  (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:  
  
     **VSPerfClrEnv /off**  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Datenansichten der Instrumentierungsmethode](../profiling/instrumentation-method-data-views.md)



