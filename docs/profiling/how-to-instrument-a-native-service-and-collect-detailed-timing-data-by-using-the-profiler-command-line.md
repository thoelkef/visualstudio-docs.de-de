---
title: "Gewusst wie: Instrumentieren eines systemeigenen Diensts und Sammeln ausf&#252;hrlicher Zeitsteuerungsdaten &#252;ber die Profiler-Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: dfe58b39-63f8-4a87-ab3a-2b5b14faa8d0
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Instrumentieren eines systemeigenen Diensts und Sammeln ausf&#252;hrlicher Zeitsteuerungsdaten &#252;ber die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools einen systemeigenen Dienst \(C\/C\+\+\) instrumentieren und ausführliche Zeitsteuerungsdaten sammeln können.  
  
> [!NOTE]
>  Mit der Instrumentationsmethode kann kein Profil für einen Dienst erstellt werden, wenn der Dienst nach dem Start des Computers nicht neu gestartet werden kann, z. B. ein Dienst, der nur gleichzeitig mit dem Betriebssystem gestartet wird.  
>   
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Um die Profiler\-Befehlszeilentools zu verwenden, müssen Sie den Toolpfad der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Um ausführliche Zeitsteuerungsdaten mit der Instrumentationsmethode aus einem systemeigenen Dienst zu erfassen, generieren Sie mit dem Tool [VSInstr.exe](../profiling/vsinstr.md) eine instrumentierte Version der Komponente.  Sie ersetzen dann die nicht instrumentierte Version des Diensts durch die instrumentierte Version und stellen dabei sicher, dass der Dienst für den manuellen Start konfiguriert ist.  Starten Sie dann den Profiler.  
  
 Wenn der Dienst gestartet wird, werden die Zeitsteuerungsdaten automatisch in einer Datendatei erfasst.  Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, deaktivieren Sie den Dienst und fahren danach den Profiler selbst herunter.  
  
## Starten der Anwendung mit dem Profiler  
  
#### So starten Sie die Profilerstellung für einen systemeigenen Dienst  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Generieren Sie mit dem **VSInstr**\-Tool eine instrumentierte Version der Binärdatei des Diensts.  
  
3.  Ersetzen Sie die ursprüngliche Binärdatei durch die instrumentierte Version.  Stellen Sie im Windows Dienststeuerungs\-Manager sicher, dass der Starttyp auf Manuell eingestellt ist.  
  
4.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd** [\/start](../profiling/start.md)**:trace** [\/output](../profiling/output.md)**:**`OutputFile` \[`Options`\]  
  
    -   Mit der **\/start:trace**\-Option wird der Profiler initialisiert.  
  
    -   Die **\/output:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:trace**\-Option verwenden.  
  
    > [!NOTE]
    >  Die **\/user**\-Option und die **\/crosssession**\-Option sind normalerweise für ASP.NET\-Anwendungen erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET\-Arbeitsprozesses ist.  Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.  Diese Option ist erforderlich, wenn die ASP.NET\-Anwendung in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte "Prozesse" in der Spalte "Sitzungs\-ID" des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|Gibt die Anzahl der Sekunden an, die auf die Initialisierung des Profilers gewartet werden soll, bevor ein Fehler zurückgegeben wird.  Wenn `Interval` nicht angegeben wird, wartet der Profiler unendlich lange.  Standardmäßig wird **\/start** sofort beendet.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Um den Profiler mit angehaltener Datensammlung zu starten, fügen Sie der **\/start**\-Befehlszeile die **\/globaloff**\-Option hinzu.  Mit **\/globalon** setzen Sie die Profilerstellung fort.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Sammelt Informationen aus dem in Config angegebenen Prozessorleistungsindikator.  Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
5.  Startet den Dienst aus dem Dienststeuerungs\-Manager.  
  
## Steuern der Datenauflistung  
 Wenn der Dienst ausgeführt wird, können Sie die **VSPerfCmd.exe**\-Optionen verwenden, um das Schreiben der Daten in die Profilerdatendatei zu starten und zu beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen des Diensts.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Paare von **VSPerfCmd**\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [\/threadoff](../profiling/threadon-and-threadoff.md)**:**`TID`|Startet \(**\/threadon**\) oder beendet \(**\/threadoff**\) die Datensammlung für den mit der Thread\-ID \(`TID`\) angegebenen Thread.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, beenden Sie den Dienst, der die instrumentierte Komponente ausführt, und rufen Sie dann die **VSPerfCmd**[\/shutdown](../profiling/shutdown.md)\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Beenden Sie den Dienst aus dem Dienststeuerungs\-Manager.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/shutdown**  
  
3.  Ersetzen Sie das instrumentierte Modul durch das Original.  Konfigurieren Sie bei Bedarf den Starttyp des Diensts neu.  
  
## Siehe auch  
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)   
 [Instrumentationsmethoden\-Datenansichten](../profiling/instrumentation-method-data-views.md)