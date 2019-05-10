---
title: Diagnostizieren von UI-Erweiterung in Visual Studio verzögert | Microsoft-Dokumentation
ms.date: 01/26/2018
ms.topic: conceptual
author: PooyaZv
ms.author: pozandev
manager: jillfra
ms.workload: multiple
ms.openlocfilehash: 00266fd8fbc881707652247e08b093ca4b15a88d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912083"
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Vorgehensweise: Analysieren von Benutzeroberflächen-Verzögerungen durch Erweiterungen

Bei der Benutzeroberfläche nicht mehr reagiert, überprüft Visual Studio die Aufrufliste des UI-Threads, beginnt dabei auf der Blattebene und arbeitet sich zur Basis herunter. Wenn Visual Studio feststellt, dass ein Aufruf Stapelrahmen auf ein Modul gehört, die Teil einer installierten und aktivierten Erweiterung ist, wird eine Benachrichtigung angezeigt.

![Verzögerung der Benutzeroberfläche (einen Stillstand) Benachrichtigung](media/ui-delay-notification-in-vs.png)

Die Benachrichtigung informiert den Benutzer, dass die Verzögerung der Benutzeroberfläche (d. h., die eine nicht reagierende Benutzeroberfläche in der Benutzeroberfläche) für das Ergebnis des Codes von einer Erweiterung gegangen sein könnte. Darüber hinaus werden die Benutzer mit Optionen, um die Erweiterung oder zukünftige Benachrichtigungen für diese Erweiterung zu deaktivieren.

In diesem Dokument wird beschrieben, wie Sie diagnostizieren können, was zu Ihrem Erweiterungscode Benachrichtigungen zur UI Verzögerung verursacht.

> [!NOTE]
> Verwenden Sie nicht die experimentelle Instanz von Visual Studio, um Verzögerungen zu diagnostizieren. Einige Teile der Aufrufliste-Analyse für Benachrichtigungen zur UI Verzögerung erforderlich sind deaktiviert, wenn mit der experimentellen Instanz ein, was bedeutet, dass Benachrichtigungen zur UI Verzögerung nicht angezeigt werden können.

Eine Übersicht über den Diagnoseprozess lautet wie folgt aus:
1. Identifizieren Sie die Trigger-Szenario.
2. Starten Sie Visual Studio mit der Aktivität, die Protokollierung auf neu.
3. Starten Sie die ETW-Ablaufverfolgung.
4. Lösen Sie die Benachrichtigung erneut angezeigt werden.
5. ETW-Ablaufverfolgung zu beenden.
6. Überprüfen Sie das Aktivitätsprotokoll zum Abrufen der Verzögerung-ID.
7. Analysieren Sie die ETW-Ablaufverfolgung, die mit der Verzögerung-ID aus Schritt 6.

In den folgenden Abschnitten werden wir diese Schritte ausführlicher durchlaufen.

## <a name="identify-the-trigger-scenario"></a>Identifizieren Sie das Szenario für trigger

Um eine Verzögerung der Benutzeroberfläche zu diagnostizieren, müssen Sie zunächst zu identifizieren, welche (Sequenz von Aktionen) bewirkt, dass Visual Studio, um die Benachrichtigung angezeigt. Dies ist in der Reihenfolge für die Sie in der Lage sein, um die Benachrichtigung höher mit aktivierter Protokollierung auszulösen.

## <a name="restart-vs-with-activity-logging-on"></a>Starten Sie Visual Studio mit der Aktivität, die Protokollierung auf neu

Visual Studio kann ein "Aktivitätsprotokoll" generieren, die hilfreiche Informationen bereitstellt, wenn ein Problem debuggen. So schalten Sie die Aktivität, die Protokollierung in Visual Studio, öffnen Sie Visual Studio mit der `/log` -Befehlszeilenoption. Nach dem Start von Visual Studio wird das Aktivitätsprotokoll an folgendem Speicherort gespeichert:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Mehr darüber, wie Sie Ihre Visual Studio suchen können Instanz-ID finden Sie unter [Tools zum Erkennen und Verwalten von Visual Studio-Instanzen](../install/tools-for-managing-visual-studio-instances.md). Wir werden diese Aktivitätsprotokoll später benötigen, finden Sie weitere Informationen zu Verzögerungen und die zugehörigen Benachrichtigungen.

