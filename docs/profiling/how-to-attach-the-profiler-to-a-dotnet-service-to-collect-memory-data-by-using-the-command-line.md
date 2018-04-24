---
title: 'Vorgehensweise: Anfügen des Profilers an einen .NET-Dienst zum Erfassen von Speicherdaten über die Befehlszeile | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 84e5505b077d4d237ed8f8b2532b4ac2b48544d5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Gewusst wie: Anfügen des Profilers an einen .NET-Dienst zum Sammeln von Speicherdaten über die Befehlszeile
In diesem Artikel wird beschrieben, wie die Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools verwendet werden, um den Profiler an einen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Dienst anzufügen und Speicherdaten zu erfassen. Sie können Daten zur Anzahl und der Größe der Speicherbelegungen erfassen, und Sie können auch Daten zur Lebensdauer von Arbeitsspeicherobjekten erfassen.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind 64-Bit- und 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Um Arbeitsspeicherdaten von einem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Dienst zu erfassen, verwenden Sie das [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)-Tool, um die entsprechenden Umgebungsvariablen auf dem Computer zu initialisieren, der den Dienst hostet. Der Computer muss neu gestartet werden, um ihn für die Profilerstellung zu konfigurieren.  
  
 Sie verwenden dann das [VSPerfCmd](../profiling/vsperfcmd.md)-Tool, um den Profiler an den Dienstprozess anzufügen. Während der Profiler an den Dienst angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler vom Dienst getrennt und explizit beendet werden. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## <a name="attaching-the-profiler"></a>Anfügen des Profilers  
  
#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>So fügen Sie den Profiler an einen .NET Framework-Dienst an  
  
1.  Installieren Sie den Dienst, falls notwendig.  
  
2.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
3.  Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:  
  
     **VSPerfClrEnv** {**/globalsamplegc /globalsamplegclife**}[**/samplelineoff**]  
  
    -   Die Optionen **/globalsamplegclife** und **/globalsamplegclife** geben den Typ der Speicherdaten an, die erfasst werden sollen. Geben Sie eine der folgenden Optionen.  
  
     **/globalsamplegc**  
     Aktiviert die Sammlung von Daten zur Speicherbelegung.  
  
     **/globalsamplegclife**  
     Aktiviert die Sammlung von Daten zur Speicherbelegung und zur Objektlebensdauer.  
  
    -   Die Option **/samplelineoff** deaktiviert die Erfassung der Quellcode-Zeilennummerdaten.  
  
4.  Starten Sie den Computer neu, um die neue Umgebungskonfiguration festzulegen.  
  
5.  Starten Sie den Dienst bei Bedarf.  
  
6.  Öffnen Sie ein Eingabeaufforderungsfenster. Fügen Sie der PATH-Umgebungsvariable den Profilerpfad falls notwendig hinzu.  
  
7.  Starten Sie den Profiler. Typ:  
  
     **VSPerfCmd** [/start](../profiling/start.md) **:sample** [/output](../profiling/output.md) **:** `OutputFile` [`Options`]  
  
    -   Mit der Option **/start:sample** wird der Profiler initialisiert.  
  
    -   Die Option **/output:**`OutputFile` ist für **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  
  
     Sie können mindestens eine der folgenden Optionen zusammen mit der Option **/start:sample** verwenden.  
  
    > [!NOTE]
    >  Die Option **/user** und **/crosssession** sind normalerweise für Dienste erforderlich.  
  
    |Option|description|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des Prozesses ist. Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.|  
    |[/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen. Diese Option ist erforderlich, wenn die ASP.NET-Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte „Prozesse“ in der Spalte „Sitzungs-ID“ des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden.|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Gibt den optionalen Domänen- und Benutzernamen des Anmeldekontos an, unter dem der Dienst ausgeführt wird. Das Anmeldekonto ist in der Spalte "Anmelden als" des Diensts im Windows Dienststeuerungs-Manager aufgeführt.|  
    |[/crosssession|cs](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|  
  
8.  Fügen Sie den Profiler an den Dienst an. Typ:  
  
     **VSPerfCmd** [/attach](../profiling/attach.md) **:**{`PID`|`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  
  
    -   Geben Sie entweder die Prozess-ID oder den Prozessnamen des Diensts an. Die Prozess-IDs und die Namen aller aktiven Prozesse werden im Windows Task-Manager angezeigt.  
  
    -   **/targetclr:** `Version` gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere Laufzeitversionen geladen wurden. Dies ist optional.  
  
## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Wenn der Dienst ausgeführt wird, können Sie die **VSPerfCmd.exe**-Optionen verwenden, um das Schreiben der Daten in die Profilerdatendatei zu starten und zu beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Optionenpaare **VSPerfCmd** starten und beenden die Datensammlung. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet (**/globalon**) oder beendet (**/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet (**/processon**) oder beendet (**/processoff**).|  
    |**/attach:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[:{`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess-ID oder des Prozessnamens angegeben ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess, oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist, beendet.|  
  
## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen. Sie können die Auflistung der Daten von einer Anwendung beenden, die mit der Samplingmethode profiliert wurde, indem Sie den Dienst beenden oder die **VSPerfCmd /detach**-Option aufrufen. Rufen Sie anschließend die Option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Der Befehl **VSPerfClrEnv /globaloff** löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.  
  
#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Beenden Sie den Dienst.  
  
         - oder -   
  
    -   Geben Sie **VSPerfCmd /detach** ein.  
  
2.  Schließen Sie den Profiler. Typ:  
  
     **VSPerfCmd /shutdown**  
  
3.  (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:  
  
     **VSPerfClrEnv /globaloff**  
  
4.  Starten Sie den Computer neu.  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)   
 [.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)