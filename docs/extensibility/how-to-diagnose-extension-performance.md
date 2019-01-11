---
title: 'Vorgehensweise: Leistung der diagnoseerweiterung | Microsoft-Dokumentation'
ms.date: 11/08/2016
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: douge
ms.workload:
- bertaygu
ms.openlocfilehash: fd51728f5e57af1017cb4b280f9ffc9d1c50df98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943420"
---
# <a name="measuring-extension-impact-in-startup"></a>Messen der Auswirkungen der Erweiterung in der Startdatei

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Konzentrieren Sie sich auf die erweiterungsleistung in Visual Studio 2017

Basierend auf Kundenfeedback, war einer der Bereiche den Fokus für Visual Studio 2017 Version Leistung beim Start und -Lösung laden. Wie im Visual Studio-Platform-Team haben unsere Arbeit an der Verbesserung der Leistung beim Start und -Lösung laden. Im Allgemeinen sollten unsere Messungen installierte Erweiterungen auch einen erheblichen Einfluss auf die Szenarios haben können.

Damit können Benutzer diese Auswirkungen zu verstehen, haben wir ein neues Feature in Visual Studio zum Benachrichtigen von Benutzern langsamer Erweiterungen hinzugefügt. In einigen Fällen erkennt Visual Studio eine neue Erweiterung, die entweder-Ladevorgang für Projektmappen oder beim Start verlangsamt. Wenn zu eine Verlangsamung Ihrer erkannt wird, wird Benutzern eine Benachrichtigung in der IDE auf neuen "Visual Studio-Leistung verwalten"-Dialogfeld angezeigt. Dieses Dialogfeld kann auch immer vom Menü "Hilfe", um zuvor erkannten Extensions durchsuchen zugegriffen werden.

![Visual Studio-Leistung verwalten](media/manage-performance.png)

Dieses Dokument soll ermöglicht es erweiterungsentwicklern, von beschreiben, wie die Erweiterung Auswirkungen berechnet wird. Dieses Dokument beschreibt auch, wie die Erweiterung Auswirkungen lokal analysiert werden kann. Lokal Analysieren der Auswirkungen auf die Erweiterung wird bestimmt, ob eine Erweiterung als eine Leistung, die Auswirkungen auf die Erweiterung angezeigt werden kann.

