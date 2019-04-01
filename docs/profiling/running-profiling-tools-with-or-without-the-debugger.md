---
title: Ausführen von Profilerstellungstools mit oder ohne Debugger | Microsoft-Dokumentation
ms.date: 11/04/2018
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63215d6350a4922ed416c8c48f006cd23c9e0728
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58323723"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Ausführen von Profilerstellungstools mit oder ohne Debugger

Visual Studio bietet eine Auswahl an Tools für Leistungsmessung und Profilerstellung. Einige Tools, wie z.B. die **CPU-Auslastung** und die **Arbeitsspeicherauslastung**, können mit oder ohne Debugger und in den Release- oder Debugbuildkonfigurationen ausgeführt werden. **Leistungsprofilertools** wie die **Anwendungszeitachse** können in Debug- oder Releasebuilds ausgeführt werden. In den Debugger integrierte Tools wie das Fenster **Diagnosetools** und die Registerkarte **Ereignisse** können nur während der Debugsitzungen ausgeführt werden.

>[!NOTE]
>Sie können die nicht in den Debugger integrierten Leistungstools unter Windows 7 und höher verwenden. Windows 8 oder höher ist erforderlich, um die in den Debugger integrierten Profilerstellungstools auszuführen.

Der nicht in den Debugger integrierte **Leistungsprofiler** und die in den Debugger integrierten **Diagnosetools** bieten verschiedene Informationen und Funktionen. In den Debugger integrierte Tools zeigen Breakpoints und Variablenwerte an. Nicht in den Debugger integrierte Tools bieten Ihnen Ergebnisse, die sich näher an der Endbenutzeroberfläche befinden.

Berücksichtigen Sie bei der Entscheidung, welche Tools und Ergebnisse Sie nutzen möchten, die folgenden Punkte:

- Externe Leistungsprobleme, wie z.B. Datei-E/A oder die Reaktionszeit des Netzwerks, werden in den Debuggertools ähnlich angezeigt wie in den nicht in den Debugger integrierten Tools.
- Bei Problemen, die durch CPU-intensive Aufrufe ausgelöst werden, kann es möglicherweise zu erheblichen Leistungsunterschieden zwischen Release- und Debugbuilds kommen. Überprüfen Sie, ob das Problem in Releasebuilds vorhanden ist.
- Wenn das Problem nur in Debugbuilds auftritt, ist es wahrscheinlich, dass Sie die nicht in den Debugger integrierten Tools nicht ausführen müssen. Bei Problemen mit Releasebuilds entscheiden Sie, ob die Debuggertools Ihnen bei weiteren Untersuchungen helfen können.
- Releasebuilds bieten Optimierungen wie Inlinefunktionsaufrufe und -konstanten, die ungenutzte Codepfade bereinigen und Variablen mit bestimmten Methoden speichern, sodass sie vom Debugger nicht genutzt werden können. Leistungsangaben der in den Debugger integrierten Tools sind weniger genau, da Debugbuilds diese Optimierungen nicht vorweisen.
- Der Debugger selbst ändert Leistungszeiten, während er erforderliche Debuggervorgänge durchführt, wie z.B. das Abfangen von Ausnahmen- und Modullastereignissen.
- Leistungsangaben zu Releasebuilds in den **Leistungsprofilertools** sind am präzisesten und genauesten. In den Debugger integrierte Toolergebnisse sind besonders nützlich, wenn es um den Vergleich mit anderen debuggingbezogenen Messungen geht.

##  <a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Sammeln von Profilerstellungsdaten während des Debuggens

Wenn Sie mit dem Debuggen in Visual Studio beginnen, indem Sie **Debuggen** > **Debuggen starten** wählen oder **F5** drücken, wird das Fenster **Diagnosetools** standardmäßig angezeigt. Klicken Sie auf **Debuggen** > **Fenster** > **Diagnosetools anzeigen**, um dieses Fenster manuell zu öffnen. Das Fenster **Diagnosetools** enthält Informationen über Ereignisse, den Prozessarbeitsspeicher und die CPU-Auslastung.

![Diagnosetools](../profiling/media/diagnostictools-update1.png "Diagnostic Tools")

- Klicken Sie auf das Symbol für **Einstellungen** in der Symbolleiste, um die **Arbeitsspeicherauslastung**, die **UI-Analyse**, und die **CPU-Auslastung** zu anzuzeigen.

