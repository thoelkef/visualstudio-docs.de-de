---
title: "Gewusst wie: Anf&#252;gen des Profilers an eine eigenst&#228;ndige .NET Framework-Anwendung zum Sammeln von Parallelit&#228;tsdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fdd41576-797e-4312-8520-fee7bb767e4a
caps.latest.revision: 29
caps.handback.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an eine eigenst&#228;ndige .NET Framework-Anwendung zum Sammeln von Parallelit&#228;tsdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie der Profiler mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools an eine ausgeführte eigenständige .NET Framework\-\(Client\-\)Anwendung angefügt wird und wie Parallelitätsdaten zu Prozessen und Threads gesammelt werden.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Während der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden.  
  
## Anfügen des Profilers  
  
#### So fügen Sie den Profiler an eine aktive .NET Framework\-Anwendung an  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile`\[`Options`\]  
  
     Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:concurrency** \-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
3.  Starten Sie die Zielanwendung auf die gewohnte Weise.  
  
4.  Fügen Sie den Profiler an die Zielanwendung an.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/attach:** `PID` \[**\/lineoff**\] \[**\/targetclr:**`Version`\]  
  
    -   `PID` gibt die Prozess\-ID der Zielanwendung an.  Die Prozess\-IDs aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
    -   [\/Lineoff](../profiling/lineoff.md) deaktiviert die Auflistung der Zeilennummerndaten.  
  
    -   [\/targetclr](../profiling/targetclr.md) **:** `Version` gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn in einer Anwendung mehrere Laufzeitversionen geladen wurden.  Optional.  
  
## Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit VSPerfCmd.exe\-Optionen starten und beenden.  Durch die Steuerung der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Mit den folgenden VSPerfCmd.exe\-Optionspaaren wird die Datensammlung gestartet und beendet.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID \(`PID`\) oder des Prozessnamens \("ProcName"\) angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist\) beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen.  Sie können das Sammeln von Daten einer Anwendung, für die mithilfe der Parallelitätsmethode ein Profil erstellt wird, beenden. Schließen Sie dazu die Anwendung, oder rufen Sie die **VSPerfCmd \/detach**\-Option auf.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Mit dem **VSPerfClrEnv \/off**\-Befehl werden die Umgebungsvariablen für die Profilerstellung gelöscht.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Geben Sie **VSPerfCmd \/detach** ein.  
  
         \- oder \-  
  
    -   Schließen Sie die Zielanwendung.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     VSPerfCmd[\/shutdown](../profiling/shutdown.md)