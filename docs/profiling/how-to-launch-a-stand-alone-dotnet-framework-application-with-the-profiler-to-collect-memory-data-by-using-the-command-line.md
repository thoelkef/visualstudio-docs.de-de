---
title: "Gewusst wie: Starten einer eigenst&#228;ndigen .NET Framework-Anwendung mit dem Profiler zum Sammeln von Speicherdaten &#252;ber die Befehlszeile | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3bc53041-91b7-4ad0-8413-f8bf2c4b3f5e
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Starten einer eigenst&#228;ndigen .NET Framework-Anwendung mit dem Profiler zum Sammeln von Speicherdaten &#252;ber die Befehlszeile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie mit den Befehlszeilentools der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools eine eigenständige .NET Framework \(Client\-\)Anwendung gestartet wird und Arbeitsspeicherdaten gesammelt werden.  
  
 Eine Profilerstellungssitzung besteht aus drei Teilen:  
  
-   Starten der Anwendung mit dem Profiler  
  
-   Sammeln von Profilerstellungsdaten  
  
-   Beenden der Profilerstellungssitzung  
  
> [!NOTE]
>  Die Befehlszeilentools der Profilerstellungstools befinden sich im Unterverzeichnis "\\Team Tools\\Performance Tools" des [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Installationsverzeichnisses.  Auf 64\-Bit\-Computern sind 64\-Bit\- und 32\-Bit\-Versionen der Tools verfügbar.  Damit Sie die Profilerbefehlszeilentools verwenden können, müssen Sie den Pfad des Tools der PATH\-Umgebungsvariable des Eingabeaufforderungsfensters oder dem Befehl selbst hinzufügen.  Weitere Informationen finden Sie unter [Angeben des Pfads zu Tools für die Befehlszeile](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
  
## Starten der Anwendung mit dem Profiler  
 Wenn Sie die Zielanwendung mit dem Profiler starten möchten, verwenden Sie die **VSPerfCmd.exe**\-Optionen **\/start** und **\/launch**, um den Profiler zu initialisieren und die Anwendung zu starten.  Sie können **\/start** und **\/launch** sowie die zugehörigen Optionen in einer Befehlszeile angeben.  
  
 Außerdem können Sie die **\/globaloff**\-Optionen hinzufügen, um die Datensammlung beim Starten der Zielanwendung anzuhalten.  Dann starten Sie die Datensammlung mit **\/globalon**.  
  
#### So starten Sie eine Anwendung mit dem Profiler  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Starten Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd \/start:sample \/output:** `OutputFile` \[`Options`\]  
  
    -   Mit der [\/start](../profiling/start.md)**:sample**\-Option wird der Profiler initialisiert.  
  
    -   Die [\/output](../profiling/output.md)**:**`OutputFile`\-Option ist bei **\/start** erforderlich.  Das `OutputFile`\-Objekt gibt den Namen und Speicherort der Profilerstellungs\-Datendatei \(.vsp\) an.  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/start:sample**\-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Gibt einen Windows\-Leistungsindikator an, dessen Daten während der Profilerstellung gesammelt werden sollen.|  
    |[\/automark](../profiling/automark.md) **:** `Interval`|Diese Option kann nur in Kombination mit **\/wincounter** verwendet werden.  Gibt die Anzahl von Millisekunden zwischen Ereignissen bei der Datensammlung mit Windows\-Leistungsindikatoren an.  Der Standardwert ist 500 ms.|  
  
3.  Starten Sie die Zielanwendung.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/launch](../profiling/launch.md) **:** `appName` **\/gc:**{**allocation**&#124;**lifetime**}\[`Options`\]  
  
    -   Die [\/gc](../profiling/gc-vsperfcmd.md)**:**`Keyword`\-Option ist erforderlich, um Arbeitsspeicherdaten für .NET Framework zu erfassen.  Der Schlüsselwortparameter gibt an, ob nur Daten zur Speicherbelegung oder Daten zur Speicherbelegung und zur Objektlebensdauer gesammelt werden sollen.  
  
        |Schlüsselwort|**Beschreibung**|  
        |-------------------|----------------------|  
        |**allocation**|Es werden nur Daten zur Speicherbelegung gesammelt.|  
        |**lifetime**|Es werden Daten zur Speicherbelegung und zur Objektlebensdauer gesammelt.|  
  
     Sie können jede der folgenden Optionen zusammen mit der **\/launch**\-Option verwenden.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/args](../profiling/args.md) **:** `Arguments`|Gibt eine Zeichenfolge mit den Befehlszeilenargumenten an, die an die Zielanwendung übergeben werden sollen.|  
    |[\/console](../profiling/console.md)|Startet die Ziel\-Befehlszeilenanwendung in einem separaten Fenster.|  
    |[\/events](../profiling/events-vsperfcmd.md) **:** `Config`|Gibt ein ETW\-Ereignis \(Ereignisablaufverfolgung für Windows\) an, dessen Daten während der Profilerstellung gesammelt werden sollen.  ETW\-Ereignisse werden in einer separaten Datei \(.etl\) gesammelt.|  
    |[\/targetclr](../profiling/targetclr.md) **:** `Version`|Gibt die Version der CLR \(Common Language Runtime\) für die Profilerstellung an, wenn mehr als eine Laufzeitversion in eine Anwendung geladen wird.|  
  
## Steuern der Datenauflistung  
 Wenn die Zielanwendung ausgeführt wird, können Sie die Datensammlung steuern, indem Sie das Schreiben von Daten in die Datei mit **VSPerfCmd.exe**\-Optionen starten und beenden.  Durch das Steuern der Datensammlung können Sie Daten zu einem bestimmten Teil der Programmausführung sammeln, z. B. zum Starten oder Schließen der Anwendung.  
  
#### So starten und beenden Sie die Datensammlung  
  
-   Mit den folgenden Optionspaaren wird die Datensammlung gestartet und beendet.  Geben Sie jede Option in einer eigenen Befehlszeile an.  Sie können die Datensammlung mehrmals aktivieren und deaktivieren.  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |[\/globalon \/globaloff](../profiling/globalon-and-globaloff.md)|Startet \(**\/globalon**\) oder beendet \(**\/globaloff**\) die Datensammlung für alle Prozesse.|  
    |[\/processon](../profiling/processon-and-processoff.md) **:** `PID` [processoff](../profiling/processon-and-processoff.md)**:**`PID`|Startet \(**\/processon**\) oder beendet \(**\/processoff**\) die Datensammlung für den über die Prozess\-ID \(`PID`\) angegebenen Prozess.|  
    |[\/attach](../profiling/attach.md) **:** `PID` [\/detach](../profiling/detach.md)|Mit **\/attach** wird die Datensammlung für den Prozess gestartet, der mit `PID` \(Prozess\-ID\) angegeben wurde.  Mit **\/detach** wird die Datensammlung für alle Prozesse beendet.|  
  
-   Sie können auch die [\/mark](../profiling/mark.md)\-Option von **VSPerfCmd.exe** verwenden, um eine Profilmarkierung in die Datendatei einzufügen.  Der **\/mark**\-Befehl fügt einen Bezeichner, einen Zeitstempel und eine optionale benutzerdefinierte Textzeichenfolge hinzu.  Markierungen können zum Filtern von Daten verwendet werden.  
  
## Beenden der Profilerstellungssitzung  
 Um eine Profilerstellungssitzung zu beenden, muss der Profiler von allen profilierten Prozessen getrennt und explizit beendet werden.  Den Profiler können Sie von einer Anwendung trennen, für die ein Profil mit der Samplingmethode erstellt wurde, indem Sie die Anwendung schließen oder die **VSPerfCmd \/detach**\-Option aufrufen.  Rufen Sie dann die **VSPerfCmd \/shutdown**\-Option auf, um den Profiler zu deaktivieren und die Profilerstellungs\-Datendatei zu schließen.  Mit dem **VSPerfClrEnv \/off**\-Befehl werden die Umgebungsvariablen für die Profilerstellung gelöscht.  
  
#### So beenden Sie eine Profilerstellungssitzung  
  
1.  Führen Sie einen der folgenden Schritte aus, um den Profiler von der Zielanwendung zu trennen:  
  
    -   Schließen Sie die Zielanwendung.  
  
         \- oder \-  
  
    -   Geben Sie **VSPerfCmd \/detach** ein.  
  
2.  Schließen Sie den Profiler.  Geben Sie Folgendes ein:  
  
     **VSPerfCmd**  [\/shutdown](../profiling/shutdown.md)  
  
## Siehe auch  
 [Profilerstellung für eigenständige Anwendungen](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [.NET\-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)