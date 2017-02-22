---
title: "Gewusst wie: Anf&#252;gen des Profilers an einen eigenst&#228;ndigen Dienst zum Sammeln von Parallelit&#228;tsdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an einen eigenst&#228;ndigen Dienst zum Sammeln von Parallelit&#228;tsdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie der Profiler mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools an einen systemeigenen Dienst \(C\/C\+\+\) angefügt wird und Parallelitätsdaten für Prozesse und Threads mit der Samplingmethode erfasst werden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des Visual Studio\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie den Profiler an einer Eingabeaufforderung verwenden können, müssen Sie der PATH\-Umgebungsvariable in der **Eingabeaufforderung** oder dem Befehl selbst den Pfad des Tools hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Während der Profiler an den Dienst angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an den Dienst angefügt sein und muss explizit beendet werden.  
  
## Anfügen des Profilers  
 Verwenden Sie zum Anfügen des Profilers an einen systemeigenen Dienst die **VSPerfCmd**\-Optionen **\/start** und **\/attach**, um den Profiler zu initialisieren und an die Zielanwendung anzufügen.  Sie können **\/start** und **\/attach** sowie die zugehörigen Optionen in einer einzigen Befehlszeile angeben.  Sie können auch die **\/globaloff**\-Option hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten.  Zum Starten der Datensammlung verwenden Sie dann das **\/globalon**\-Objekt.  
  
#### So fügen Sie den Profiler an einen systemeigenen Dienst an  
  
1.  Wenn der Dienst nicht ausgeführt wird, starten Sie ihn.  
  
2.  Starten Sie den Profiler, indem Sie Folgendes an einer Eingabeaufforderung eingeben:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
    -   Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und den Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der **\/start** \-Option verwenden.  
  
    > [!NOTE]
    >  Für die meisten Dienste sind die **\/user**\-Option und die **\/crosssession**\-Option erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|Gibt den optionalen Domänen\- und Benutzernamen des Kontos an, dem Zugriff auf den Profiler gewährt werden soll.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
3.  Fügen Sie den Profiler an den Dienst an, indem Sie den folgenden Befehl an einer Eingabeaufforderung eingeben:  
  
     **VSPerfCmd \/attach:** `PID`  
  
     `PID` gibt die Prozess\-ID oder den Prozessnamen der Zielanwendung an.  Die Prozess\-IDs aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
## Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei über VSPerfCmd.exe\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Mit den Optionspaaren in der folgenden Tabelle wird die Datensammlung gestartet und beendet.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID \(`PID`\) oder des Prozessnamens \(*ProcName*\) angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein Prozess angegeben ist\) beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen.  Sie können das Sammeln von Daten aus einem systemeigenen Dienst, für den mit der Parallelitätsmethode ein Profil erstellt wurde, anhalten, indem Sie den Dienst beenden oder die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Trennen Sie den Profiler von der Zielanwendung, indem Sie den Dienst beenden oder an einer Eingabeaufforderung den folgenden Befehl eingeben:  
  
     Geben Sie **VSPerfCmd \/detach** ein.  
  
2.  Beenden Sie den Profiler, indem Sie den folgenden Befehl an der Eingabeaufforderung eingeben:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)