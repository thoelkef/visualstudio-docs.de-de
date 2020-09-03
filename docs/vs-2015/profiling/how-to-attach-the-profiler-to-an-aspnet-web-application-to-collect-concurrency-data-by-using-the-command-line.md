---
title: 'Vorgehensweise: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln paralleler Daten über die Befehlszeile | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d720779019ab4106fa6c4b727e9994f168a2d8f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179281"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-concurrency-data-by-using-the-command-line"></a>Gewusst wie: Anfügen des Profilers an eine ASP.NET-Webanwendung zum Sammeln paralleler Daten über die Befehlszeile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie der Profiler mit den Befehlszeilentools der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Profilerstellungstools an eine ASP.NET-Anwendung angefügt wird und Parallelitätsdaten für Prozesse und Threads erfasst werden können.  

 Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\Team Tools\Performance Tools" des Visual Studio-Installationsverzeichnisses. Auf 64-Bit-Computern sind sowohl 64 Bit- als auch 32-Bit-Versionen der Tools verfügbar. Damit Sie den Profiler an einer Eingabeaufforderung verwenden können, müssen Sie der PATH-Umgebungsvariablen in der **Eingabeaufforderung** oder dem Befehl selbst den Pfad des Tools hinzufügen. Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Fügen Sie zum Sammeln von Nebenläufigkeitsdaten den Profiler an den ASP.NET-Arbeitsprozess an, der die Website hostet. Während der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen. Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden. Es empfiehlt sich in den meisten Fällen, am Ende einer Sitzung die Umgebungsvariablen für die Profilerstellung zu löschen.  

## <a name="attaching-the-profiler"></a>Anfügen des Profilers  

#### <a name="to-attach-the-profiler-to-a-aspnet-application"></a>So fügen Sie den Profiler an eine ASP.NET-Anwendung an  

1. Starten Sie den Profiler, indem Sie den folgenden Befehl eingeben:  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: Parallelität/Output:** `OutputFile` [ `Options` ]  

   - Mit der Option [/start](../profiling/start.md) wird der Profiler initialisiert, um Ressourcenkonfliktdaten zu sammeln.  

   - Die Option [/output](../profiling/output.md) **:** `OutputFile` ist zusammen mit **/start** erforderlich. Mit dem `OutputFile`-Objekt werden Name und Speicherort der Profilerstellungs-Datendatei (VSP-Datei) angegeben.  

     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der Option **/start** verwenden.  

   |                               Option                               |                                                                     Beschreibung                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/user](../profiling/user-vsperfcmd.md) **:** [`Domain\`]`UserName` |                           Gibt den optionalen Domänen- und Benutzernamen des Kontos an, dem Zugriff auf den Profiler gewährt werden soll.                           |
   |           [/crosssession](../profiling/crosssession.md)            |                                               Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.                                                |
   |  [/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`  |                                      Gibt einen Windows-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.                                       |
   |       [/automark](../profiling/automark.md) **:** `Interval`       | Verwenden Sie nur **/wincounter**. Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows-Leistungsindikatoren an. Der Standardwert ist 500. |
   |     [/events](../profiling/events-vsperfcmd.md) **:** `Config`     |       Gibt ein ETW-Ereignis (Ereignisablaufverfolgung für Windows) an, dessen Daten während der Profilerstellung gesammelt werden sollen. ETW-Ereignisse werden in einer separaten Datei (.etl) gesammelt.       |

2. Starten Sie die ASP.NET-Anwendung wie gewohnt.  

3. Fügen Sie den Profiler an den ASP.NET-Arbeitsprozess an, indem Sie den folgenden Befehl eingeben:**VSPerfCmd/Attach:** `PID` [**/targetclr:** `Version` ]  

   - `PID` gibt die ID oder den Namen des ASP.NET-Arbeitsprozesses an. Die Prozess-IDs aller aktiven Prozesse werden im Windows Task-Manager angezeigt.  

   - [/targetclr](../profiling/targetclr.md) **:** `Version` gibt die Version des Common Language Runtime (CLR) für die Profilerstellung an, wenn mehr als eine Laufzeitversion in eine Anwendung geladen wird. Dieser Parameter ist optional.  

## <a name="controlling-data-collection"></a>Steuern der Datenauflistung  
 Während die Anwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit VSPerfCmd.exe-Optionen starten und beenden. Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  

#### <a name="to-start-and-stop-data-collection"></a>So starten und beenden Sie die Datensammlung  

- Mit den VSPerfCmd-Optionspaaren in der folgenden Tabelle wird die Datensammlung gestartet und beendet. Geben Sie jede Option in einer eigenen Befehlszeile an. Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  

    |Option|Beschreibung|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Die Datensammlung wird für alle Prozesse gestartet ( **/globalon**) oder beendet ( **/globaloff**).|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [PROCESSOFF](../profiling/processon-and-processoff.md) **:**  `PID`|Die Datensammlung wird für den mit der Prozess-ID (`PID`) angegebenen Prozess gestartet ( **/processon**) oder beendet ( **/processoff**).|  
    |[/attach](../profiling/attach.md) **:** {`PID`&#124;`ProcName`} [/detach](../profiling/detach.md)[ **:** {`PID`&#124;`ProcName`}]|Mit **/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess-ID (`PID`) oder des Prozessnamens (*ProcName*) angegeben ist. Mit **/detach** wird die Datensammlung für den angegebenen Prozess (oder für alle Prozesse, wenn kein Prozess angegeben ist) beendet.|  

## <a name="ending-the-profiling-session"></a>Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen. Sie können das Sammeln von Daten einer Anwendung, für die mit der Parallelitätsmethode ein Profil erstellt wird, beenden, indem Sie den ASP.NET-Arbeitsprozess neu starten oder die **VSPerfCmd /detach**-Option aufrufen. Rufen Sie anschließend die Option **VSPerfCmd /shutdown** auf, um den Profiler zu deaktivieren und die Profilerstellungs-Datendatei zu schließen. Der **VSPerfClrEnv /globaloff**-Befehl löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.  

#### <a name="to-end-a-profiling-session"></a>So beenden Sie eine Profilerstellungssitzung  

1. Trennen Sie den Profiler von der Zielanwendung, indem Sie die Anwendung schließen oder an einer Eingabeaufforderung Folgendes eingeben:  

     **VSPerfCmd /detach**  

2. Beenden Sie den Profiler, indem Sie den folgenden Befehl an der Eingabeaufforderung eingeben:  

     **VSPerfCmd**  [/shutdown](../profiling/shutdown.md)  

## <a name="see-also"></a>Weitere Informationen  
 [Profilerstellung ASP.NET Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Schnelle Website-Profilerstellung mit vsperfaspnetcmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
