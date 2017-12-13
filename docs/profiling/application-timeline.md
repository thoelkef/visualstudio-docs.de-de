---
title: Analysieren des Ressourcenverbrauchs in XAML-Apps in Visual Studio | Microsoft-Dokumentation
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 32d6ac2581f71196d1f1d826d8f1024906b7cab9
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Analysieren des Ressourcenverbrauchs und der Threadaktivitäten auf Benutzeroberflächen (XAML)
Verwenden Sie den Profiler **Anwendungszeitachse** , um Leistungsprobleme in Bezug auf die Anwendungsinteraktion in XAML-Anwendungen zu suchen und zu beheben. Mit diesem Tool können Sie die Leistung von XAML-Anwendungen verbessern, indem Sie eine detaillierte Ansicht des Ressourcenverbrauchs einer Anwendung bereitstellen. Sie können analysieren, wie viel Zeit Ihre Anwendung zum Vorbereiten von Benutzeroberflächenframes (Anordnen und Rendern), zum Verarbeiten von Netzwerk- und Datenträgeranforderungen sowie in Szenarien wie Starten von Anwendungen, Laden von Seiten und Ändern von Fenstergrößen benötigt.  
  
 Die **Anwendungszeitachse** ist eines der Tools, die Sie mit dem Befehl **Debuggen/Leistungsprofiler...** starten können.  
  
 Dieses Tool ersetzt das Tool **XAML-UI-Reaktionsfähigkeit** , das zum Diagnosetoolset für Visual Studio 2013 gehört.  
  
 Sie können dieses Tool auf den folgenden Plattformen verwenden:  
  
1.  Universelle Windows-Apps (unter Windows 10)  
  
2.  Windows 8.1  
  
3.  Windows Phone 8.1 (Gemeinsame XAML-Plattform)  
  
4.  Windows Presentation Foundation (.NET 4.0 und höher)  
  
5.  Windows 7  
  
