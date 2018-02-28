---
title: "Diagnostizieren von UI-Erweiterung in Visual Studio verzögert | Microsoft Docs"
ms.custom: 
ms.date: 01/26/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
author: PooyaZv
ms.author: pozandev
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9dede2f30a9d91e94bda3183deaae337e4c556dc
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2018
---
# <a name="how-to-diagnose-ui-delays-caused-by-extensions"></a>Vorgehensweise: Analysieren der UI Verzögerungen aufgrund von Erweiterungen

Wenn UI nicht mehr reagiert, überprüft Visual Studio die Aufrufliste des UI-Threads an, beginnend mit der Blattebene und arbeiten auf der Basis. Wenn Visual Studio feststellt, dass ein Aufruf Stapelrahmen auf ein Modul gehört, die Teil einer Erweiterung installiert und aktiviert ist, wird eine Benachrichtigung angezeigt.

![UI-Verzögerung (nicht reagierenden) Benachrichtigung](media/ui-delay-notification-in-vs.png)

Die Benachrichtigung informiert den Benutzer, dass die Benutzeroberfläche Verzögerung (d. h. die nicht reagierenden in der Benutzeroberfläche), das Ergebnis des Codes von einer Erweiterung gegangen sein könnte. Darüber hinaus den Benutzer mit der Erweiterung oder zukünftige Benachrichtigungen für diese Erweiterung zu deaktivieren.

Dieses Dokument beschreibt, wie Sie diagnostizieren können, was im Code Benutzeroberfläche verzögert Benachrichtigungen verursacht. 

> [!NOTE]
> Verwenden Sie nicht die experimentelle Instanz von Visual Studio UI Verzögerungen zu diagnostizieren. Bei Verwendung die experimentelle Instanz, was bedeutet, dass UI Verzögerung Benachrichtigungen möglicherweise nicht angezeigt werden, sind einige Teile der Aufrufliste Analyse für UI Verzögerung Benachrichtigungen erforderlich sind deaktiviert.

Eine Übersicht über die Diagnose Prozess sieht folgendermaßen aus:
1. Identifizieren Sie die Trigger-Szenario.
2. Starten Sie mit der Aktivität, die Protokollierung auf VS neu.
3. ETW-Ablaufverfolgung starten.
4. Lösen Sie die Benachrichtigung erneut angezeigt werden.
5. ETW-Ablaufverfolgung zu beenden.
6. Überprüfen Sie das Aktivitätsprotokoll Abrufen der Verzögerung-ID.
7. Analysieren Sie die ETW-Ablaufverfolgung, die mit Verzögerung-ID aus Schritt 6.

In den folgenden Abschnitten werden wir diese Schritte ausführlicher durchlaufen.

## <a name="identifying-the-trigger-scenario"></a>Identifizieren die Trigger-Szenario

Eine Verzögerung für die Benutzeroberfläche für die Diagnose, müssen Sie zunächst Idetify welche (Sequenz von Aktionen) bewirkt, dass Visual Studio, um die Benachrichtigung anzeigen. Dies ist in der Reihenfolge für die Sie in der Lage sein, um die Benachrichtigung höher mit aktivierter Protokollierung ausgelöst.

## <a name="restarting-vs-with-activity-logging-on"></a>Neustarten von VS mit Aktivität anmelden

Visual Studio kann ein "Aktivitätsprotokoll" generieren, die hilfreiche Informationen bereitstellt, wenn ein Problem debuggen. Um die Aktivität, die in Visual Studio-Protokollierung zu aktivieren, starten Sie Visual Studio mit der `/log` -Befehlszeilenoption. Nach dem Start von Visual Studio wird das Aktivitätsprotokoll in folgendem Verzeichnis gespeichert:

```DOS
%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml
```

Erfahren Sie, wie Sie Ihre VS erhalten Instanz-ID finden Sie unter [Tools zur Erkennung und Verwaltung von Visual Studio-Instanzen](../install/tools-for-managing-visual-studio-instances.md). Wir werden diese Aktivitätsprotokoll später verwenden, um weitere Informationen zu Verzögerungen bei der Benutzeroberfläche und verwandte Benachrichtigungen erhalten.

## <a name="starting-etw-tracing"></a>Starten Sie die ETW-Ablaufverfolgung

