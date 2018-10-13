---
title: 'Vorgehensweise: Instrumentieren einer nativen, eigenständigen Komponente und Sammeln von Zeitsteuerungsdaten über die Befehlszeile mit dem Profiler'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 36883074-9be8-4e90-a66f-7e87f21fcd30
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80a58cd6427f6f59629abf591141b2af036bb345
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49278173"
---
# <a name="how-to-instrument-a-native-stand-alone-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Gewusst wie: Instrumentieren einer systemeigenen, eigenständigen Komponente und Sammeln von Zeitsteuerungsdaten über die Befehlszeile mit dem Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie eine systemeigene Komponente (beispielsweise eine EXE- oder DLL-Datei in C++) mit den Befehlszeilentools der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools instrumentiert wird und wie ausführliche Zeitsteuerungsdaten gesammelt werden.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-Installationsverzeichnisses. Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Um ausführliche Zeitsteuerungsdaten aus einer Komponente mithilfe der Instrumentierungsmethode zu sammeln, generieren Sie mit dem Tool [VSInstr.exe](../profiling/vsinstr.md) eine instrumentierte Version der Komponente. Starten Sie dann den Profiler. Wenn die instrumentierte Komponente ausgeführt wird, werden Zeitsteuerungsdaten automatisch in einer Datendatei erfasst. Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Zielanwendung, und schließen Sie danach den Profiler.  
  
## <a name="starting-the-profiling-session"></a>Starten der Profilerstellungssitzung  
  
#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>So starten Sie die Profilerstellung mit der Instrumentationsmethode  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Generieren Sie mit dem Tool **VSInstr** eine instrumentierte Version der Zielanwendung.  
  
3.  Starten Sie den Profiler. Typ:  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   Mit der Option [/start](../profiling/start.md)**:trace** wird der Profiler initialisiert.  
  
    -   Die Option [/output](../profiling/output.md)**:**`OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  
  
     Sie können mindestens eine der folgenden Optionen zusammen mit der Option **/start:trace** verwenden.  
  
    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist. Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist. Der Prozessbesitzer ist auf der Registerkarte „Prozesse“ in der Spalte „Benutzername“ des Windows Task-Managers aufgeführt.|  
    |[/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen. Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird. Die Sitzungs-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs-ID des Windows Task-Managers aufgeführt. **/CS** kann als Abkürzung für **/crosssession** angegeben werden.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Startet den Profiler mit angehaltener Datensammlung. Mit[/globalon](../profiling/globalon-and-globaloff.md) setzen Sie die Profilerstellung fort.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Sammelt Informationen aus dem in `Config` angegebenen Prozessorleistungsindikator. Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500 ms.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.|  
  
4.  Starten Sie die Zielanwendung auf die gewohnte Weise.  
  
## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit Optionen **VSPerfCmd.exe** starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  
  
-   Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet (**/globalon**) oder beendet (**/globaloff**).|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet (**/processon**) oder beendet (**/processoff**).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Die Datensammlung wird für den mit der Prozess-ID (`TID`) angegebenen Prozess gestartet (**/threadon**) oder beendet (**/threadoff**).|  
  
## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, schließen Sie die Anwendung, die die instrumentierte Komponente ausführt, und rufen Sie dann die Option **VSPerfCmd** [/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen.  
  
#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  
  
1.  Schließen Sie die Zielanwendung.  
  
2.  Schließen Sie den Profiler. Typ:  
  
     **VSPerfCmd /shutdown**  
  
## <a name="see-also"></a>Siehe auch  
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Datenansichten der Instrumentierungsmethode](../profiling/instrumentation-method-data-views.md)



