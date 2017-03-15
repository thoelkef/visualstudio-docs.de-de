---
title: "Gewusst wie: Anf&#252;gen des Profilers an eine ASP.NET-Webanwendung zum Sammeln von Speicherdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Anf&#252;gen des Profilers an eine ASP.NET-Webanwendung zum Sammeln von Speicherdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools den Profiler an eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung anfügen und Daten zur Anzahl und Größe der .NET Framework\-Speicherbelegungen sammeln können.  Sie können außerdem Daten zur Lebensdauer von .NET Framework\-Arbeitsspeicherobjekten erfassen.  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
 Um Leistungsdaten von einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung zu erfassen, müssen Sie das [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md)\-Tool verwenden, um die entsprechenden Umgebungsvariablen auf dem Computer zu initialisieren, der die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung hostet.  Sie müssen dann den Computer neu starten, um den Webserver für die Profilerstellung zu konfigurieren.  
  
 Verwenden Sie dann das [VSPerfCmd.exe](../profiling/vsperfcmd.md)\-Tool, um den Profiler an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess anzufügen, der die Website hostet.  Wenn der Profiler an die Anwendung angefügt ist, können Sie die Datensammlung anhalten und fortsetzen.  
  
 Um eine Profilerstellungssitzung zu beenden, darf der Profiler nicht mehr an die Anwendung angefügt sein und muss explizit beendet werden.  In den meisten Fällen empfiehlt es sich, die Umgebungsvariablen für die Profilerstellung am Ende einer Sitzung zu entfernen.  
  
## Anfügen des Profilers  
  
#### So fügen Sie den Profiler an eine ASP.NET\-Webanwendung an  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Initialisieren Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfClrEnv** {**\/globalsamplegc** &#124; **\/globalsamplegclife**} \[**\/samplelineoff**\]  
  
    -   Die **\/globalsamplegc**\-Option und die **\/globalsamplegclife**\-Option geben den Typ der Arbeitsspeicherdaten an, die gesammelt werden sollen.  
  
         Geben Sie genau eine der folgenden Optionen an:  
  
        |Option|**Beschreibung**|  
        |------------|----------------------|  
        |**\/globalsamplegc**|Aktiviert die Sammlung von Daten zur Speicherbelegung.|  
        |**\/globalsamplegclife**|Aktiviert die Sammlung von Daten zur Speicherbelegung und zur Objektlebensdauer.|  
  
    -   Die **\/samplelineoff**\-Option deaktiviert die Zuweisung gesammelter Daten zu bestimmten Quellcodezeilen.  Wenn diese Option angegeben ist, werden Daten auf Funktionsebene zugewiesen.  
  
3.  Starten Sie den Computer neu, um die neue Umgebungskonfiguration festzulegen.  
  
4.  Öffnen Sie ein Eingabeaufforderungsfenster.  Legen Sie ggf. die Umgebungsvariable des Profilerpfads fest.  
  
5.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/start](../profiling/start.md) **:sample**  [\/output](../profiling/output.md) **:** `OutputFile` \[`Options`\]  
  
    -   Mit der **\/start:sample**\-Option wird der Profiler initialisiert.  
  
    -   Die **\/output:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:sample**\-Option verwenden.  
  
    > [!NOTE]
    >  Die **\/user**\-Option und die **\/crosssession**\-Option sind normalerweise für ASP.NET\-Anwendungen erforderlich.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/user](../profiling/user-vsperfcmd.md) **:**\[`Domain`**\\**\]`UserName`|Gibt die Domäne und den Benutzernamen des Kontos an, das Besitzer des ASP.NET\-Arbeitsprozesses ist.  Diese Option ist erforderlich, wenn der Prozess als ein Benutzer ausgeführt wird, der nicht der angemeldete Benutzer ist.  Der Prozessbesitzer ist auf der Registerkarte "Prozesse" in der Spalte "Benutzername" des Windows Task\-Managers aufgeführt.|  
    |[\/crosssession](../profiling/crosssession.md)|Aktiviert die Profilerstellung für Prozesse in anderen Anmeldesitzungen.  Diese Option ist erforderlich, wenn die ASP.NET\-Anwendung in einer anderen Sitzung ausgeführt wird.  Die Sitzungs\-ID ist auf der Registerkarte Prozesse in der Spalte Sitzungs\-ID des Windows Task\-Managers aufgeführt.  **\/CS** kann als Abkürzung für **\/crosssession** angegeben werden.|  
    |[\/waitstart](../profiling/waitstart.md) \[**:**`Interval`\]|Gibt die Anzahl der Sekunden an, die auf die Initialisierung des Profilers gewartet werden soll, bevor ein Fehler zurückgegeben wird.  Wenn `Interval` nicht angegeben wird, wartet der Profiler unendlich lange.  Standardmäßig wird **\/start** sofort beendet.|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
  
6.  Starten Sie die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung auf die gewohnte Weise.  
  
7.  Fügen Sie den Profiler an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess an.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/attach](../profiling/attach.md) **:**{`PID`&#124;`ProcName`} \[[\/targetclr](../profiling/targetclr.md)**:**`Version`\]  
  
    -   Die Prozess\-ID `(PID)` gibt die Prozess\-ID oder den Prozessnamen des [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozesses an.  Die Prozess\-IDs aller aktiven Prozesse werden im Windows Task\-Manager angezeigt.  
  
    -   **\/targetclr:** `Version` gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn mehr als eine Laufzeitversion in eine Anwendung geladen wird.  
  
## Steuern der Datenauflistung  
 Während die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Profiler\-Datendatei mit **VSPerfCmd.exe**\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Die folgenden Paare von **VSPerfCmd**\-Optionen starten und beenden die Datensammlung.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [\/processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den über die `PID` angegebenen Prozess.|  
    |**\/attach:**{`PID`&#124;`ProcName`} [\/detach](../profiling/detach.md)\[**:**{`PID`&#124;:`ProcName`}\]|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der anhand der Prozess\-ID oder des Prozessnamens angegeben ist.  Mit **\/detach** wird die Datensammlung für den angegebenen Prozess \(oder für alle Prozesse, wenn kein bestimmter Prozess angegeben ist\) beendet.|  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von der Webanwendung getrennt werden.  Sie können das Sammeln von Daten für eine Anwendung anhalten, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess erneut starten oder die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die Option **VSPerfCmd** [\/shutdown](../profiling/shutdown.md) auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Der **VSPerfClrEnv \/globaloff**\-Befehl löscht die Umgebungsvariablen für die Profilerstellung, die Systemkonfiguration wird jedoch erst zurückgesetzt, wenn der Computer neu gestartet wird.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Geben Sie **VSPerfCmd** [\/detach](../profiling/detach.md) ein  
  
         \- oder \-  
  
    -   Schließen Sie den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess.  Geben Sie Folgendes ein:  
  
     **IISReset \/stop**  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/shutdown**  
  
3.  \(Optional\) Löschen Sie die Umgebungsvariablen für die Profilerstellung.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/globaloff**  
  
4.  Starten Sie den Computer neu.  Starten Sie bei Bedarf Internetinformationsdienste \(Internet Information Services, IIS\) erneut.  Geben Sie Folgendes ein:  
  
     **IISReset \/start**  
  
## Siehe auch  
 [Profilerstellung für ASP.NET\-Webanwendungen](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [.NET\-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)