- Wählen Sie **Einstellungen** in der Dropdownliste **Einstellungen**, um die Eigenschaftenseiten der **Diagnosetools** mit weiteren Optionen zu öffnen.

- Wenn Sie Visual Studio Enterprise ausführen, können Sie IntelliTrace in Visual Studio unter **Tools** > **Optionen** > **IntelliTrace** aktivieren oder deaktivieren.

Die Diagnosesitzung endet, wenn Sie das Debugging beenden.

Sie können auch **Diagnosetools** aufrufen, um Remotedebugziele anzuzeigen. Der Visual Studio-Remotedebugger muss für das Remotedebuggen und die Profilerstellung installiert sein und auf dem Remoteziel ausgeführt werden.
- Weitere Informationen zum Remotedebuggen und zur Profilerstellung von Desktop-App-Projekten finden Sie im Artikel zum [Remotedebuggen](../debugger/remote-debugging.md).
- Weitere Informationen zum Remotedebuggen und zur Profilerstellung von UWP-Apps finden Sie unter [Debug UWP apps on remote machines (Debuggen von UWP-Apps auf Remotecomputern)](../debugger/run-windows-store-apps-on-a-remote-machine.md).

### <a name="the-events-tab"></a>Die Registerkarte „Ereignisse“

Während einer Debugsitzung werden die auftretenden Diagnoseereignisse auf der Registerkarte **Ereignisse** im Fenster **Diagnosetools** aufgelistet. Mit Kategoriepräfixen wie **Breakpoint** und **Datei** können Sie schnell die Liste nach einer Kategorie durchsuchen oder die Kategorien überspringen, die für Sie gerade nicht relevant sind.

Verwenden Sie in der Dropdownliste **Filter**, um Ereignisse anzuzeigen oder auszublenden, indem Sie bestimmte Ereigniskategorien auswählen oder abwählen.

![Diagnoseereignisfilter](../profiling/media/diagnosticeventfilter.png "Diagnostic Event Filter")

Verwenden Sie das Suchfeld, um eine bestimmte Zeichenfolge in der Ereignisliste zu suchen. Dies sind die Suchergebnisse für die Zeichenfolge „Name“, die mit vier Ereignissen übereinstimmt:

![Diagnoseereignissuche](../profiling/media/diagnosticseventsearch.png "Diagnostic Event Search")

