---
title: "Gewusst wie: Anf&#252;gen des Profilers an eine ASP.NET-Webanwendung zum Sammeln paralleler Daten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e215fdd-55f8-43ef-9534-06542eefe223
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an eine ASP.NET-Webanwendung zum Sammeln paralleler Daten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie der Profiler mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools an eine ASP.NET\-Anwendung angefügt wird und Parallelitätsdaten für Prozesse und Threads erfasst werden können.  
  
 Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des Visual Studio\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie den Profiler an einer Eingabeaufforderung verwenden können, müssen Sie der PATH\-Umgebungsvariablen in der **Eingabeaufforderung** oder dem Befehl selbst den Pfad des Tools hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Fügen Sie zum Sammeln von Nebenläufigkeitsdaten den Profiler an den ASP.NET\-Arbeitsprozess an, der die Website hostet.  Während der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden.  Es empfiehlt sich in den meisten Fällen, am Ende einer Sitzung die Umgebungsvariablen für die Profilerstellung zu löschen.  
  
## Anfügen des Profilers  
  
#### So fügen Sie den Profiler an eine ASP.NET\-Anwendung an  
  
1.  Starten Sie den Profiler, indem Sie den folgenden Befehl eingeben:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency \/output:**`OutputFile` \[`Options`\]  
  
    -   Mit der Option [\/start](../profiling/start.md) wird der Profiler initialisiert, um Ressourcenkonfliktdaten zu sammeln.  
  
    -   Die Option [\/output](../profiling/output.md)**:**`OutputFile` ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können alle Optionen in der folgenden Tabelle in Verbindung mit der **\/start** \-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain\`\]`UserName`|Gibt den optionalen Domänen\- und Benutzernamen des Kontos an, dem Zugriff auf den Profiler gewährt werden soll.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
2.  Starten Sie die ASP.NET\-Anwendung wie gewohnt.  
  
3.  Fügen Sie den Profiler an den ASP.NET\-Arbeitsprozess an, indem Sie den folgenden Befehl eingeben:**VSPerfCmd \/attach:**\-`PID` \[**\/targetclr:**`Version`\]  
  
    -   `PID` gibt die ID oder den Namen des ASP.NET\-Arbeitsprozesses an.  Die Prozess\-IDs aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn in einer Anwendung mehrere Laufzeitversionen geladen wurden.  Dieser Parameter ist optional.  
  
## Steuern der Datenauflistung  
 Während die Anwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit VSPerfCmd.exe\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Mit den VSPerfCmd\-Optionspaaren in der folgenden Tabelle wird die Datensammlung gestartet und beendet.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID`  [processoff](../profiling/processon-and-processoff.md) **:** `PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID \(`PID`\) oder des Prozessnamens \(*ProcName*\) angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein Prozess angegeben ist\) beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen.  Sie können das Sammeln von Daten einer Anwendung, für die mit der Parallelitätsmethode ein Profil erstellt wird, beenden, indem Sie den ASP.NET\-Arbeitsprozess neu starten oder die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Der **VSPerfClrEnv \/globaloff**\-Befehl löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Trennen Sie den Profiler von der Zielanwendung, indem Sie die Anwendung schließen oder an einer Eingabeaufforderung Folgendes eingeben:  
  
     **VSPerfCmd \/detach**  
  
2.  Beenden Sie den Profiler, indem Sie den folgenden Befehl an der Eingabeaufforderung eingeben:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Siehe auch  
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Schnelle Website\-Profilerstellung mit VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)