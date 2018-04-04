---
title: Tour zur Profilerstellungsfunktion | Microsoft-Dokumentation
ms.custom: H1HackMay2017
ms.date: 05/18/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugger
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
caps.latest.revision: 1
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b4662b1e498303bd7a4e09acd78db43519c142b1
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="profiling-feature-tour"></a>Tour zur Profilerstellungsfunktion

Visual Studio bietet eine Vielzahl von Profilerstellungstools, um Ihnen bei der Diagnose von unterschiedlichen Leistungsprobleme zu helfen, die von dem App-Typ abhängen.

Die Profilerstellungstools, auf die Sie während einer Debugsitzung zugreifen können, stehen im Fenster „Diagnosetools“ zur Verfügung. Das Fenster „Diagnosetools“ wird automatisch angezeigt, wenn Sie es nicht deaktiviert haben. Klicken Sie auf **Debuggen/Windows/Diagnosetools anzeigen**, um das Fenster aufzurufen. Wenn das Fenster geöffnet ist, können Sie Tools auswählen, für die Sie Daten sammeln möchten.

![Fenster „Diagnosetools“](../profiling/media/prof-tour-diagnostic-tools.png "Diagnosetools")

Während Sie Debuggen, können Sie das **Diagnosetools**-Fenster zum Analysieren der CPU und Speicherauslastung verwenden, und Sie können Ereignisse anzeigen, die Leistungsbezogene Informationen zeigen.