Sie können [PerfView](https://github.com/Microsoft/perfview/) eine ETW-Ablaufverfolgung sammeln. PerfView stellt eine einfach zu verwendende Schnittstelle für eine ETW-Ablaufverfolgung gesammelt und analysiert, bereit. Verwenden Sie den folgenden Befehl aus, um eine Ablaufverfolgung sammeln:

```DOS
Perfview.exe collect C:\trace.etl /BufferSizeMB=1024 -CircularMB:2048 -Merge:true -Providers:*Microsoft-VisualStudio:@StacksEnabled=true -NoV2Rundown /kernelEvents=default+FileIOInit+ContextSwitch+Dispatcher
```

Dadurch wird die "Microsoft Visual Studio" Anbieter, der den Anbieter, den Visual Studio für Ereignisse im Zusammenhang mit der Benutzeroberfläche verzögert Benachrichtigungen verwendet. Es gibt auch das Schlüsselwort für den Kernel-Anbieter, den PerfView zum Generieren der Ansicht "Threads Zeit Stapel" verwenden können.

## <a name="triggering-the-notification-to-appear-again"></a>Auslösen der benachrichtigungs erneut angezeigt.

Nachdem PerfView Trace Auflistung gestartet wurde, können Sie die Trigger aktionsabfolge (aus Schritt 1) für die Benachrichtigung, erneut angezeigt werden. Sobald die Benachrichtigung angezeigt wird, können Sie Trace-Auflistung für PerfView zu verarbeiten und generieren die Datei für die Ablaufverfolgungsausgabe beenden.

## <a name="stopping-etw-tracing"></a>ETW-Ablaufverfolgung beenden

Verwenden Sie zum Beenden der Ablaufverfolgung Sammlung einfach die `Stop collection` -Fenster auf die Schaltfläche PerfView. Nach dem Beenden der Ablaufverfolgung-Sammlung wird PerfView verarbeitet automatisch die ETW-Ereignisse und generiert eine Ausgabedatei der Ablaufverfolgung.

## <a name="examining-the-activity-log-to-get-the-delay-id"></a>Untersuchen das Aktivitätsprotokoll zum Abrufen der Verzögerung-ID

Wie bereits erwähnt, können Sie das Aktivitätsprotokoll auf finden `%APPDATA%\Microsoft\VisualStudio\<vs_instance_id>\ActivityLog.xml`. Jedes Mal, wenn Visual Studio eine Erweiterung UI Verzögerung entdeckt, schreibt er einen Knoten in das Aktivitätsprotokoll mit `UIDelayNotifications` als Quelle. In diesem Knoten sind vier Arten von Informationen über die Benutzeroberfläche Verzögerung:

- Die Benutzeroberfläche Verzögerung-ID eine laufende Nummer, die eine Verzögerung UI in einer VS-Sitzung eindeutig.
- Die Sitzungs-ID, die Visual Studio-Sitzung von Anfang bis zum Schließen eindeutig identifiziert
- Und zwar unabhängig davon, ob eine Benachrichtigung angezeigt wurde, für die UI-Verzögerung
- Die Erweiterung, die die Benutzeroberfläche wahrscheinlich Verzögerung

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
> Nicht alle Benutzeroberflächen-Verzögerungen führen eine Benachrichtigung. Aus diesem Grund sollten Sie immer die "Benachrichtigung angezeigt?" Überprüfen Wert, der die richtige UI-Verzögerung, ordnungsgemäß identifizieren.

Wenn Sie die richtige UI Verzögerung im Aktivitätsprotokoll gefunden haben, notieren Sie sich die Benutzeroberfläche Verzögerung-ID, die im Knoten angegeben. Verwenden Sie die ID für das entsprechende ETW-Ereignis im nächsten Schritt gesucht werden soll.

## <a name="analyzing-the-etw-trace"></a>Analysieren der ETW-Ablaufverfolgungs

Als Nächstes öffnen Sie die Ablaufverfolgungsdatei an. Hierzu können Sie entweder mithilfe der gleichen Instanz von PerfView oder um eine neue Instanz starten und den aktuellen Ordnerpfad in der oberen linken Ecke des Fensters auf den Speicherort der Ablaufverfolgungsdatei festlegen.

![Den Ordnerpfad festlegen in Perfview](media/perfview-set-path.png)

Wählen Sie im linken Bereich der Ablaufverfolgungsdatei und öffnen Sie, indem Sie mit der rechten Maustaste oder Kontext Menü öffnen auswählen.

> [!NOTE]
> Standardmäßig gibt PerfView aus einem Zip-Archiv. Wenn Sie trace.zip öffnen, werden automatisch Archiv dekomprimiert und öffnet die Ablaufverfolgung. Sie können diesen Schritt überspringen, deaktivieren Sie das Kontrollkästchen "Zip" während der Trace-Auflistung. Jedoch wenn Sie beabsichtigen, übertragen und ablaufverfolgungen auf verschiedenen Computern verwenden, empfehlen wir für das Kontrollkästchen "Zip". Ohne diese Option die erforderlichen PDBs für Ngen-Assemblys werden nicht die Ablaufverfolgung begleitet, und daher Symbole von Ngen-Assemblys nicht auf dem Zielcomputer behoben werden werden. (Siehe [diesem Blogbeitrag](https://blogs.msdn.microsoft.com/devops/2012/12/10/creating-ngen-pdbs-for-profiling-reports/) für Weitere Informationen zu PDB-Dateien für Ngen-Assemblys.) 

Es kann mehrere Minuten dauern PerfView zu verarbeiten, und öffnen Sie die Ablaufverfolgung. Sobald die Ablaufverfolgung geöffnet ist, wird eine Liste der verschiedenen "Ansichten" darunter angezeigt.

![PerfView Trace Zusammenfassungsansicht](media/perfview-summary-view-events-selected.png)

Wir verwenden die Ansicht "Ereignisse" zuerst, um dem Zeitraum, der die Verzögerung für die Benutzeroberfläche zu erhalten:

1. Öffnen Sie die Ansicht "Ereignisse" vom Knoten "Ereignisse" die Ablaufverfolgung auswählen und Öffnen von der mit der rechten Maustaste oder im Kontextmenü aus.
2. Wählen Sie "`Microsoft-VisualStudio/ExtensionUIUnresponsiveness`" im linken Bereich.
3. Drücken Sie die EINGABETASTE

Die Auswahl wird angewendet, und alle `ExtensionUIUnresponsiveness` Ereignisse werden im rechten Bereich angezeigt.

![Ereignisse in der Ansicht "Ereignisse" auswählen](media/perfview-event-selection.png)

Jede Zeile im rechten Bereich werden zu einer Verzögerung der Benutzeroberfläche entspricht. Das Ereignis enthält einen "ID" Verzögerung "-Wert, der die ID der Verzögerung im Aktivitätsprotokoll aus Schritt 6 entsprechen soll. Da `ExtensionUIUnresponsiveness` ausgelöst wird am Ende der UI-Verzögerung, den Zeitstempel des Ereignisses (ungefähr) markiert die Endzeit der Benutzeroberfläche Verzögerung. Das Ereignis enthält auch die Dauer der Verzögerung. Wir können die Dauer von der Zeitstempel für das Ende den Zeitstempel der abrufen, wenn die UI-Verzögerung gestartet subtrahieren.

![Berechnen den UI-Verzögerung-Zeitraum](media/ui-delay-time-range.png)

In der vorherigen Abbildung beispielsweise der Zeitstempel des Ereignisses ist 12,125.679 und die Dauer der Verzögerung wird 6,143.085 (ms). Demnach sind
* Verzögerung befindet sich 12,125.679 6,143.085 = 5,982.594.
* Der Zeitraum der UI-Verzögerung ist 5,982.594 auf 12,125.679.

Nachdem wir den Zeitbereich haben, können wir die Ansicht "Ereignisse" schließen und öffnen Sie die Ansicht "Threadstapel (mit StartStop Aktivitäten)". In dieser Ansicht ist besonders hilfreich, da häufig Erweiterungen, die im UI-Thread blockieren lediglich auf andere Threads oder eines e/A-gebundene Vorgangs warten. Daher kann die Ansicht "CPU-Stapel" die Option "Gehe zu" in den meisten Fällen ist, nicht die Zeit erfasst werden aufwenden der Thread blockiert, da es nicht die CPU-Nutzung während dieser Zeit verwendet wird. Der "Thread Zeit Stapel" löst dieses Problem durch ordnungsgemäß mit blockiert Zeit.

![Thread-Stapel (mit StartStop Aktivitäten) Knoten in PerfView Zusammenfassungsansicht](media/perfview-thread-time-with-startstop-activities-stacks.png)

Beim Öffnen von "Thread Zeit Stapel" anzuzeigen Sie, wählen Sie "Devenv"-Prozess, um die Analyse zu starten.

![Zeit Stapelansicht Analysezwecken Verzögerung UI-Thread](media/ui-delay-thread-time-stacks.png)

In der Ansicht "Threads Zeit Stapel" kann in der oberen linken Ecke der Seite des Zeitraums auf die Werte festlegen, die wir in den vorherigen Schritt, und drücken Sie die EINGABETASTE berechnet, dass der Stapel auf diesem Zeitraum angepasst werden.

> [!NOTE]
> Bestimmen, welcher Thread der Benutzeroberfläche wird kann (Start)-Thread nicht intuitiv, wenn die Trace-Auflistung gestartet wird, nachdem Sie Visual Studio bereits geöffnet ist. Allerdings sind die ersten Elemente im Stapel des Threads UI (Start) den wahrscheinlichsten immer Betriebssystem DLLs ("ntdll.dll" und "kernel32.dll") gefolgt von Devenv! und klicken Sie dann Msenv!. Diese Sequenz kann dabei helfen, die im UI-Thread zu identifizieren.

 ![Identifizieren des starten-Threads](media/ui-delay-startup-thread.png)

Zudem den in dieser Ansicht zu filtern, z. B. nur die Stapel, die Module, aus dem Paket enthalten.

* Legen Sie "GroupPats" auf leerer Text So entfernen Sie alle Gruppierung standardmäßig hinzugefügt.
* Gruppe "IncPats", um einen Teil der Name der Assembly zusätzlich zu den vorhandenen Prozessfilter enthalten. In diesem Fall sollten sie "Devenv; sein. UIDelayR2 ".

![Festlegen von GroupPath und IncPath in Thread Zeit Stapelansicht](media/perfview-tts-group-path-inc-path.png)

PerfView detaillierte Anleitung im Menü "Hilfe", die Sie zum Identifizieren von Leistungsengpässen im Code verwenden können. Darüber hinaus enthalten die folgenden Links Weitere Informationen zum Verwenden von Visual Studio-threading-APIs verwendet, um den Code optimieren:

* [https://aka.ms/vsthreading](https://aka.ms/vsthreading)
* [https://aka.ms/vsthreadingcookbook](https://aka.ms/vsthreadingcookbook)