> [!NOTE]
> Dieses Dokument konzentriert sich auf die Auswirkungen von Erweiterungen beim Starten und die Projektmappe laden. Erweiterungen haben ebenfalls Auswirkungen auf Visual Studio-Leistung, wenn sie dazu führen, die Benutzeroberfläche dass reagiert. Weitere Informationen zu diesem Thema finden Sie unter [Vorgehensweise: Analysieren von Benutzeroberflächen Verzögerungen durch Erweiterungen](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Erweiterungen können wie Start auswirken.

Eine der am häufigsten verwendeten Methoden für Erweiterungen für die startleistung auswirken wird durch automatisches Laden eines bekannten Start-Benutzeroberflächen-Kontexten wie z. B. NoSolutionExists oder ShellInitialized auswählen. Diese Benutzeroberfläche-Kontexte erhalten während des Starts aktiviert. Alle enthaltenen Pakete die `ProvideAutoLoad` -Attribut in ihrer Definition mit diesen Kontexten geladen und initialisiert Sie zu diesem Zeitpunkt.

Wenn wir die Auswirkungen einer Erweiterung messen, konzentrieren wir uns in erster Linie auf die Zeit, diese Erweiterungen, die automatisch geladen, in den oben genannten Kontexten auswählen. Gemessen Mal enthalten würde, aber nicht darauf beschränkt:

* Laden von Assemblys für die Erweiterung für synchrone Pakete
* In den Konstruktor der Paket-Klasse für synchrone Pakete verbrachte Zeit
* Paketmethode initialisieren (oder SetSite) für synchrone Pakete verbrachte Zeit
* Führen für asynchrone-Pakete die oben genannten Vorgänge Hintergrundthread.  Daher werden die Vorgänge von der Überwachung ausgeschlossen.
* Zeit im irgendwelche asynchronen Vorgänge, die während der Initialisierung des Pakets im Hauptthread die Ausführung geplant
* In den Ereignishandlern, insbesondere die Shell initialisiert Kontext-Aktivierung oder die Shell Zombie-statusänderung verbrachte Zeit
* Ab Visual Studio 2017 Update 3 wird außerdem beginnen wir Zeitspanne im für aufrufen im Leerlauf aufgewendet wird, bevor die Shell initialisiert wurde. Lange Operationen in den Leerlauf Handler auch dazu führen, dass nicht mehr reagiert IDE und tragen zu einer vom Benutzer wahrgenommene Startzeit.

Wir haben viele Features, die beginnend mit Visual Studio 2015 hinzugefügt. Diese Funktionen können mit müssen Sie die Pakete automatisch geladen. Die Features verschieben auch die Notwendigkeit von Paketen zum Laden in spezifischere Fällen. Zu diesen Szenarien gehören Beispiele, wo Benutzer mehr bestimmte verwenden Sie die Erweiterung, oder eine Erweiterung-Auswirkungen zu reduzieren wären, wenn automatisch geladen.

Weitere Informationen zu diesen Funktionen finden Sie in den folgenden Dokumenten:

[Regel-basierte Benutzeroberfläche-Kontexte](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): Eine umfangreichere regelbasierte Engine benutzeroberflächenkontexte so konzipiert, können Sie benutzerdefinierte Kontexte, die basierend auf Projekttypen, Typen und Attribute erstellen. Benutzerdefinierte Kontexte können verwendet werden, ein Paket während der spezifischere Szenarios zu laden. Diesen speziellen Szenarien umfassen das Vorhandensein eines Projekts mit einer bestimmten Funktion starten. Können Sie auch benutzerdefinierte Kontexten [Befehl Sichtbarkeit für einen benutzerdefinierten Kontext gebunden werden](visibilityconstraints-element.md) basierend auf Projektkomponenten oder andere Bedingungen verfügbaren. Diese entfällt die Notwendigkeit zum Laden eines Pakets, um die Abfrage einen Befehlshandler-Status zu registrieren.

[Unterstützung für asynchrone Bereitstellungspaket](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): Die neue Asyncpackage-Basisklasse in Visual Studio 2015 ermöglicht Visual Studio-Pakete, wenn das Laden des Pakets von einer Auto-Load-Attribut oder ein Dienst für die asynchrone Abfrage angefordert wurde asynchron im Hintergrund geladen. Diese laden im Hintergrund kann die IDE reaktionsfähig bleiben. Die IDE reagiert auch, wenn die Erweiterung im Hintergrund initialisiert wird und kritische Szenarien wie starten und -Lösung laden wäre nicht beeinträchtigt werden.

[Asynchrone Dienste](how-to-provide-an-asynchronous-visual-studio-service.md): Durch die Unterstützung asynchroner Pakets haben wir auch Unterstützung für Abfragen von Diensten asynchron und asynchrone Dienste registrieren wird hinzugefügt. Darüber hinaus arbeiten wir zum Konvertieren von Visual Studio-Basisdienste, um asynchrone Abfrage unterstützt, sodass der Großteil der Arbeit in einer Async-Abfrage in Hintergrundthreads auftritt. SComponentModel (Visual Studio MEF-Host) ist eine der wichtigsten Dienste, die unterstützt jetzt die asynchrone Abfrage von Erweiterungen zur Unterstützung asynchronen Laden vollständig zu ermöglichen.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reduzieren der Auswirkungen von "Auto" Erweiterungen geladen

Wenn ein Paket weiterhin automatisch beim Start geladen werden muss, ist es wichtig, um die Arbeit, die während der Initialisierung des Pakets zu minimieren. Minimieren der Initialisierungsarbeit Pakets verringert die Wahrscheinlichkeit, dass die Erweiterung beim Start beeinträchtigen.

Sind einige Beispiele, die Paket-Initialisierung teuer verursachen könnte:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Verwendung von synchronen Paket Last anstelle der das Laden des asynchroner Pakets

Da auf dem Hauptthread synchron Pakete standardmäßig geladen werden, empfehlen wir die Erweiterung-Besitzer, die automatisch geladen Pakete verwenden die Basisklasse asynchroner Pakets stattdessen, wie bereits erwähnt haben. Ändern eines Pakets automatisch geladen, um das asynchrone Laden zu unterstützen wird auch die anderen Probleme, die folgenden lösen erleichtern.

### <a name="synchronous-filenetwork-io-requests"></a>Synchrone Datei/Netzwerk-e/a-Anforderungen

Im Idealfall sollten alle synchronen e/a-Anforderungen von Datei- oder Netzwerkvorgänge im Hauptthread vermieden werden. Ihre Auswirkungen werden, hängt davon ab, Zustand des Computers und kann für längere Zeit in einigen Fällen blockiert.

Verwenden asynchroner Pakets laden und asynchrone e/a-APIs sollten sicherstellen, dass die Initialisierung des Pakets den Hauptthread in solchen Fällen nicht blockiert. Benutzer können auch weiterhin mit Visual Studio zu interagieren, während der e/a-Anforderungen im Hintergrund ausgeführt.

### <a name="early-initialization-of-services-components"></a>Frühe Initialisierung der Services, Komponenten

Eine allgemeine Muster im Paket-Initialisierung ist zum Initialisieren der Dienste, die von verwendet und bereitgestellt werden, indem Sie das Paket in das Paket `constructor` oder `initialize` Methode. Während dadurch wird, dass die Dienste für die sichergestellt Verwendung bereit sind, können sie auch hinzufügen unnötige Kosten, wenn Sie ein Paket geladen wird, wenn diese Dienste nicht sofort verwendet werden. Stattdessen sollten solche Dienste bei Bedarf, um die Arbeit, die im Paket-Initialisierung zu minimieren initialisiert werden.

Für globale Dienste, die von einem Paket bereitgestellt werden, können Sie `AddService` Methoden, die eine Funktion des Diensts verzögert initialisiert wird, nur, wenn sie von einer Komponente angefordert werden. Für Dienste, die innerhalb des Pakets verwendet werden, können Sie verzögert<T> oder AsyncLazy<T> um sicherzustellen, dass Dienste bei der ersten Verwendung initialisiert/abgefragt werden.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Messen der Auswirkungen von "Auto" Erweiterungen mit Aktivitätsprotokoll geladen

Ab Visual Studio 2017 Update 3 können enthält Visual Studio-Aktivitätsprotokoll jetzt Einträge für die Auswirkungen auf die Leistung von Paketen beim Laden von Start- und die Lösung. Um diese Messungen angezeigt wird, müssen Sie Visual Studio starten, mit dem/Log-Schalter, und öffnen Sie *ActivityLog.xml* Datei.

Im Aktivitätsprotokoll aufgeführt die Einträge werden unter "Visual Studio-Leistung verwalten"-Quelle, und sieht wie im folgenden Beispiel:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Dieses Beispiel zeigt, in ein Paket mit der GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" 2008 ms beim Start von Visual Studio hat. Beachten Sie, dass Visual Studio der obersten Ebene Kosten als primäre Telefonnummer, beim Berechnen der Auswirkungen eines Pakets berücksichtigt, wie dies, dass die einsparungen-Benutzern angezeigt wäre, wenn sie die Erweiterung für das Paket zu deaktivieren.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Messen der Auswirkungen von "Auto" Erweiterungen unter Verwendung von PerfView geladen

Während der Codeanalyse kann Codepfade zu identifizieren, die Initialisierung des Pakets verlangsamen können, können Sie auch Ablaufverfolgung verwenden, mit, dass Anwendungen wie PerfView um die Auswirkungen einer Laden des Pakets in der Start von Visual Studio zu verstehen.

PerfView ist ein Ablaufverfolgungstool, eine systemweite. Dieses Tool wird Ihnen ein Verständnis Langsamster Pfade in einer Anwendung, entweder aufgrund von CPU-Auslastung oder Systemaufrufe zum Blockieren. Im folgenden finden Sie ein kurzes Beispiel analysiert eine beispielerweiterung, die PerfView unter Verwendung der [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Beispielcode:**

Dieses Beispiel basiert auf dem Beispiel folgenden Code zum Anzeigen vorgesehen ist Fall einige häufige Ursachen für die Verzögerung:

```csharp
protected override void Initialize()
{
    // Initialize a class from another assembly as an example
    MakeVsSlowServiceImpl service = new MakeVsSlowServiceImpl();

    // Costly work in main thread involving file IO
    string systemPath = Environment.GetFolderPath(Environment.SpecialFolder.Windows);
    foreach (string file in Directory.GetFiles(systemPath))
    {
        DateTime creationDate = File.GetCreationTime(file);
    }

    // Costly work after shell is initialized. This callback executes on main thread
    KnownUIContexts.ShellInitializedContext.WhenActivated(() =>
    {
        DoMoreWork();
    });

    // Start async work on background thread
    DoAsyncWork().Forget();
}

private async Task DoAsyncWork()
{
    // Switch to background thread to do expensive work
    await TaskScheduler.Default;
    System.Threading.Thread.Sleep(500);
}

private void DoMoreWork()
{
    // Costly work
    System.Threading.Thread.Sleep(500);
    // Blocking call to an asynchronous work.
    ThreadHelper.JoinableTaskFactory.Run(async () => { await DoAsyncWork(); });
}
```

**Aufzeichnen einer Ablaufverfolgungs mit PerfView:**

Nachdem Sie mit der Erweiterung installiert der Visual Studio-Umgebung eingerichtet haben, können Sie eine Ablaufverfolgung starten aufzeichnen, indem PerfView öffnen und die **sammeln** Dialogfeld aus der **sammeln** Menü.

![Perfview Menü "erfassen"](media/perfview-collect-menu.png)

Stellt die Standardoptionen Aufruflisten für CPU-Auslastung, doch da Blockierungszeit auch interessiert sind, Sie sollten aktivieren **Thread Zeit** Stapel. Sobald die Einstellungen bereit sind. Klicken Sie auf **Sammlung starten** und starten Sie Visual Studio nach der Aufzeichnung gestartet wird.

Bevor Sie die Datenerfassung beenden, um sicherzustellen, dass Visual Studio vollständig initialisiert, das Hauptfenster vollständig sichtbar ist und wenn die Erweiterung auf alle Teile der Benutzeroberfläche, die automatisch angezeigt verfügt, sind auch angezeigt werden soll. Sobald Visual Studio vollständig geladen ist, und die Erweiterung initialisiert wird, können Sie beenden, zum Analysieren der Ablaufverfolgungs aufgezeichnet.

**Analysieren eine Ablaufverfolgung mit PerfView:**

Nach Abschluss der Aufzeichnung PerfView automatisch die Ablaufverfolgung zu öffnen und erweitern Sie die Optionen.

Für die Zwecke dieses Beispiels, interessieren wir uns vor allem die **Thread Zeit Stapel** Ansicht finden Sie unter **Gruppe erweitert**. Diese Ansicht zeigt die Gesamtzeit für einen Thread eine Methode, einschließlich CPU-Zeit und blockierte Zeit an, wie z. B. Datenträger-e/a oder auf Handles warten.

 ![Threadstapel-Zeit](media/perfview-thread-time-stacks.png)

 Beim Öffnen **Thread Zeit Stapel** anzuzeigen, wählen Sie die **Devenv** Prozess zur Analyse zu starten.

PerfView detaillierte Anleitungen zum Thread Zeit-Stapel unter eigene Menü "Hilfe", um eine ausführlichere Analyse lesen. Dieses Beispiel möchten wir in dieser Ansicht weiter zu filtern, indem nur einschließlich Stapel mit unserer Pakete-Modul und der Starttyp Thread.

1. Legen Sie **GroupPats** , leerer Text So entfernen Sie alle möglichen Gruppierungen, die standardmäßig hinzugefügt.
2. Legen Sie **IncPats** Teil Ihrer Assemblyname und Thread-Start zusätzlich zu vorhandenen Prozessfilter einschließen. In diesem Fall wird **Devenv; Startupthread. MakeVsSlowExtension**.

Die Ansicht zeigt jetzt nur Kosten, die mit den Assemblys, die im Zusammenhang mit der Erweiterung zugeordnet ist. In dieser Ansicht können jederzeit aufgeführt, unter dem **Inc (inklusive Kosten)** -Spalte der Start-Thread bezieht sich auf unsere gefilterte Erweiterung, und wird beim Start beeinträchtigt werden.

Im Beispiel oben einige interessante Aufruf wäre Stapel:

1. Mithilfe von e/a- `System.IO` Klasse: Zwar inklusive Kosten für diese Frames zu teuer in der Ablaufverfolgung unter nicht Umständen sind jedoch eine mögliche Ursache eines Problems, da die Datei-e/a-Geschwindigkeit von Computer zu Computer unterschiedlich sind.

   ![System-e/a-frames](media/perfview-system-io-frames.png)

2. Warten auf andere asynchrone Arbeit Aufrufe zum Blockieren: In diesem Fall würde der inklusiven Zeit, die Uhrzeit darzustellen, die auf den Abschluss asynchroner Arbeit der Hauptthread blockiert wird.

   ![blockierende Aufrufframes](media/perfview-blocking-call-frames.png)

Für eine der anderen Ansichten in der Ablaufverfolgung, die nützlich, um zu bestimmen, Auswirkungen gibt es die **Image-Load-Stapel**. Sie können die gleichen Filter angewendet, wie auf **Thread Zeit Stapel** anzuzeigen, und erfahren Sie, alle Assemblys, die aufgrund des Codes ausgeführt, indem Ihr Auto geladene Paket geladen.

Es ist wichtig, um die Anzahl der geladenen Assemblys in einem Paket Initialisierungsroutine zu minimieren, wie jede zusätzliche Assembly zusätzlichen Datenträger-e/a umfasst die Start auf langsameren Computern erheblich verlangsamen können.

## <a name="summary"></a>Zusammenfassung

Beim Start von Visual Studio wurde einer der Bereiche, die wir laufend Feedback erhalten, auf. Unser Ziel, wie bereits erwähnt, ist für alle Benutzer, damit eine konsistente Start auftreten, unabhängig von Komponenten und -Erweiterungen, die sie installiert haben. Wir möchten die Arbeit mit Besitzern von Erweiterung sie uns bei der Erreichung dieses Ziels unterstützen können. In den Anweisungen oben sind hilfreich zum Verständnis der Auswirkungen Erweiterungen beim Start und zum Vermeiden von entweder der Notwendigkeit, automatisch laden "oder" Laden Sie sie asynchron, um die Auswirkungen auf die Produktivität der Benutzer zu minimieren.