Weitere Informationen finden Sie unter [Suchen und Filtern auf der Registerkarte "Ereignisse" im Fenster "Diagnosetools"](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Sammeln von Profilerstellungsdaten ohne das Debuggen

Sie können zum Erfassen von Leistungsdaten ohne Debuggen **Leistungsprofilertools** ausführen. Für die Ausführung einiger Profilerstellungstools sind Administratorrechte erforderlich. Öffnen Sie daher entweder Visual Studio als Administrator, oder führen Sie die Tools als Administrator aus, wenn Sie die Diagnosesitzung starten.

1. Öffnen Sie ein Projekt in Visual Studio, und wählen Sie **Debuggen** > **Leistungsprofiler** aus, oder drücken Sie **Alt**+**F2**.

1. Wählen Sie auf der Diagnosestartseite mindestens ein Tools aus, das ausgeführt werden soll. Es werden nur die Tools angezeigt, die für den Projekttyp, das Betriebssystem und die Programmiersprache infrage kommen. Wählen Sie **Alle Tools anzeigen**, um auch Tools anzuzeigen, die für diese Diagnosesitzung deaktiviert sind. Für eine C#-UWP-App kann die Auswahl zum Beispiel folgendermaßen aussehen:

   ![Diagnosetools auswählen](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Klicken Sie zum Starten der Diagnosesitzung auf **Start**.

   Während Sie die Sitzung ausführen, zeigen einige Tools Diagramme mit Echtzeitdaten auf der Seite der Diagnosetools an.

    ![Daten auf der Seite „Leistung und Diagnose“ erfassen](../profiling/media/pdhub_collectdata.png "Hub-Datenerfassung")

1. Klicken Sie zum Beenden der Diagnosesitzung auf **Sammlung beenden**.

   Die analysierten Daten werden unter **Bericht** angezeigt.

Sie können die Berichte auch speichern und über die Liste der **zuletzt geöffneten Sitzungen** auf der Startseite für die Diagnosetools öffnen.

![Öffnen einer gespeicherten Diagnosesitzungsdatei](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>Der Profilerstellungsbericht
 ![Diagnosetools-Bericht](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![Schritt 1](../profiling/media/procguid_1.png "ProcGuid_1")|Die Zeitachse zeigt die Länge der Profilerstellungssitzung, der App-Lebenszyklusaktivierungsereignisse und der Benutzermarkierungen an.|
|![Schritt 2](../profiling/media/procguid_2.png "ProcGuid_2")|Sie können den Bericht auf einen Teil der Zeitachse einschränken, indem Sie die blauen Striche ziehen, um einen Bereich der Zeitachse auszuwählen.|
|![Schritt 3](../profiling/media/procguid_3.png "ProcGuid_3")|Jedes Diagnosetool zeigt mindestens ein Hauptdiagramm an. Wenn Ihre Diagnosesitzung mehr als ein Tool vorweist, werden alle ihre Hauptdiagramme angezeigt.|
|![Schritt 4](../profiling/media/procguid_4.png "ProcGuid_4")|Sie können die einzelnen Diagramme jedes Tools auf- und zuklappen.|
|![Schritt 5](../profiling/media/procguid_6.png "ProcGuid_6")|Wenn die Daten aus mehr als einem Tool stammen, werden die Tooldetails in Registerkarten gesammelt.|
|![Schritt 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|Die untere Hälfte des Berichts zeigt mindestens eine Detailansicht für jedes Tool an. Sie können die Ansicht filtern, indem Sie die Bereiche auf der Zeitachse auswählen.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Ausführen von Diagnosesitzungen in installierten oder ausgeführten Apps

 Sie können nicht nur Ihre App im Visual Studio-Projekt starten, sondern auch Diagnosesitzungen auf alternativen Zielen ausführen. Beispielsweise empfiehlt es sich, die Diagnose von Leistungsproblemen in einer App durchzuführen, die über den Windows App Store installiert wurde.

 ![Analyseziel für Diagnosetools auswählen](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

 Sie können Apps starten, die bereits installiert sind, oder Sie können die Diagnosetools an Apps und Prozesse anfügen, die bereits ausgeführt werden. Wenn Sie **Ausgeführte App** oder **Installierte App** auswählen, können Sie die App aus einer Liste aller gefundenen Apps im angegebenen Bereitstellungsziel auswählen. Dieses Ziel kann ein lokaler oder ein Remotecomputer sein.

 ![Auswählen einer ausgeführten oder installierten App für die Diagnose](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

## <a name="see-also"></a>Siehe auch

Im Folgenden finden Sie Blogbeiträge und MSDN-Artikel vom Diagnoseentwicklungsteam:
- [MSDN Magazine: Analyze Performance While Debugging in Visual Studio 2015 (Analysieren der Leistung während des Debuggings in Visual Studio 2015)](https://msdn.microsoft.com/magazine/dn973013.aspx)

- [MSDN Magazine: Use IntelliTrace to Diagnose Issues Faster (Schnellere Problemdiagnose mit IntelliTrace)](https://msdn.microsoft.com/magazine/dn973014.aspx)

- [Blogbeitrag: Diagnosing Event Handler Leaks with the Memory Usage Tool in Visual Studio 2015 (Diagnostizieren von Ereignishandlerverlusten mit dem Speicherauslastungstool in Visual Studio 2015)](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)

- [Video: Historical Debugging with IntelliTrace in Microsoft Visual Studio Ultimate 2015 (Verlaufsbezogenes Debuggen mit IntelliTrace in Microsoft Visual Studio Ultimate 2015)](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)

- [Video: Debugging Performance Issues Using Visual Studio 2015 (Debuggen von Leistungsproblemen mit Visual Studio 2015)](https://channel9.msdn.com/Events/Build/2015/3-731)

- [PerfTips: Performance Information at-a-glance while Debugging with Visual Studio (Leistungsinformationen auf einen Blick beim Debuggen mit Visual Studio)](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)

- [Diagnostic Tools debugger window in Visual Studio 2015 (Fenster des Diagnosetoolsdebugger in Visual Studio 2015)](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)

- [IntelliTrace in Visual Studio Enterprise 2015](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
