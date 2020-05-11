---
title: Ausführen von Profilerstellungstools mit oder ohne Debugger | Microsoft-Dokumentation
ms.date: 04/02/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf544b3bec9b492f1d1669549ba5501a52f7d5f2
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638802"
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

Zum Überprüfen der CPU-Auslastung können Sie das Tool mithilfe von Befehlszeilentools auf einem Remotecomputer ausführen.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Sammeln von Profilerstellungsdaten während des Debuggens

Wenn Sie mit dem Debuggen in Visual Studio beginnen, indem Sie **Debuggen** > **Debuggen starten** wählen oder **F5** drücken, wird das Fenster **Diagnosetools** standardmäßig angezeigt. Klicken Sie auf **Debuggen** > **Fenster** > **Diagnosetools anzeigen**, um dieses Fenster manuell zu öffnen. Das Fenster **Diagnosetools** enthält Informationen über Ereignisse, den Prozessarbeitsspeicher und die CPU-Auslastung.

![Diagnosetools](../profiling/media/diagnostictools-update1.png "Diagnosetools")

- Klicken Sie in der Symbolleiste auf das Symbol **Einstellungen**, um auszuwählen, ob die **Arbeitsspeicherauslastung** oder die **CPU-Auslastung** angezeigt werden soll.

- Wählen Sie **Einstellungen** in der Dropdownliste **Einstellungen**, um die Eigenschaftenseiten der **Diagnosetools** mit weiteren Optionen zu öffnen.

- Wenn Sie Visual Studio Enterprise ausführen, können Sie IntelliTrace in Visual Studio unter **Tools** > **Optionen** > **IntelliTrace** aktivieren oder deaktivieren.

Die Diagnosesitzung endet, wenn Sie das Debugging beenden.

### <a name="the-events-tab"></a>Die Registerkarte „Ereignisse“

Während einer Debugsitzung werden die auftretenden Diagnoseereignisse auf der Registerkarte **Ereignisse** im Fenster **Diagnosetools** aufgelistet. Mit Kategoriepräfixen wie **Breakpoint** und **Datei** können Sie schnell die Liste nach einer Kategorie durchsuchen oder die Kategorien überspringen, die für Sie gerade nicht relevant sind.

Verwenden Sie in der Dropdownliste **Filter**, um Ereignisse anzuzeigen oder auszublenden, indem Sie bestimmte Ereigniskategorien auswählen oder abwählen.

![Filtern von Diagnoseereignissen](../profiling/media/diagnosticeventfilter.png "Filtern von Diagnoseereignissen")

Verwenden Sie das Suchfeld, um eine bestimmte Zeichenfolge in der Ereignisliste zu suchen. Dies sind die Suchergebnisse für die Zeichenfolge „Name“, die mit vier Ereignissen übereinstimmt:

![Suchen nach Diagnoseereignissen](../profiling/media/diagnosticseventsearch.png "Suchen nach Diagnoseereignissen")