## <a name="starting-etw-tracing"></a>ETW-Ablaufverfolgung wird gestartet.

Sie können [PerfView](https://github.com/Microsoft/perfview/) zum Sammeln von ETW-Ablaufverfolgung. PerfView bietet eine einfache zu bedienende-Schnittstelle, für das Sammeln von ETW-Ablaufverfolgung und der Analyse. Verwenden Sie den folgenden Befehl aus, um eine Ablaufverfolgung sammeln:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Dadurch wird den Anbieter "Microsoft-VisualStudio", der den Anbieter, die, den Visual Studio für Ereignisse im Zusammenhang mit Verzögerung Benachrichtigungen zur UI verwendet. Es gibt auch das Schlüsselwort für den kernelanbieter, die PerfView, zum Generieren verwenden können der **Thread Zeit Stapel** anzeigen.

## <a name="trigger-the-notification-to-appear-again"></a>Lösen Sie die Benachrichtigung erneut angezeigt.

Nachdem PerfView Ablaufverfolgungssammlung gestartet wurde, können Sie die Trigger-aktionsabfolge (aus Schritt 1) für die Benachrichtigung, wieder angezeigt werden. Wenn die Benachrichtigung angezeigt wird, können Sie Ablaufverfolgungssammlung für PerfView zum Verarbeiten und generieren die Ausgabedatei der Ablaufverfolgung beenden.

## <a name="stop-etw-tracing"></a>Beenden Sie die ETW-Ablaufverfolgung

Zum Beenden der Sammlung von startablaufdaten verwenden Sie einfach die **Auflistung beenden** Schaltfläche im PerfView-Fenster. Wenn Ablaufverfolgungssammlung beendet wurde, kann PerfView automatisch die ETW-Ereignisse verarbeitet und generiert eine Ausgabedatei der Ablaufverfolgung.

## <a name="examine-the-activity-log-to-get-the-delay-id"></a>Überprüfen Sie das Aktivitätsprotokoll zum Abrufen der Verzögerung-ID

Wie bereits erwähnt, finden Sie das Aktivitätsprotokoll *%APPDATA%\Microsoft\VisualStudio\<Vs_instance_id > \ActivityLog.xml*. Jedes Mal, wenn eine Erweiterung Verzögerung der Benutzeroberfläche von Visual Studio erkannt wird, schreibt er einen Knoten, in das Aktivitätsprotokoll mit `UIDelayNotifications` als Quelle. Dieser Knoten enthält vier Arten von Informationen über die Verzögerung der Benutzeroberfläche:

- Die UI-Delay-ID, eine sequenzielle Zahl, die eine Verzögerung der Benutzeroberfläche in einem Visual Studio-Sitzung eindeutig identifiziert
- Die Sitzungs-ID, die Identifizierung von Visual Studio-Sitzung vom Anfang bis zum Schließen
- Unabhängig davon, ob eine Benachrichtigung für die Verzögerung der Benutzeroberfläche angezeigt wurde
- Die Erweiterung, die die Verzögerung der Benutzeroberfläche dadurch, dass verursacht

```xml
<entry>
  <record>271</record>
  <time>2018/02/03 12:02:52.867</time>
  <type>Information</type>
  <source>UIDelayNotifications</source>
  <description>A UI delay (Delay ID = 0) has been detected. (Session ID=16e49d4b-26c2-4247-ad1c-488edeb185e0; Blamed extension="UIDelayR2"; Notification shown? Yes.)</description>
</entry>
```

> [!NOTE]
> Nicht alle Benutzeroberflächen-Verzögerungen führen eine Benachrichtigung. Aus diesem Grund sollten Sie immer überprüfen die **Benachrichtigung angezeigt?** Wert den richtige Verzögerung der Benutzeroberfläche ordnungsgemäß zu identifizieren.

Nachdem Sie die richtige Verzögerung der Benutzeroberfläche im Aktivitätsprotokoll gefunden haben, notieren Sie die UI-Verzögerung-ID, die im Knoten angegeben. Die ID verwenden, suchen Sie nach der entsprechenden ETW-Ereignis im nächsten Schritt.

## <a name="analyze-the-etw-trace"></a>Analysieren der ETW-Ablaufverfolgungs

Öffnen Sie als Nächstes die Datei ein. Dazu können Sie mit der gleichen Instanz von PerfView oder durch eine neue Instanz starten und den aktuellen Ordnerpfad in der oberen linken Ecke des Fensters auf den Speicherort der Ablaufverfolgungsdatei festlegen.

![Festlegen des Ordnerpfads in Perfview](media/perfview-set-path.png)

Wählen Sie die Datei im linken Bereich und öffnen Sie es durch Auswahl **öffnen** aus dem Kontextmenü -Menü.

> [!NOTE]
> Standardmäßig gibt PerfView ein Zip-Archiv. Beim Öffnen *trace.zip*, wird automatisch das Archiv dekomprimiert und öffnet Sie die Ablaufverfolgung. Sie können diesen Schritt überspringen, wenn Sie deaktivieren die **Zip** Feld bei der Ablaufverfolgungssammlung. Aber wenn Sie beabsichtigen, übertragen und ablaufverfolgungen auf unterschiedlichen Computern verwenden, wird dringend empfohlen Deaktivieren der **Zip** Feld. Ohne diese Option die erforderlichen PDBs für Assemblys mit Ngen werden die Ablaufverfolgung nicht begleitet, und daher Symbole von Assemblys mit Ngen nicht auf dem Zielcomputer aufgelöst werden werden. (Finden Sie unter [in diesem Blogbeitrag](https://devblogs.microsoft.com/devops/creating-ngen-pdbs-for-profiling-reports/) für Weitere Informationen zu PDB-Dateien für Assemblys mit Ngen.)

Es dauert einige Minuten, bis PerfView zum Verarbeiten und die Ablaufverfolgung zu öffnen. Sobald die Ablaufverfolgung geöffnet ist, wird eine Liste der verschiedenen "Ansichten" darunter angezeigt.

![Zusammenfassungsansicht für PerfView-Ablaufverfolgung](media/perfview-summary-view-events-selected.png)

Wir verwenden zunächst das **Ereignisse** anzeigen, um den Zeitraum, der die Verzögerung der Benutzeroberfläche zu erhalten:

1. Öffnen der **Ereignisse** Ansicht wählen `Events` Knoten unter der Ablaufverfolgung auswählen und **öffnen** aus dem Kontextmenü -Menü.
2. Wählen Sie "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" im linken Bereich.
3. Drücken Sie die EINGABETASTE

Die Auswahl angewendet wird und alle `ExtensionUIUnresponsiveness` Ereignisse werden im rechten Bereich angezeigt.

![Auswählen von Ereignissen in der Ereignisansicht](media/perfview-event-selection.png)

Jede Zeile im rechten Bereich entspricht eine Verzögerung der Benutzeroberfläche. Das Ereignis enthält einen Verzögerung ID-Wert, der die ID der Verzögerung im Aktivitätsprotokoll aus Schritt 6 übereinstimmen sollte. Da `ExtensionUIUnresponsiveness` wird ausgelöst, am Ende der Verzögerung der Benutzeroberfläche, den Zeitstempel des Ereignisses (ungefähr) markiert die Endzeit der die Verzögerung der Benutzeroberfläche. Das Ereignis enthält auch die Dauer der Verzögerung. Wir können die Dauer von der Zeitstempel für das Ende den Zeitstempel des abgerufen, wenn die Verzögerung der Benutzeroberfläche gestartet, subtrahieren.

![Berechnen der Benutzeroberfläche verzögert Zeitraum](media/ui-delay-time-range.png)

Im vorherigen Screenshot ist beispielsweise der Zeitstempel des Ereignisses ist 12,125.679 und der Dauer der Verzögerung wird 6,143.085 (ms). Demnach sind
* Die Verzögerung Start ist 12,125.679-6,143.085 5,982.594 =.
* Der Zeitbereich der UI-Verzögerung ist 5,982.594 zu 12,125.679.

Sobald wir den Zeitbereich haben, können wir Schließen von der **Ereignisse** anzeigen und öffnen Sie die **Thread-Zeit (mit StartStop Aktivitäten) Stapel** anzeigen. Diese Ansicht ist besonders praktisch, da häufig Erweiterungen, die im UI-Thread blockieren lediglich auf andere Threads oder ein e/A Vorgang warten. Daher die **CPU-Stack** anzuzeigen, in der die Go-to-Option in den meisten Fällen ist, nicht die Zeit eines Threads blockiert benötigt, da es während dieser Zeit nicht die CPU verwendet erfasst werden kann. Die **Thread Zeit Stapel** löst dieses Problem durch ordnungsgemäß mit blockierten Zeit.

![Knoten des Threads (mit StartStop Aktivitäten)-Stapel in PerfView Ansicht "Zusammenfassung"](media/perfview-thread-time-with-startstop-activities-stacks.png)

Beim Öffnen **Thread Zeit Stapel** anzuzeigen, wählen Sie die **Devenv** Prozess zur Analyse zu starten.

![Thread Zeit Stapelansicht für die Analyse der Benutzeroberfläche verzögert](media/ui-delay-thread-time-stacks.png)

In der **Thread Zeit Stapel** anzeigen, in der oberen linken Ecke der Seite können Sie den Zeitraum, wir berechneten, Werte in den vorherigen Schritt, und drücken Sie **EINGABETASTE** , dass der Stapel zu diesem Zeitraum angepasst werden.

> [!NOTE]
> Bestimmen, welcher Thread der Benutzeroberfläche wird möglich (Start) Thread kontraintuitiv, wenn die Sammlung von startablaufdaten gestartet wird, nachdem Visual Studio bereits geöffnet ist. Die ersten Elemente auf dem Stapel des Benutzeroberflächenthreads (Start) sind jedoch häufig immer Operating System-DLLs (*ntdll.dll* und *"Kernel32.dll"*) gefolgt von `devenv!?` und dann `msenv!?` . Diese Sequenz können Sie den UI-Thread identifizieren.

 ![Identifiziert den Startupthread](media/ui-delay-startup-thread.png)

Sie können auch weitere in dieser Ansicht filtern, dazu nur Stapel, die Module aus dem Paket enthalten.

* Legen Sie **GroupPats** , leerer Text So entfernen Sie alle möglichen Gruppierungen, die standardmäßig hinzugefügt.
* Legen Sie **IncPats** Teil Ihres Assemblynamens "zusätzlich zum vorhandenen Prozessfilter einschließen. In diesem Fall wird **Devenv; UIDelayR2**.

![Festlegen von GroupPath und IncPath in Thread Zeit Stapelansicht](media/perfview-tts-group-path-inc-path.png)

PerfView enthält ausführliche Anleitungen unter dem **Hilfe** Menü, das Sie verwenden können, um Leistungsengpässe in Ihrem Code zu erkennen. Darüber hinaus enthalten die folgenden Links Weitere Informationen zum Verwenden von Visual Studio-threading-APIs, um Ihren Code zu optimieren:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

Sie können auch die neuen statischen Analysetools für Visual Studio für Erweiterungen (NuGet-Paket [hier](https://www.nuget.org/packages/microsoft.visualstudio.sdk.analyzers)), die Anleitungen zu bewährten Methoden zum Schreiben von effizienten Erweiterungen bereitstellen. Eine Liste der [VS-SDK-Analysetools](https://github.com/Microsoft/VSSDK-Analyzers/blob/master/doc/index.md) und [threading Analysen](https://github.com/Microsoft/vs-threading/blob/master/doc/analyzers/index.md).

> [!NOTE]
> Wenn Sie nicht auf eine nicht reagierende Benutzeroberfläche aufgrund der Abhängigkeiten der Adresse können Sie haben keine Kontrolle über (z. B., wenn die Erweiterung ist zum Aufrufen von synchronen Visual Studio-Diensten im UI-Thread), möchten wir davon erfahren. Wenn Sie Mitglied unserer Visual Studio-Partner-Programm sind, können Sie uns kontaktieren, durch die Übermittlung einer Supportanfrage für Entwickler. Andernfalls verwenden Sie das Tool "Problem melden", um Ihr Feedback übermitteln, und schließen `"Extension UI Delay Notifications"` im Titel. Nehmen Sie auch eine ausführliche Beschreibung der Analyse.