> [!NOTE]
>  Zusätzlich zu den Daten der **Anwendungszeitachse** können Sie Daten zu CPU-Auslastung und Energieverbrauch sammeln und analysieren. Sie [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
##  <a name="BKMK_Collect_Timeline_data_for_your_app"></a> Erfassen von Anwendungszeitachsen-Daten  
 Sie können Profile für die Reaktionsfähigkeit Ihrer App auf dem lokalen Computer, einem angeschlossenen Gerät, dem Visual Studio-Simulator bzw. -Emulatoren sowie auf einem Remotegerät erstellen. Sie [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md).
  
> [!TIP]
>  Führen Sie die App nach Möglichkeit direkt auf dem Gerät aus. Die Anwendungsleistung, die im Simulator oder über eine Remotedesktopverbindung überwacht wird, ist möglicherweise nicht identisch mit der tatsächlichen Leistung auf dem Gerät. Auf der anderen Seite wirkt sich das Sammeln der Daten mithilfe der Visual Studio-Remotetools sich nicht auf die Leistungsdaten aus.  
  
 Im Folgenden finden Sie die grundlegenden Schritte:  
  
1.  Öffnen Sie die XAML-App.  
  
2.  Klicken Sie auf **Debuggen/Leistungsprofiler...**. Im Fenster ".diagsession" sollte eine Liste der Profilerstellungstools angezeigt werden.  
  
3.  Wählen Sie **Anwendungszeitachse** aus, und klicken Sie unten im Fenster auf **Starten** .  
  
    > [!NOTE]
    >  Möglicherweise wird das Fenster "Benutzerkontensteuerung" angezeigt, im dem Sie zur Eingabe Ihrer Berechtigung zur Ausführung von "VsEtwCollector.exe" aufgefordert werden. Klicken Sie auf **Ja**.  
  
4.  Führen Sie das Szenario aus, mit dem Sie ein Profil für Ihre App erstellen möchten, um Leistungsdaten zu sammeln.  
  
5.  Um die Profilerstellung zu beenden, wechseln Sie zurück zum Fenster ".diagsession", und klicken Sie oben im Fenster auf **Beenden** .  
  
     Visual Studio analysiert die gesammelten Daten und zeigt die Ergebnisse an.  
  
     ![Zeitachsenprofiler-Bericht](../profiling/media/timeline_base.png "TIMELINE_Base")  
  
##  <a name="BKMK_Analyze_Timeline_profiling_data"></a> Analysieren von Zeitachsen-Profilerstellungsdaten  
 Nachdem Sie die Profilerstellungsdaten gesammelt haben, können Sie diese Schritte ausführen, um mit der Analyse zu beginnen:  
  
1.  Überprüfen Sie die Informationen in den Diagrammen **Auslastung des UI-Threads** und **Visueller Durchsatz (FPS)** , und wählen Sie dann über die Navigationsleisten der Zeitachse den Zeitraum aus, den Sie analysieren möchten.  
  
2.  Überprüfen Sie anhand der Informationen in den Diagrammen **Auslastung des UI-Threads** bzw. **Visueller Durchsatz (FPS)** die Details in der Ansicht **Zeitachse** , um mögliche Ursachen für eine mangelhafte Reaktionsfähigkeit zu ermitteln.  
  
###  <a name="BKMK_Report_scenarios_categories_and_events"></a> Berichtsszenarien, Kategorien und Ereignisse  
 Das Tool **Anwendungszeitachse** zeigt zeitbezogene Daten zu Szenarien, Kategorien und Ereignissen im Zusammenhang mit der XAML-Leistung.  
  
###  <a name="BKMK_Diagnostic_session_timeline"></a> Zeitachse der Diagnosesitzung  
 ![Leistungs- und Diagnosezeitachse](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  
  
 Das Lineal oben auf der Seite zeigt die Zeitachse für die Profilerstellungsinformationen an. Diese Zeitachse gilt sowohl für das Diagramm **Auslastung des UI-Threads** als auch für das Diagramm **Visueller Durchsatz** . Sie können den Bereich des Berichtes eingrenzen, indem Sie die Navigationsleisten auf der Zeitachse ziehen, um ein Segment der Zeitachse auszuwählen.  
  
 Die Zeitachse zeigt auch alle Benutzermarkierungen an, die Sie eingefügt haben, sowie die Ereignisse des Aktivierungslebenszyklus der App.  
  
###  <a name="BKMK_UI_thread_utilization_graph"></a> Diagramm der Auslastung des UI-Threads  
 ![CPU-Auslastungsdiagramm](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")  
  
 Das Diagramm **Auslastung des UI-Threads (%)** ist ein Balkendiagramm, in dem für den Verlauf einer Datensammlung die relative Dauer in der jeweiligen Kategorie angezeigt wird.  
  
###  <a name="BKMK_Visual_throughput_FPS_graph"></a> Diagramm des visuellen Durchsatzes (FPS)  
 ![Diagramm des visuellen Durchsatzes](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")  
  
 Das Liniendiagramm **Visueller Durchsatz (FPS)** zeigt die Bilder pro Sekunde (FPS) auf der UI und dem Kompositionsthread für die App an.  
  
###  <a name="BKMK_Timeline_details_"></a> Zeitachse  
 Die Detailansicht werden Sie am häufigsten benötigen, um den Bericht zu analysieren. Sie zeigt eine detaillierte Ansicht der CPU-Auslastung Ihrer Anwendung, kategorisiert nach UI-Frameworksubsystem oder der Systemkomponente, die die CPU verbraucht.  
  
 Die folgenden Ereignisse werden unterstützt:  
  
|||  
|-|-|  
|**Analyse**|Für das Analysieren von XAML-Dateien und Erstellen von Objekten benötigte Zeit.<br /><br /> Beim Erweitern eines Knotens **Analyse** im Bereich **Zeitachsendetails** wird die Abhängigkeitskette aller XAML-Dateien anzeigt, die als Ergebnis des Ausgangsereignisses analysiert wurden. Dadurch können Sie unnötige Dateianalysen und Objekterstellungen in leistungssensiblen Szenarien ausmachen und entfernen.|  
|**Layout**|In großen Anwendungen können Tausende von Elementen zur gleichen Zeit auf dem Bildschirm angezeigt werden. Dies kann zu einer niedrigen UI-Framerate und einer entsprechend geringen Reaktionsfähigkeit der Anwendung führen. Das Layoutereignis bestimmt genau die Kosten für die Anordnung jedes Elements (d. h. die Zeit, die für Arrange-, Measure-, ApplyTemplate- und ArrangeOverride-Vorgänge aufgewendet wird) und erstellt die visuelle Struktur, die an einem Layoutdurchlauf beteiligt war. Sie können diese Visualisierung verwenden, um zu ermitteln, welche Ihrer logischen Strukturen bereinigt werden muss, oder um andere Verzögerungsmechanismen auszuwerten, um den Layoutdurchlauf zu optimieren.|  
|**Rendern**|Zeitaufwand für das Zeichnen von XAML-Elementen auf dem Bildschirm.|  
|**E/A**|Zeitaufwand für das Abrufen von Daten vom lokalen Datenträger oder von Netzwerkressourcen, auf die über die [Microsoft Windows Internet-API (WinINet)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa385331.aspx)zugegriffen wird.|  
|**App-Code**|Zeitaufwand für die Ausführung von Anwendungs- bzw. Benutzercode, der nicht mit der Analyse oder dem Layout im Zusammenhang steht.|  
|**Andere XAML**|Zeitaufwand für die Ausführung von XAML-Laufzeitcode.|  
  
> [!TIP]
>  Wählen Sie das Tool **CPU-Auslastung** zusammen mit dem Tool **Anwendungszeitachse** aus, wenn Sie mit der Profilerstellung beginnen, um App-Methoden anzuzeigen, die im UI-Thread ausgeführt werden. Durch das Verlagern von App-Code mit langer Ausführungsdauer in einen Hintergrundthread kann die UI-Reaktionsfähigkeit verbessert werden.  
  
####  <a name="BKMK_Customizing_Timeline_details_"></a> Anpassen von Zeitachsendetails  
 Verwenden Sie die Symbolleiste **Zeitachsendetails** zum Sortieren, Filtern und Angeben der Anmerkungen zu Einträgen in der Ansicht **Zeitachsendetails** .  
  
|||  
|-|-|  
|**Sortieren nach**|Sortieren Sie nach Startzeit oder Ereignisdauer.|  
|![Ereignisse nach Frame gruppieren](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Dient zum Hinzufügen oder Entfernen einer Kategorie **Frame** der obersten Ebene, die Ereignisse nach Frame gruppiert.|  
|![Filtern der Zeitachsendetails-Liste](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Filtert die Liste anhand ausgewählter Kategorien und der Dauer von Ereignissen.|  
|![Information zu Zeitachsendetails anpassen](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Ermöglicht die Angabe von Anmerkungen zu Ereignissen.|  
  
## <a name="see-also"></a>Siehe auch  
 [WPF Team Blog: New UI Performance Analysis Tool for WPF Applications (WPF-Teamblog: Neues Tool für die Analyse der Benutzeroberflächenleistung für WPF-Anwendungen)](http://blogs.msdn.com/b/wpf/archive/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications.aspx)  
 [Bewährte Methoden zur Leistungsverbesserung für UWP-Apps mit C++, C# und Visual Basic](http://msdn.microsoft.com/en-us/567bcefa-5da5-4e42-a4b8-1358c71adfa2)   
 [Optimieren der WPF-Anwendungsleistung](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)  
 [Profilerstellung in Visual Studio](../profiling/index.md)  
 [Tour zur Profilerstellungsfunktion](../profiling/profiling-feature-tour.md)
