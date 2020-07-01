---
title: Ausführen von Profilerstellungstools mit oder ohne Debugger | Microsoft-Dokumentation
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45632967c39348e8dc78dc3e2fb95227dcd86d7d
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285900"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Ausführen von Profilerstellungstools mit oder ohne Debugger

Visual Studio bietet eine Auswahl an Tools für Leistungsmessung und Profilerstellung. Einige Tools, wie z. B. „CPU-Auslastung“ und „Speicherauslastung“, können mit oder ohne Debugger und in den Release- oder Debugbuildkonfigurationen ausgeführt werden. Leistungs-Profiler-Tools wie „Anwendungszeitachse“ können in Debug- oder Releasebuilds ausgeführt werden. In den Debugger integrierte Tools wie das Fenster „Diagnosetools“ und die Registerkarte „Ereignisse“ können nur während Debugsitzungen ausgeführt werden.

>[!NOTE]
>Sie können die nicht in den Debugger integrierten Leistungstools unter Windows 7 und höher verwenden. Windows 8 oder höher ist erforderlich, um die in den Debugger integrierten Profilerstellungstools auszuführen.

Der nicht in den Debugger integrierte Leistungs-Profiler und die in den Debugger integrierten Diagnosetools bieten verschiedene Informationen und Funktionen. In den Debugger integrierte Tools zeigen Breakpoints und Variablenwerte an. Nicht in den Debugger integrierte Tools bieten Ihnen Ergebnisse, die sich näher an der Endbenutzeroberfläche befinden.

Berücksichtigen Sie bei der Entscheidung, welche Tools und Ergebnisse Sie nutzen möchten, Folgendes:

- Externe Leistungsprobleme, wie z.B. Datei-E/A oder die Reaktionszeit des Netzwerks, werden in den Debuggertools ähnlich angezeigt wie in den nicht in den Debugger integrierten Tools.
- Bei Problemen, die durch CPU-intensive Aufrufe ausgelöst werden, kann es möglicherweise zu erheblichen Leistungsunterschieden zwischen Release- und Debugbuilds kommen. Überprüfen Sie, ob das Problem in Releasebuilds vorhanden ist.
- Wenn das Problem nur bei Debugbuilds auftritt, ist es wahrscheinlich, dass Sie die nicht in den Debugger integrierten Tools nicht ausführen müssen. Bei Problemen mit Releasebuilds entscheiden Sie, ob die Debuggertools Ihnen bei weiteren Untersuchungen helfen können.
- Releasebuilds bieten Optimierungen wie Inlinefunktionsaufrufe und -konstanten, die ungenutzte Codepfade bereinigen und Variablen mit bestimmten Methoden speichern, sodass sie vom Debugger nicht genutzt werden können. Leistungsangaben der in den Debugger integrierten Tools sind weniger genau, da Debugbuilds diese Optimierungen fehlen.
- Der Debugger selbst ändert Leistungszeiten, während er erforderliche Debuggervorgänge durchführt, wie z. B. das Abfangen von Ausnahmen und Modulladeereignissen.
- Leistungsangaben zu Releasebuilds in den Leistungs-Profiler-Tools sind am präzisesten und genauesten. In den Debugger integrierte Toolergebnisse sind besonders nützlich, wenn es um den Vergleich mit anderen debuggingbezogenen Messungen geht.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Sammeln von Profilerstellungsdaten während des Debuggens

Wenn Sie mit dem Debuggen in Visual Studio beginnen, indem Sie **Debuggen** > **Debuggen starten** wählen oder **F5** drücken, wird das Fenster **Diagnosetools** standardmäßig angezeigt. Klicken Sie auf **Debuggen** > **Fenster** > **Diagnosetools anzeigen**, um dieses Fenster manuell zu öffnen. Das Fenster **Diagnosetools** enthält Informationen über Ereignisse, den Prozessarbeitsspeicher und die CPU-Auslastung.

![Screenshot des Fensters „Diagnosetools“](../profiling/media/diagnostictoolswindow.png "Fenster „Diagnosetools“")

- Klicken Sie auf das Symbol für **Einstellungen** in der Symbolleiste, um die **Arbeitsspeicherauslastung**, die **UI-Analyse**, und die **CPU-Auslastung** zu anzuzeigen.

- Wählen Sie **Einstellungen** in der Dropdownliste **Einstellungen** aus, um die **Eigenschaftenseiten der Diagnosetools** mit weiteren Optionen zu öffnen.

- Wenn Sie Visual Studio Enterprise ausführen, können Sie IntelliTrace unter **Extras** > **Optionen** > **IntelliTrace** aktivieren oder deaktivieren.

Die Diagnosesitzung endet, wenn Sie das Debugging beenden.

### <a name="the-events-tab"></a>Die Registerkarte „Ereignisse“

