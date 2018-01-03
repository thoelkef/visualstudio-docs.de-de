---
title: "Vorgehensweise: Anfügen des Profilers an einen eigenständigen Dienst zum Sammeln von Parallelitätsdaten über die Befehlszeile | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d0906a567d71bb1f200803e1a3933ee7bad64f0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Gewusst wie: Anfügen des Profilers an einen eigenständigen Dienst zum Sammeln von Parallelitätsdaten über die Befehlszeile
In diesem Thema wird beschrieben, wie der Profiler mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Profilerstellungstools an einen nativen Dienst (C/C++) angefügt wird und Parallelitätsdaten für Prozesse und Threads mit der Samplingmethode erfasst werden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis „\Team Tools\Performance Tools“ des Visual Studio-Installationsverzeichnisses. Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie den Profiler an einer Eingabeaufforderung verwenden können, müssen Sie der PATH-Umgebungsvariable in der **Eingabeaufforderung** oder dem Befehl selbst den Pfad des Tools hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Während der Profiler an den Dienst angefügt ist, können Sie die Datensammlung anhalten und fortsetzen. Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an den Dienst angefügt sein und muss explizit beendet werden.  
  
## <a name="attaching-the-profiler"></a>Anfügen des Profilers  
 Wenn Sie den Profiler an einen nativen Dienst anfügen möchten, verwenden Sie die Optionen **VSPerfCmd/start** und **/attach**, um den Profiler zu initialisieren und an die Zielanwendung anzufügen. Sie können **/start** und **/attach** sowie die zugehörigen Optionen in einer einzigen Befehlszeile angeben. Sie können auch die **/globaloff**-Option hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten. Zum Starten der Datensammlung verwenden Sie anschließend **/globalon**.  
  
#### <a name="to-attach-the-profiler-to-a-native-service"></a>So fügen Sie den Profiler an einen systemeigenen Dienst an  
  
1.  Wenn der Dienst nicht ausgeführt wird, starten Sie ihn.  
  
2.  Starten Sie den Profiler, indem Sie Folgendes an einer Eingabeaufforderung eingeben:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **/start:concurrency   /output:** `OutputFile` [`Options`]  
  
    -   Die Option [/output](../profiling/output.md)**:**`OutputFile` ist zusammen mit **/start** erforderlich. Das `OutputFile`-Objekt gibt den Namen und den Speicherort der Profilerstellungs-Datendatei (.vsp) an.  
  
     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der Option **/start** verwenden.  
  
    > [!NOTE]
    >  Die meisten Dienste erfordern sowohl die Option **/user** als auch **/crosssession**.  
  
    |Option|description|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain\`]`UserName`|Gibt den optionalen Domänen- und Benutzernamen des Kontos an, dem Zugriff auf den Profiler gewährt werden soll.|  
    |[/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|  
  
3.  Fügen Sie den Profiler an den Dienst an, indem Sie den folgenden Befehl an einer Eingabeaufforderung eingeben:  
  
     **VSPerfCmd /attach:** `PID`  
  
     `PID` gibt die Prozess-ID oder den Prozessnamen der Zielanwendung an. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.  
  
## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei über VSPerfCmd.exe-Optionen starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  
  
-   Mit den Optionspaaren in der folgenden Tabelle wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|description|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet (**/globalon**) oder beendet (**/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet (**/processon**) oder beendet (**/processoff**).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess-ID (`PID`) oder des Prozessnamens (*ProcName*) angegeben ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein Prozess angegeben ist) beendet.|  
  
## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen. Sie können das Sammeln von Daten aus einem nativen Dienst, für den mit der Parallelitätsmethode ein Profil erstellt wurde, anhalten, indem Sie den Dienst beenden oder die Option **VSPerfCmd /detach** aufrufen. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen.  
  
#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  
  
1.  Trennen Sie den Profiler von der Zielanwendung, indem Sie den Dienst beenden oder an einer Eingabeaufforderung den folgenden Befehl eingeben:  
  
     Geben Sie **VSPerfCmd /detach** ein.  
  
2.  Beenden Sie den Profiler, indem Sie den folgenden Befehl an der Eingabeaufforderung eingeben:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)