![Zusammenfassungsansicht der Diagnosetools](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Zusammenfassung der Diagnosetools")

Das Fenster **Diagnosetools** ist häufig die bevorzugte Methode für die App-Profilerstellung, aber für Releasebuilds können Sie stattdessen auch eine nachträgliche Analyse Ihrer App durchführen. Weitere Informationen zu den verschiedenen Herangehensweisen finden Sie unter [Ausführen von Profilerstellungstools mit oder ohne Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Informationen zur Unterstützung der Profilerstellungstools für die verschiedenen App-Typen finden Sie unter [Welches Tool soll ich verwenden?](#tool_support_info).

## <a name="analyze-cpu-usage"></a>Analysieren der CPU-Auslastung

Mit dem CPU-Auslastungstool können Sie die Analyse der Leistung Ihrer App starten. So erfahren Sie mehr über die CPU-Ressourcen, die Ihre App in Anspruch nimmt. Eine ausführlichere Anleitung für die CPU-Auslastung, finden Sie unter [Beginner's Guide to Performance Profiling (Leitfaden für Einsteiger zur Leistungsprofilerstellung)](../profiling/beginners-guide-to-performance-profiling.md).

Wählen Sie aus der Ansicht **Zusammenfassung** der Diagnosetools **CPU-Profilerstellung aktivieren** aus. (Sie müssen in einer Debugsitzung sein.)

![Aktivieren der CPU-Auslastung in den Diagnosetools](../profiling/media/prof-tour-enable-cpu-profiling.png "Diagnosetools: Aktivieren der CPU-Auslastung")

Um das Tool am effektivsten verwenden zu können, legen Sie zwei Haltepunkte im Code fest, einen am Anfang und einen am Ende der Funktion, oder in dem Codebereich, den Sie analysieren möchten. Überprüfen Sie die Profilerstellungsdaten, wenn Sie beim zweiten Haltepunkt angehalten werden.

Die Ansicht **CPU-Auslastung** zeigt eine Liste der Funktionen, geordnet nach den am längsten ausgeführten, mit der längsten Funktion oben. Dies kann helfen, Sie zu Funktionen zu führen, in denen Leistungsengpässe auftauchen.

![Ansicht CPU-Auslastung in den Diagnosetools](../profiling/media/prof-tour-cpu-usage.png "CPU-Auslastung in den Diagnosetools")

Doppelklicken Sie auf eine Funktion, an der Sie interessiert sind. Ihnen wird eine detailliertere „Schmetterlingsansicht“ aus drei Bereichen angezeigt. Die ausgewählte Funktion befindet sich in der Mitte des Fensters, die aufrufende Funktion auf der linken Seite und die aufgerufenen Funktionen auf der rechten Seite. Unter **Funktionsrumpf** wird die Gesamtzeit (und der Prozentsatz der Zeit) angezeigt, die im Funktionsrumpf aufgewendet wurde. Die Zeit, die in aufrufenden und aufgerufenen Funktionen aufgewendet wurde, ist nicht enthalten. Diese Daten können bei der Bewertung helfen, ob die Funktion selbst ein Leistungsengpass ist.

![Diagnosetools-Schmetterlingsansicht mit Aufrufer/Aufgerufenem](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Diagnosetools-Ansicht mit Aufrufer/Aufgerufenem")

## <a name="analyze-memory-usage"></a>Analysieren der Speicherauslastung

Mit dem Fenster „Diagnosetools“ können Sie auch die Speicherauslastung in Ihrer App bewerten. Beispielsweise können Sie die Anzahl und Größe der Objekte auf dem Heap anzeigen. Ausführlichere Anweisungen zum Analysieren von Speicher finden Sie unter [Analyze Memory Usage](../profiling/memory-usage.md) (Analysieren der Arbeitsspeicherauslastung).

Um die Speicherauslastung zu analysieren, müssen Sie mindestens eine Momentaufnahme des Speichers während des Debuggens machen. Häufig ist es zum Analysieren von Arbeitsspeicher am Besten, wenn man zwei Momentaufnahmen macht, die erste direkt vor einem vermuteten Arbeitsspeicherproblem und die zweite Momentaufnahme direkt nach dem Auftreten eines vermuteten Arbeitsspeicherproblems. Anschließend können Sie einen Vergleich der zwei Momentaufnahmen anzeigen und sehen, was genau sich geändert hat.

![Erstellen einer Momentaufnahme in den Diagnosetools](../profiling/media/prof-tour-take-snapshots.gif "Erstellen von Momentaufnahmen in den Diagnosetools")

Bei Auswahl einer der Pfeil-Links erhalten Sie eine differenzielle Ansicht des Heap (ein roter Pfeil ![Zunahme der Speicherauslastung](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zunahme der Speicherauslastung") zeigt eine zunehmende Objektanzahl (links) oder eine höhere Heapgröße (rechts)). Wenn Sie den richtigen Link klicken, erhalten Sie eine differenzielle Heapansicht, sortiert nach Objekten, die in der Heapgröße am meisten erhöht wurden. Dadurch können Sie Speicherprobleme ermitteln. Zum Beispiel wurden in der folgenden Abbildung die Bytes mithilfe des `ClassHandlersStore`-Objekts in der zweiten Momentaufnahme um 3492 Bytes erhöht.

![Differenzielle Heapansicht der Diagnosetools](../profiling/media/prof-tour-mem-usage-diff-heap.png "Differenzielle Heapansicht der Diagnosetools")

Wenn Sie statt in der Ansicht **Speicherauslastung** auf den Link auf der linken Seite klicken, ist die Heapansicht nach der Objektanzahl organisiert. Die Objekte eines bestimmten Typs, der die Zahl am meisten erhöht hat, werden oben angezeigt (sortiert nach der Spalte **Anzahlunterschied**).

## <a name="examine-performance-events"></a>Untersuchen der Leistungsereignisse

Die Ansicht **Ereignisse** in den Diagnosetools zeigt verschiedene Ereignisse an, die während des Debuggens auftreten, z.B. die Einstellung eines Haltepunkts oder einer schrittweisen Ausführung von Code. Sie können Informationen wie z.B. die Dauer des Ereignisses überprüfen (gemessen daran, wann der Debugger zuletzt angehalten wurde oder wann die App gestartet ist). Wenn Sie den Code schrittweise ausführen (F10, F11), zeigt die **Ereignisse**-Ansicht die Dauer der App-Laufzeit aus dem vorherigen Schritt zum aktuellen Schritt.

![Ereignisansicht in den Diagnosetools](../profiling/media/prof-tour-events.png "Anzeigen von Ereignissen in den Diagnosetools")

 > [!NOTE]
 > Wenn Sie über Visual Studio Enterprise verfügen, sehen Sie auch [IntelliTrace-Ereignisse](../debugger/intellitrace.md) auf dieser Registerkarte.

Die gleichen Ereignisse werden auch im Code-Editor angezeigt, den Sie als PerfTips anzeigen können.

![Profilerstellungstour PerfTips](../profiling/media/prof-tour-perf-tips.png "Profilerstellungstour PerfTips")

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>Überprüfen der UI-Leistung und Barrierefreiheits-Ereignisse (UWP)

In Ihren UWP-Apps können Sie die **Benutzeroberfläche Analye** im Fenster „Diagnosetools“ aktivieren. Das Tool sucht nach gemeinsamen Leistungs- oder Barrierefreiheitsproblemen, und zeigt sie in der Ansicht **Ereignisse** an, während Sie debuggen. Die Ereignisbeschreibungen bieten Informationen zur Problembehebung.

![Anzeigen von Ereignissen der Benutzeroberflächenanalyse in den Diagnosetools](../profiling/media/prof-tour-ui-analysis.png "Anzeigen von Ereignissen der Benutzeroberflächenanalyse in den Diagnosetools")

## <a name="profile-release-builds-without-the-debugger"></a>Profilerstellung für Releasebuilds ohne den Debugger

Profilerstellungstools wie die CPU-Auslastung und Speicherauslastung können mit dem Debugger verwendet werden (siehe frühere Abschnitte), oder Sie führen die Profilerstellungstools mithilfe des Leistungsprofilers aus, der Analysen für **Release**builds erstellen soll. Im Leistungsprofiler können Sie Diagnoseinformationen sammeln, während die App ausgeführt wird, und anschließend die gesammelten Informationen überprüfen, nachdem die App angehalten wird. Weitere Informationen zu den verschiedenen Herangehensweisen finden Sie unter [Ausführen von Profilerstellungstools mit oder ohne den Debugger](../profiling/running-profiling-tools-with-or-without-the-debugger.md) .

![Leistungsprofiler](../profiling/media/prof-tour-performance-profiler.png "Leistungsprofiler")

Öffnen Sie durch Auswählen von **Debuggen/Performance Profiler** den Leistungsprofiler.

Im Fenster können Sie mehrere Profilerstellungstools in einigen Szenarios auswählen. Tools wie z.B. CPU-Auslastung stellen möglicherweise ergänzende Daten bereit, die Sie als Hilfe bei Ihrer Analyse verwenden können.

## <a name="analyze-resource-consumption-xaml"></a>Analysieren des Ressourcenverbrauchs (XAML)

In XAML-Apps, z.B. Windows Desktop WPF-Apps und UWP-Apps, können Sie mit der Anwendungszeitachse den Ressourcenverbrauch analysieren. Sie können analysieren, wie viel Zeit Ihre Anwendung zum Vorbereiten von Benutzeroberflächenframes (Layout und Render), von Netzwerk- und Datenträgeranforderungen sowie in Szenarios wie Starten von Anwendungen, Laden von Seiten und Ändern von Fenstergrößen benötigt. Wählen Sie die **Anwendungszeitachse** im Leistungsprofiler aus und anschließend **Starten**, um das Tool zu verwenden. Navigieren Sie in Ihrer App zum Szenario mit einem vermuteten Ressourcenverbrauch-Problem, und wählen Sie anschließend **Auflistung beenden** zum Generieren des Berichts aus.

Geringe Framerates im Diagramm **Visueller Durchsatz** entsprechen möglicherweise visuellen Problemen, die Sie beim Ausführen der App sehen. Auf ähnliche Weise können hohe Zahlen des Diagramms **Auslastung des UI-Thread** Problemen mit der Reaktionsfähigkeit der Benutzeroberfläche entsprechen. Im Bericht können Sie den Zeitraum mit einem vermuteten Leistungsproblem auswählen, und anschließend die detaillierten UI-Threadaktivitäten in der Zeitachsendetailansicht (unten) überprüfen.

![Profilerstellungstool „Anwendungszeitachse“](../profiling/media/prof-tour-application-timeline.gif "Profilerstellungstool „Anwendungszeitachse“")

In der Zeitachsendetailansicht finden Sie Informationen, wie z.B. den Typ der Aktivität (oder das beteiligte Benutzeroberflächenelement) sowie die Dauer der Aktivität. In der Abbildung benötigt beispielsweise ein **Layout**-Ereignis für ein Grid-Steuerelement 57,53 ms.

Weitere Informationen finden Sie unter [Anwendungszeitachse](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>Analysieren der GPU-Nutzung (Direct3D)

In Direct3D-Apps (Direct3D-Komponenten müssen in C++ vorhanden sein) können Sie Aktivitäten auf der GPU überprüfen und Leistungsprobleme analysieren. Weitere Informationen erhalten Sie unter [GPU-Nutzung](../debugger/gpu-usage.md). Wählen Sie die **GPU-Nutzung** im Leistungsprofiler und anschließend **Starten** aus, um das Tool zu verwenden. Durchlaufen Sie in Ihrer Anwendung das Szenario, für das Sie ein Profil erstellen wollen, und wählen Sie anschließend **Auflistung beenden**, um einen Bericht zu generieren.

Wenn Sie einen Zeitraum im Diagramm und **Details anzeigen** auswählen, wird eine detaillierte Ansicht wird im unteren Bereich angezeigt. In der Detailansicht können Sie überprüfen, wie viel Aktivität auf jeder CPU und GPU vorhanden ist. Wählen Sie Ereignisse im untersten Bereich aus, um Popups in der Zeitachse aufzurufen. Wählen Sie z.B. das **Vorhanden**-Ereignis aus, um die **Vorhanden**-Aufruf-Popups anzuzeigen. (Die hellgrauen vertikalen Vsync-Zeilen können als Verweis verwendet werden, um zu verstehen, ob bestimmte **Vorhanden**-Aufrufe Vsync verpasst haben. Es muss ein **Vorhanden**-Aufruf zwischen jeden zwei Vsyncs in der Reihenfolge geben, damit die App kontinuierlich 60 FPS erreicht.)

![Profilerstellungstool „GPU-Nutzung“](../profiling/media/prof-tour-gpu-usage.png "Dialogfeld „GPU-Nutzung“")

Die Diagramme können auch bestimmen, ob es CPU-gebundene oder GPU-gebundene Leistungsengpässe gibt.

## <a name="analyze-performance-javascript"></a>Analysieren der Leistung (JavaScript)

Für UWP-Apps können Sie das JavaScript-Speichertool und das Tool für die Reaktionsfähigkeit der HTML-Benutzeroberfläche verwenden.

Das JavaScript-Speichertool ähnelt dem für andere App-Typen verfügbaren Speicherauslastungstool. Mit diesem Tool können Sie die Speicherauslastung verstehen und Speicherverluste in Ihrer App finden. Weitere Informationen zu diesem Tool finden Sie unter [JavaScript-Memory](../profiling/javascript-memory.md).

![Profilerstellungstool „JavaScript-Speicher“](../profiling/media/diagjsmemory.png "DiagJSMemory")

Verwenden Sie das Tool für die Reaktionsfähigkeit der HTML-Benutzeroberfläche, um die UI-Reaktionsfähigkeit, die langsame Ladezeit und die langsamen visuellen Updates in UWP-Apps zu diagnostizieren. Der Verbrauch ähnelt dem Anwendungszeitachsen-Tool für andere App-Typen. Weitere Informationen finden Sie unter [HTML-UI-Reaktionsfähigkeit](../profiling/html-ui-responsiveness.md).

![Profilerstellungstool „HTML-UI-Reaktionsfähigkeit“](../profiling/media/diaghtmlresp.png "DiagHTMLResp")

## <a name="analyze-network-usage-uwp"></a>Analysieren der Netzwerkverwendung (UWP)

In UWP-Apps können Sie Netzwerkoperationen mithilfe der `Windows.Web.Http`-API analysieren. Mit diesem Tool können Sie Probleme wie Zugriffs-und Authentifizierungsprobleme, falsche Cacheverwendung und schlechte Anzeige- und Downloadleistung lösen. Wählen Sie **Netzwerk** im Leistungsprofiler und anschließend **Starten** aus, um das Tool zu verwenden. Durchlaufen Sie in Ihrer Anwendung das Szenario, das `Windows.Web.Http` verwendet, und wählen Sie anschließend **Auflistung beenden** aus, um einen Bericht zu generieren.

![Profilerstellungstool „Netzwerkverwendung“](../profiling/media/prof-tour-network-usage.png "Dialogfeld „Netzwerkverwendung“")

Wählen Sie einen Vorgang in der Ansicht „Zusammenfassung“ aus, um mehr Details anzuzeigen.

![Ausführliche Informationen im Tool „Netzwerkverwendung“](../profiling/media/prof-tour-network-usage-details.png "Dialogfeld mit Details zur Netzwerkverwendung")

Weitere Informationen finden Sie unter [Netzwerkverwendung](../profiling/network-usage.md).

## <a name="analyze-performance-legacy-tools"></a>Analysieren der Leistung (Legacytools)

Wenn Sie Funktionen wie z.B. Instrumentation benötigen, die derzeit nicht in der CPU-Nutzung oder in den Speicherauslastungstools vorhanden sind, und Desktop- oder ASP.NET-Apps ausgeführt werden, können Sie für die Profilerstellung den Leistungs-Explorer verwenden. (Wird in UWP-Apps nicht unterstützt.) Weitere Informationen finden Sie unter [Leistungs-Explorer](../profiling/performance-explorer.md).

![Tool „Leistungs-Explorer“](../profiling/media/prof-tour-performance-explorer.png "Leistungs-Explorer")

## <a name="tool_support_info"></a>Welches Tool soll ich verwenden?  

Hier sehen Sie eine Tabelle, in der die verschiedenen Tools aufgelistet sind, die Visual Studio anbietet sowie die verschiedenen Projekttypen, die Sie mit diesen verwenden können:
  
|Leistungstool|Windows-Desktop|UWP|ASP.NET/ASP.NET Core| 
|----------------------|---------------------|-------------|-------------|  
|[Speicherauslastung](../profiling/memory-usage.md)|ja|ja|ja| 
|[CPU-Auslastung](../profiling/cpu-usage.md)|ja (siehe Hinweis)|ja|ja (siehe Hinweis)|
|[GPU-Nutzung](../debugger/gpu-usage.md)|ja|ja|Nein| 
|[Anwendungszeitachse](../profiling/application-timeline.md)|ja|ja|Nein|
|[PerfTips](../profiling/perftips.md)|ja|ja für XAML, nicht für HTML|ja|
|[Leistungs-Explorer](../profiling/performance-explorer.md)|ja|Nein|ja|
|[IntelliTrace](../debugger/intellitrace.md)|Nur .NET mit Visual Studio Enterprise|Nur .NET mit Visual Studio Enterprise|Nur .NET mit Visual Studio Enterprise|
|[Netzwerkverwendung](../profiling/network-usage.md)|Nein|ja|Nein|
|[HTML UI responsiveness](../profiling/html-ui-responsiveness.md)|Nein|ja für HTML, nicht für XAML|Nein| 
|[JavaScript-Speicher](../profiling/javascript-memory.md)|Nein|ja für HTML, nicht für XAML|Nein|

> [!NOTE]
> Das CPU-Auslastungstool bietet derzeit keine exakten Ergebnisse mit portablen PBDs für .NET Core und ASP.NET Core. Verwenden Sie stattdessen vollständige PDBs.

## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)