Während einer Debugsitzung werden die auftretenden Diagnoseereignisse im Fenster „Diagnosetools“ auf der Registerkarte „Ereignisse“ aufgelistet. Mit den Kategoriepräfixen *Haltepunkt*, *Datei* u. a. können Sie schnell die Liste nach einer Kategorie durchsuchen oder die Kategorien überspringen, die für Sie gerade nicht relevant sind.

Verwenden Sie in der Dropdownliste **Filter**, um Ereignisse anzuzeigen oder auszublenden, indem Sie bestimmte Ereigniskategorien auswählen oder abwählen.

![Screenshot des Filters „Diagnoseereignis“](../profiling/media/diagnosticeventfilter.png "Filtern von Diagnoseereignissen")

Verwenden Sie das Suchfeld, um eine bestimmte Zeichenfolge in der Ereignisliste zu suchen. Dies sind die Suchergebnisse für die Zeichenfolge *name*, die mit vier Ereignissen übereinstimmt:

![Screenshot der Suche „Diagnoseereignis“](../profiling/media/diagnosticseventsearch.png "Suchen nach Diagnoseereignissen")

Weitere Informationen finden Sie unter [Suchen und Filtern auf der Registerkarte "Ereignisse" im Fenster "Diagnosetools"](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Sammeln von Profilerstellungsdaten ohne das Debuggen

Sie können zum Erfassen von Leistungsdaten ohne Debuggen die Leistungs-Profiler-Tools ausführen.

1. Legen Sie mit einem in Visual Studio geöffneten Projekt die Konfiguration der Projektmappe auf  **Release** fest, und wählen Sie als Bereitstellungsziel  **Lokaler Windows-Debugger**  (oder  **Lokaler Computer**) aus.

1. Klicken Sie auf **Debuggen** > **Leistungs-Profiler**, oder drücken Sie **ALT**+**F2**.

1. Wählen Sie auf der Startseite der Diagnosetools mindestens ein Tools aus, das ausgeführt werden soll. Es werden nur die Tools gezeigt, die für den Projekttyp, das Betriebssystem und die Programmiersprache infrage kommen. Wählen Sie **Alle Tools anzeigen**, um auch Tools anzuzeigen, die für diese Diagnosesitzung deaktiviert sind.

   ![Screenshot der Diagnosetools](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Klicken Sie zum Starten der Diagnosesitzung auf **Start**.

   Während Sie die Sitzung ausführen, zeigen einige Tools auf der Seite der Diagnosetools Diagramme mit Echtzeitdaten sowie Steuerelemente zum Anhalten und Fortsetzen der Datensammlung.

    ![Screenshot der Datensammlung auf dem Leistungs- und Diagnosehub](../profiling/media/diaghubcollectdata.png "Sammeln von Daten im Hub")

1. Klicken Sie zum Beenden der Diagnosesitzung auf **Sammlung beenden**.

   Die analysierten Daten werden auf der Seite **Bericht** angezeigt.

Sie können die Berichte auch speichern und über die Liste der **zuletzt geöffneten Sitzungen** auf der Startseite der Diagnosetools öffnen.

![Screenshot der Liste der zuletzt geöffneten Sitzungen in den Diagnosetools](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>Sammeln von Profilerstellungsdaten über die Befehlszeile

Um Leistungsdaten über die Befehlszeile zu messen, können Sie das Tool „VSDiagnostics.exe“ verwenden, das entweder in Visual Studio oder den Remotetools enthalten ist. Es ist nützlich für die Erfassung von Leistungsüberwachungen auf Systemen, auf denen Visual Studio nicht installiert ist, oder für die Erstellung von Skripts für die Sammlung von Leistungsüberwachungen. Wenn Sie „VSDiagnostics.exe“ einsetzen, starten Sie eine Diagnosesitzung, die solange Profilerstellungsdaten aufnimmt und speichert, bis das Tool beendet wird. Anschließend werden diese Daten in eine Datei mit der Erweiterung „.diagsession“ exportiert, die Sie in Visual Studio öffnen können, um die Ergebnisse zu analysieren.

### <a name="launch-an-application"></a>Starten einer Anwendung

1. Öffnen Sie eine Eingabeaufforderung, und wechseln Sie zum Verzeichnis mit „VSDiagnostics.exe“:

   ```
   <Visual Studio Install Folder>\Team Tools\DiagnosticsHub\Collector\
   ```

2. Starten Sie „VSDiagnostics.exe“ mit dem den folgenden Befehl:

   ```
   VSDiagnostics.exe start <id> /launch:<appToLaunch> /loadConfig:<configFile>
   ```

   Sie müssen die folgenden Argumente einschließen:

   - \<id\>: Bestimmt die Sammlungssitzung. Die ID muss eine Zahl zwischen 1 und 255 sein.
   - \<appToLaunch\>: Die zu startende ausführbare Datei, für die ein Profil erstellt werden soll.
   - \<configFile\>: Die Konfigurationsdatei des Sammlungs-Agents, den Sie starten möchten.

3. Um die Sammlung zu beenden und Ihre Ergebnisse anzuzeigen, folgen Sie den Schritten im Abschnitt „Beenden der Sammlung“ weiter unten in diesem Artikel.

### <a name="attach-to-an-existing-application"></a>Anfügen an eine vorhandene Anwendung

1. Öffnen Sie eine Anwendung wie Editor, und öffnen Sie dann **Task-Manager**, um ihre Prozess-ID (PID) abzurufen. Im Task-Manager finden Sie die PID auf der Registerkarte  **Details** .
2. Öffnen Sie eine Eingabeaufforderung, und wechseln Sie zum Verzeichnis mit der ausführbaren Datei des Sammlungs-Agents. Das befindet sich in der Regel hier:

   ```
   <Visual Studio installation folder>\2019\Preview\Team Tools\DiagnosticsHub\Collector\
   ```

3. Starten Sie „VSDiagnostics.exe“, indem Sie den folgenden Befehl eingeben.

   ```
   VSDiagnostics.exe start <id> /attach:<pid> /loadConfig:<configFile>
   ```

   Sie müssen die folgenden Argumente einschließen:

   - \<id\>: Bestimmt die Sammlungssitzung. Die ID muss eine Zahl zwischen 1 und 255 sein.
   - \<pid\>: Die PID des Prozesses, den Sie profilen möchten. Hier also die PID, die Sie in Schritt 1 abgerufen haben.
   - \<configFile\>: Die Konfigurationsdatei des Sammlungs-Agents, den Sie starten möchten. Weitere Informationen finden Sie unter  [Konfigurationsdateien für Agents](../profiling/profile-apps-from-command-line.md).

4. Um die Sammlung zu beenden und Ihre Ergebnisse anzuzeigen, folgen Sie den Schritten im nächsten Abschnitt.

### <a name="stop-collection"></a>Beenden der Sammlung

1. Beenden Sie die Sammlungssitzung, und übertragen Sie die Ausgabe mit dem folgenden Befehl in eine Datei.

   ```
   VSDiagnostics.exe stop <id> /output:<path to file>
   ```

2. Wechseln Sie zur Dateiausgabe des vorherigen Befehls, und öffnen Sie sie in Visual Studio, um die gesammelten Informationen zu untersuchen.

## <a name="agent-configuration-files"></a>Agent-Konfigurationsdateien

Sammlungs-Agents sind austauschbare Komponenten, die verschiedene Datentypen sammeln, je nachdem, was gemessen werden soll.
Der Bequemlichkeit halber können Sie diese Informationen in einer Agent-Konfigurationsdatei speichern. Die Konfigurationsdatei ist eine JSON-Datei, die mindestens den Namen der DLL-Datei und deren COM-CLSID enthält. Hier sehen Sie die Beispielkonfigurationsdateien, die Sie im folgenden Ordner finden können:

```
<Visual Studio installation folder>\Team Tools\DiagnosticsHub\Collector\AgentConfigs\
```

Unter den folgenden Links können Sie die Konfigurationsdateien für den Agent herunterladen und anzeigen:

- https://aka.ms/vs/diaghub/agentconfig/cpubase
- https://aka.ms/vs/diaghub/agentconfig/cpuhigh
- https://aka.ms/vs/diaghub/agentconfig/cpulow
- https://aka.ms/vs/diaghub/agentconfig/database
- https://aka.ms/vs/diaghub/agentconfig/dotnetasyncbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetallocbase
- https://aka.ms/vs/diaghub/agentconfig/dotnetalloclow

Konfigurationen für die CPU-Nutzung (CpuUsage) (Standard/Hoch/Niedrig). entsprechen den Daten, die für das Profilerstellungstool für die  [CPU-Auslastung](../profiling/cpu-usage.md) gesammelt wurden.
DotNetObjectAlloc-Konfigurationen (Standard/Niedrig) entsprechen den Daten, die für das  [.NET-Objektzuteilungstool](../profiling/dotnet-alloc-tool.md) gesammelt wurden.

Die Konfigurationen „Standard“, „Niedrig“ und „Hoch“ beziehen sich auf die Stichprobenentnahmerate. So bedeutet „Niedrig“ z.B. 100 Stichproben pro Sekunde, und „Hoch“ 4000 Stichproben pro Sekunde.
Damit das Tool „VSDiagnostics.exe“ mit einem Sammlungs-Agent zusammenarbeitet, werden für den entsprechenden Agent sowohl eine DLL als auch eine COM-CLSID benötigt. Für den Agent gibt es möglicherweise auch zusätzliche Konfigurationsoptionen. Wenn Sie einen Agent ohne Konfigurationsdatei verwenden, verwenden Sie das Format im folgenden Befehl:

```
VSDiagnostics.exe start <id> /attach:<pid> /loadAgent:<agentCLSID>;<agentName>[;<config>]
```
