---
title: "Gewusst wie: Instrumentieren eines .NET-Diensts und Sammeln ausf&#252;hrlicher Zeitsteuerungsdaten &#252;ber die Profiler-Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Instrumentieren eines .NET-Diensts und Sammeln ausf&#252;hrlicher Zeitsteuerungsdaten &#252;ber die Profiler-Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mit den Befehlszeilentools der [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)]\-Profilerstellungstools einen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Dienst instrumentieren und ausführliche Zeitsteuerungsdaten sammeln können.  
  
> [!NOTE]
>  Mit der Instrumentationsmethode kann kein Profil für einen Dienst erstellt werden, wenn der Dienst nach dem Start des Computers nicht neu gestartet werden kann, z. B. ein Dienst, der nur gleichzeitig mit dem Betriebssystem gestartet wird.  
>   
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Um die Profiler\-Befehlszeilentools zu verwenden, müssen Sie den Toolpfad der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Das Hinzufügen von Ebeneninteraktionsdaten zu einer Profilerstellung erfordert bestimmte Verfahren der Befehlszeilenprofilerstellungstools.  Siehe [Erfassen von Ebeneninteraktionsdaten](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Um ausführliche Zeitsteuerungsdaten mit der Instrumentationsmethode aus einem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Dienst zu erfassen, generieren Sie mit dem Tool [VSInstr.exe](../profiling/vsinstr.md) eine instrumentierte Version der Komponente.  Sie ersetzen dann die nicht instrumentierte Version des Diensts durch die instrumentierte Version und stellen dabei sicher, dass der Dienst für den manuellen Start konfiguriert ist.  Verwenden Sie das [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)\-Tool, um die globalen Umgebungsvariablen für die Profilerstellung zu initialisieren und dann den Hostcomputer neu zu starten.  Starten Sie dann den Profiler.  
  
 Wenn der Dienst gestartet wird, werden die Zeitsteuerungsdaten automatisch in einer Datendatei erfasst.  Sie können die Datensammlung während der Profilerstellungssitzung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, deaktivieren Sie den Dienst und fahren danach den Profiler selbst herunter.  In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## Starten der Anwendung mit dem Profiler  
  
#### So starten Sie die Profilerstellung für einen .NET Framework\-Dienst  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Generieren Sie mit dem **VSInstr**\-Tool eine instrumentierte Version der Binärdatei des Diensts.  
  
3.  Ersetzen Sie die ursprüngliche Binärdatei durch die instrumentierte Version.  Stellen Sie im Windows Dienststeuerungs\-Manager sicher, dass der Starttyp auf Manuell eingestellt ist.  
  
4.  Initialisieren Sie die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv \/globaltraceon**  
  
5.  Starten Sie den Computer neu.  
  
6.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
7.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/start:trace \/output:** `OutputFile` \[`Options`\]  
  
    -   Mit der [\/start](../profiling/start.md)**:trace**\-Option wird der Profiler initialisiert.  
  
    -   Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:trace**\-Option verwenden.  
  
    > [!NOTE]
    >  Die **\/user**\-Option und die **\/crosssession**\-Option sind normalerweise für Profilerstellungsdienste erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist.  Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen.  Diese Option ist erforderlich, wenn die Anwendung in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte "Prozesse" in der Spalte "Sitzungs\-ID" des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/waitstart](../profiling/waitstart.md)\[**:**`Interval`\]|Gibt die Anzahl der Sekunden an, die auf die Initialisierung des Profilers gewartet werden soll, bevor ein Fehler zurückgegeben wird.  Wenn `Interval` nicht angegeben wird, wartet der Profiler unendlich lange.  Standardmäßig wird **\/start** sofort beendet.|  
    |[\/globaloff](../profiling/globalon-and-globaloff.md)|Um den Profiler mit angehaltener Datensammlung zu starten, fügen Sie der **\/start**\-Befehlszeile die **\/globaloff**\-Option hinzu.  Mit **\/globalon** setzen Sie die Profilerstellung fort.|  
    |[\/counter](../profiling/counter.md) **:** `Config`|Sammelt Informationen aus dem in Config angegebenen Prozessorleistungsindikator.  Informationen zu Leistungsindikatoren werden den Daten hinzugefügt, die bei jedem Profilerstellungsereignis gesammelt werden.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
8.  Starten Sie den Dienst über den Windows Dienststeuerungs\-Manager.  
  
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
 Um eine Profilerstellungssitzung zu beenden, beenden Sie den Dienst, der die instrumentierte Komponente ausführt, und rufen Sie dann die **VSPerfCmd** [\/shutdown](../profiling/shutdown.md)\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Mit dem **VSPerfClrEnv \/globaloff**\-Befehl werden die Umgebungsvariablen für die Profilerstellung entfernt.  
  
 Sie müssen den Computer neu starten, damit die neuen Umgebungseinstellungen übernommen werden.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Beenden Sie den Dienst aus dem Dienststeuerungs\-Manager.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/shutdown**  
  
3.  Wenn Sie alle Profilerstellungsaufgaben abgeschlossen haben, entfernen Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv \/globaloff**  
  
4.  Ersetzen Sie das instrumentierte Modul durch das Original.  Konfigurieren Sie bei Bedarf den Starttyp des Diensts neu.  
  
5.  Starten Sie den Computer neu.  
  
## Siehe auch  
 [Profilerstellungsdienste](../profiling/command-line-profiling-of-services.md)   
 [Instrumentationsmethoden\-Datenansichten](../profiling/instrumentation-method-data-views.md)