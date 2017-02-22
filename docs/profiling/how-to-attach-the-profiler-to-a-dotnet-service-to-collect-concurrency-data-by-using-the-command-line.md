---
title: "Gewusst wie: Anf&#252;gen des Profilers an einen .NET-Dienst zum Sammeln von Parallelit&#228;tsdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ffbdfe37-8325-44be-bd36-2c8aab2dec7b
caps.latest.revision: 24
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an einen .NET-Dienst zum Sammeln von Parallelit&#228;tsdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie der Profiler mithilfe der Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools an einen [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Dienst angefügt wird und wie Parallelitätsdaten zu Prozessen und Threads mit der Samplingmethode erfasst werden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des Visual Studio\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Um Nebenläufigkeitsdaten zu sammeln, müssen Sie den Profiler an den Dienstprozess anfügen.  Während der Profiler an den Dienst angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an den Dienst angefügt sein und muss explizit beendet werden.  In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## Anfügen des Profilers  
  
#### So fügen Sie den Profiler an einen .NET Framework\-Dienst an  
  
1.  Installieren Sie den Dienst.  
  
2.  Öffnen Sie ein Befehlsfenster.  
  
3.  Initialisieren Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     [VSPerfClrEnv](../profiling/vsperfclrenv.md) **\/globalsampleon** \[**\/samplelineoff**\]  
  
    -   **\/globalsampleon** aktiviert das Sampling.  
  
    -   **\/samplelineoff** deaktiviert die Zuweisung gesammelter Daten zu bestimmten Quellcodezeilen.  Wenn diese Option angegeben wird, werden Daten nur Funktionen zugewiesen.  
  
4.  Starten Sie den Computer neu.  
  
5.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     [VSPerfCmd](../profiling/vsperfcmd.md) **\/start:concurrency  \/output:**`OutputFile` \[`Options`\]  
  
     Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start**\-Option verwenden.  
  
    > [!NOTE]
    >  Die **\/user**\-Option und die **\/crosssession**\-Option sind normalerweise für Dienste erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des profilierten Prozesses ist.  Diese Option ist nur erforderlich, wenn der Prozess als Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Sitzungen.  Diese Option ist erforderlich, wenn der Dienst in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte "Prozesse" in der Spalte "Sitzungs\-ID" des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
6.  Starten Sie den Dienst bei Bedarf.  
  
7.  Fügen Sie den Profiler an den Dienst an.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/attach:** `PID` \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   `PID` gibt die ID oder den Namen des Dienstprozesses an.  Die Prozess\-IDs aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
    -   **targetclr:** `Version` gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn mehr als eine Laufzeitversion in eine Anwendung geladen wird.  Optional.  
  
## Steuern der Datenauflistung  
 Während der Dienst ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit VSPerfCmd.exe\-Optionen starten und beenden.  Durch die Steuerung der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Paare von **VSPerfCmd**\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den mit der Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[:{`PID`&#124;`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID oder des Prozessnamens angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist\) beendet.|  
  
-   Sie können auch die [\/mark](../profiling/mark.md)\-Option von **VSPerfCmd.exe** verwenden, um eine Profilmarkierung in die Datendatei einzufügen.  Der **\/mark**\-Befehl fügt einen Bezeichner, einen Zeitstempel und eine optionale benutzerdefinierte Textzeichenfolge hinzu.  Mit Markierungen können die Daten in Profilerberichten und Datenansichten gefiltert werden.  Die folgenden Paare von VSPerfCmd\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung beenden zu können, darf der Profiler keine Daten erfassen.  Sie können das Sammeln von Daten einer Anwendung, für die mithilfe der Parallelitätsmethode ein Profil erstellt wird, beenden. Beenden Sie hierzu den Dienst, oder rufen Sie die **VSPerfCmd \/detach**\-Option auf.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Der **VSPerfClrEnv \/globaloff**\-Befehl löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Beenden Sie den Dienst.  
  
         \- oder \-  
  
    -   Geben Sie **VSPerfCmd \/detach.** ein.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [Shutdown](../profiling/shutdown.md)