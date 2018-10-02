---
title: 'Vorgehensweise: Anfügen des Profilers an eine eigenständige .NET Framework-Anwendung zum Sammeln von Speicherdaten über die Befehlszeile | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a869fa4-3c98-4e08-b5d9-f43523059f0e
caps.latest.revision: 38
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db640119a441a55d05df18391c92ae53af067b51
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2018
ms.locfileid: "47590458"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line"></a>Gewusst wie: Anfügen des Profilers an eine eigenständige .NET Framework-Anwendung zum Sammeln von Speicherdaten über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Anfügen von den Profiler an eine .NET Framework eigenständige Anwendung zum Sammeln von Speicherdaten über die Befehlszeile](https://docs.microsoft.com/visualstudio/profiling/how-to-attach-the-profiler-to-a-dotnet-framework-stand-alone-application-to-collect-memory-data-by-using-the-command-line).  
  
In diesem Thema wird beschrieben, wie der Profiler mit den Befehlszeilentools der [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]-Profilerstellungstools an eine aktive eigenständige .NET Framework-Clientanwendung angefügt wird und Arbeitsspeicherdaten erfasst werden können.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Zum Anfügen an eine .NET Framework-Anwendung und Sammeln von Arbeitsspeicherdaten müssen Sie mit dem Tool [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) die entsprechenden Umgebungsvariablen initialisieren, bevor die Zielanwendung gestartet wird. Wenn der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung mit dem **VSPerfCmd.exe**-Tool anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Prozessen getrennt und explizit beendet werden. In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## <a name="attaching-the-profiler"></a>Anfügen des Profilers  
  
#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>So fügen Sie den Profiler an eine aktive .NET Framework-Anwendung an  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Initialisieren Sie die Umgebungsvariablen für die Profilerstellung. Typ:  
  
     **VSPerfClrEnv** {**/samplegc** | **/samplegclife**} [**/samplelineoff**]  
  
    -   Die Optionen **/samplegc** und **/samplegclife** geben an, ob nur Daten zur Speicherbelegung oder Daten zur Speicherbelegung und der Objektlebensdauer gesammelt werden sollen. Es darf nur eine dieser Optionen angegeben werden.  
  
        |Option|Beschreibungen|  
        |------------|------------------|  
        |**/samplegc**|Es werden nur Daten zur Speicherbelegung gesammelt.|  
        |**/samplegclife**|Es werden Daten zur Speicherbelegung und zur Objektlebensdauer gesammelt.|  
  
    -   Die Option **/samplelineoff** deaktiviert die Erfassung der Quellcode-Zeilennummerdaten.  
  
3.  Starten Sie den Profiler. Typ:  
  
     **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]  
  
    -   Mit der Option [/start](../profiling/start.md)**:sample** wird der Profiler initialisiert.  
  
    -   Die Option [/output](../profiling/output.md)**:**`OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  
  
     Sie können jede der folgenden Optionen zusammen mit der Option **/start:sample** verwenden.  
  
    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.|  
    |[/crosssession | /cs](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs-ID des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.|  
  
4.  Starten Sie die Zielanwendung ggf. in der üblichen Weise.  
  
5.  Fügen Sie den Profiler an die Zielanwendung an. Typ:  
  
     **VSPerfCmd** [/attach](../profiling/attach.md) **:**{`PID`|`ProcName`} [[/targetclr](../profiling/targetclr.md)**:**`Version`]  
  
    -   `PID` gibt die Prozess-ID der Zielanwendung an. `ProcessName` gibt den Namen des Prozesses an. Beachten Sie, dass unvorhersehbare Ergebnissen ausgegeben werden können, wenn Sie `ProcessName` angeben und mehrere Prozesse mit dem gleichen Namen ausgeführt werden. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.  
  
    -   **/targetclr:** `Version` gibt die Version der CLR (Common Language Runtime) für die Profilerstellung an, wenn in einer Anwendung mehrere Laufzeitversionen geladen wurden. Dies ist optional.  
  
## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit Optionen **VSPerfCmd.exe** starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  
  
-   Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet (**/globalon**) oder beendet (**/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den Prozess, der von `PID` angegeben wird, gestartet (**/processon**) oder beendet (**/processoff**).|  
    |[/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[**:**{`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der `PID` oder des Prozessnamens (ProcName) angegeben wurde. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist) beendet.|  
  
## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Prozessen getrennt und explizit beendet werden. Den Profiler können Sie von einer Anwendung trennen, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie die Anwendung schließen oder die Option **VSPerfCmd /detach** aufrufen. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Mit dem Befehl **VSPerfClrEnv /off** werden die Umgebungsvariablen für die Profilerstellung gelöscht.  
  
#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Geben Sie **VSPerfCmd /detach** ein.  
  
         - oder -   
  
    -   Schließen Sie die Zielanwendung.  
  
2.  Schließen Sie den Profiler. Typ:  
  
     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  
  
3.  (Optional) Löschen Sie die Umgebungsvariablen für die Profilerstellung. Typ:  
  
     **VSPerfCmd /off**  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)