Weitere Informationen finden Sie unter [Suchen und Filtern auf der Registerkarte "Ereignisse" im Fenster "Diagnosetools"](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Sammeln von Profilerstellungsdaten ohne das Debuggen

Sie können zum Erfassen von Leistungsdaten ohne Debuggen **Leistungsprofilertools** ausführen. Für die Ausführung einiger Profilerstellungstools sind Administratorrechte erforderlich. Öffnen Sie daher entweder Visual Studio als Administrator, oder führen Sie die Tools als Administrator aus, wenn Sie die Diagnosesitzung starten.

1. Legen Sie mit einem in Visual Studio geöffneten Projekt die Konfiguration der Projektmappe auf **Release** fest, und wählen Sie als Bereitstellungsziel **Lokaler Windows-Debugger** (oder **Lokaler Computer**) aus.

1. Klicken Sie auf **Debuggen** > **Leistungs-Profiler**, oder drücken Sie **ALT**+**F2**.

1. Wählen Sie auf der Diagnosestartseite mindestens ein Tools aus, das ausgeführt werden soll. Es werden nur die Tools angezeigt, die für den Projekttyp, das Betriebssystem und die Programmiersprache infrage kommen. Wählen Sie **Alle Tools anzeigen**, um auch Tools anzuzeigen, die für diese Diagnosesitzung deaktiviert sind. Für eine C#-UWP-App kann die Auswahl zum Beispiel folgendermaßen aussehen:

   ![Auswählen von Diagnosetools](../profiling/media/diag_selecttool.png "DIAG_SelectTool")

1. Klicken Sie zum Starten der Diagnosesitzung auf **Start**.

   Während Sie die Sitzung ausführen, zeigen einige Tools Diagramme mit Echtzeitdaten auf der Seite der Diagnosetools an.

    ![Sammeln von Daten im Leistungs- und Diagnosehub](../profiling/media/pdhub_collectdata.png "Sammeln von Daten im Hub")

1. Klicken Sie zum Beenden der Diagnosesitzung auf **Sammlung beenden**.

   Die analysierten Daten werden unter **Bericht** angezeigt.

Sie können die Berichte auch speichern und über die Liste der **zuletzt geöffneten Sitzungen** auf der Startseite für die Diagnosetools öffnen.

![Öffnen einer gespeicherten Diagnosesitzungsdatei](../profiling/media/pdhub_openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

### <a name="the-profiling-report"></a>Der Profilerstellungsbericht
 ![Bericht zu Diagnosetools](../profiling/media/diag_report.png "DIAG_Report")

|||
|-|-|
|![Schritt 1](../profiling/media/procguid_1.png "ProcGuid_1")|Die Zeitachse zeigt die Länge der Profilerstellungssitzung, der App-Lebenszyklusaktivierungsereignisse und der Benutzermarkierungen an.|
|![Schritt 2](../profiling/media/procguid_2.png "ProcGuid_2")|Sie können den Bericht auf einen Teil der Zeitachse einschränken, indem Sie die blauen Striche ziehen, um einen Bereich der Zeitachse auszuwählen.|
|![Schritt 3](../profiling/media/procguid_3.png "ProcGuid_3")|Jedes Diagnosetool zeigt mindestens ein Hauptdiagramm an. Wenn Ihre Diagnosesitzung mehr als ein Tool vorweist, werden alle ihre Hauptdiagramme angezeigt.|
|![Schritt 4](../profiling/media/procguid_4.png "ProcGuid_4")|Sie können die einzelnen Diagramme jedes Tools auf- und zuklappen.|
|![Schritt 5](../profiling/media/procguid_6.png "ProcGuid_6")|Wenn die Daten aus mehr als einem Tool stammen, werden die Tooldetails in Registerkarten gesammelt.|
|![Schritt 6](../profiling/media/procguid_6a.png "ProcGuid_6a")|Die untere Hälfte des Berichts zeigt mindestens eine Detailansicht für jedes Tool an. Sie können die Ansicht filtern, indem Sie die Bereiche auf der Zeitachse auswählen.|

## <a name="run-diagnostic-sessions-on-installed-or-running-apps"></a>Ausführen von Diagnosesitzungen in installierten oder ausgeführten Apps

Sie können nicht nur Ihre App im Visual Studio-Projekt starten, sondern auch Diagnosesitzungen auf alternativen Zielen ausführen. Beispielsweise empfiehlt es sich, die Diagnose von Leistungsproblemen in einer App durchzuführen, die über den Windows App Store installiert wurde. Das Ziel können Sie im Leistungs-Profiler in der Dropdownliste unter **Ziel ändern** festlegen.

![Auswählen des Analyseziels für Diagnosetools](../profiling/media/pdhub_chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")

Sie können Apps starten, die bereits installiert sind, oder Sie können die Diagnosetools an Apps und Prozesse anfügen, die bereits ausgeführt werden.

Wenn Sie eine **Ausführbare Datei** als Analyseziel auswählen, können Sie den Pfad zu einer *EXE*-Datei auf einem lokalen oder Remotecomputer eingeben. In beiden Fällen wird die *EXE*-Datei lokal ausgeführt. Es wird jedoch empfohlen, dass Sie ein Profil Ihrer App erstellen, indem Sie die Projektmappe in Visual Studio öffnen.

Wenn Sie **Ausgeführte App** oder **Installierte App** für eine UWP-App auswählen, können Sie die App aus einer Liste aller gefundenen Apps auf dem angegebenen Bereitstellungsziel auswählen. Dieses Ziel kann ein lokaler oder ein Remotecomputer sein. Für die Profilerstellung für eine UWP-App auf einem Remotecomputer müssen Sie im Dialogfeld **Remoteverbindungen** die Option **Universell (unverschlüsseltes Protokoll)** auswählen.

![Auswählen einer ausgeführten oder installierten App für die Diagnose](../profiling/media/pdhub_selectrunningapp.png "PDHUB_SelectRunningApp")

> [!NOTE]
> Informationen über andere Szenarios, die die Remoteverwendung von Profilerstellungstools erfordern, finden Sie unter [Messen der Anwendungsleistung über die Befehlszeile](../profiling/profile-apps-from-command-line.md). Sie können die Befehlszeilentools mit dem CPU-Auslastungs- und dem .NET-Objektzuordnungstool verwenden.

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
