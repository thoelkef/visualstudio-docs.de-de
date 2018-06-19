---
title: 'Vorgehensweise: Erweiterung Leistung diagnostizieren | Microsoft Docs'
ms.custom: ''
ms.date: 11/08/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
author: BertanAygun
ms.author: bertaygu
manager: douge
ms.workload:
- bertaygu
ms.openlocfilehash: 60a7d1c3178d0fd74983d3f1096d01e578a49a00
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133267"
---
# <a name="measuring-extension-impact-in-startup"></a>Messen der Erweiterung Auswirkung beim Start

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Konzentrieren Sie sich auf die Leistung der Erweiterung in Visual Studio 2017

Basierend auf Feedback von Kunden, wurde eine die Schwerpunktbereiche für Visual Studio-2017 Version Leistung beim Start und Lösung. Zwar als Visual Studio-Platform-Team, wir haben zur Verbesserung der Leistung beim Start und Lösung im Allgemeinen gearbeitet bereits, schlägt unserer Telemetrie installierte Erweiterungen auch einen erheblichen Einfluss auf die Szenarios besitzen können.

Um diese Auswirkungen besser zu verstehen Benutzern erleichtern, haben wir ein neues Feature in Visual Studio um informieren, dass der langsamen Erweiterungen hinzugefügt. Wenn Visual Studio eine neue Erweiterung, die Sie Laden der Projektmappe oder Start verlangsamt wird erkennt, sehen Benutzer eine Benachrichtigung in der IDE, Dialogfeld "Neues"Verwalten von Visual Studio-Leistung"" auf. Dieses Dialogfeld kann auch immer über Menü "Hilfe" So durchsuchen Sie die zuvor erkannte Erweiterungen zugegriffen werden.

![Verwalten von Visual Studio leistungsbezogener](media/manage-performance.png)

Dieses Dokument zielt darauf ab, damit Entwickler auf Erweiterung beschreiben, wie Erweiterung Auswirkungen berechnet wird und wie es lokal analysiert werden kann zum Testen, ob eine Erweiterung als eine Erweiterung mit Auswirkungen auf Leistung angezeigt werden kann.

> [!NOTE]
> Dieses Dokument konzentriert sich auf die Auswirkungen von Erweiterungen, die beim Laden von Start- und Lösung. Erweiterungen auf die Visual Studio-Leistungs auswirken, wenn sie bewirken, die Benutzeroberfläche dass reagiert. Weitere Informationen zu diesem Thema finden Sie unter [wie: Diagnose UI Verzögerungen, die aufgrund von Erweiterungen](how-to-diagnose-ui-delays-caused-by-extensions.md).

## <a name="how-extensions-can-impact-startup"></a>Erweiterungen können wie Start beeinträchtigen.

Eine der häufigsten Verwendungsmöglichkeiten für Erweiterungen, die Leistung beim Start beeinträchtigen ist durch automatisches Laden an einem der bekannten Autostart-UI-Kontexten wie z. B. NoSolutionExists oder ShellInitialized auswählen. Kontexten UI erhalten während des Starts aktiviert und alle Pakete, die das Attribut "ProvideAutoLoad" in ihrer Definition mit diesen Kontexten enthalten sind, geladen und zu diesem Zeitpunkt initialisiert werden.

Wenn wir die Auswirkung einer Erweiterung messen, konzentrieren wir uns in erster Linie auf Zeit, diese Erweiterungen, die automatisch geladen, in den oben aufgeführten Kontexten auswählen. Gemessene Zeiten enthalten würde, aber nicht darauf beschränkt:

* Laden von Assemblys für die Erweiterung für synchrone Pakete
* In der Paket-Klassenkonstruktor für synchrone Pakete verbrachte Zeit
* Zeit zum synchronen Pakete Paket initialisieren (oder SetSite)-Methode
* Für asynchrone Pakete die oben genannten Vorgänge im Hintergrundthread ausgeführt, und daher von der Überwachung ausgeschlossen werden
* Alle asynchronen Arbeit während der Initialisierung des Pakets auf den Hauptthread ausgeführt verbrachte Zeit
* In den Ereignishandlern, insbesondere Shell initialisiert Kontext Aktivierung oder die Shell Zombie Zustandsänderung verbrachte Zeit
* Beginnend mit Visual Studio 2017 Update 3, wird es auch starten der Überwachung erforderliche Zeit bei Leerlauf aufrufen vor der Initialisierung Shell. Lange Vorgänge im Leerlauf Handler auch dazu führen, dass nicht reagierenden IDE und tragen zu einer vom Benutzer wahrgenommene Startzeit.

Wir haben mehrere beginnend mit Visual Studio 2015, um Hilfe beim Entfernen von die Notwendigkeit der Pakete automatisch geladen, verschieben ihre Arbeitslast auf spezifischere Fälle, in denen Benutzer mehr sicher wäre, dass die Erweiterung oder eine Erweiterung Auswirkungen zu reduzieren, beim Laden von, Funktionen hinzugefügt automatisch.

Weitere Informationen zu diesen Funktionen finden Sie in den folgenden Dokumenten:

[Regel-basierte Benutzeroberfläche Kontexten](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): eine umfangreichere regelbasiert-Modul erstellte Bedingungsausdruck UI Kontexten ermöglichen es Ihnen, benutzerdefinierte Kontexte basierend auf Projekttypen, Typen und Funktionen zu erstellen. Dieser benutzerdefinierte Kontexte können ein Paket während der spezifische Szenarien wie etwa der Anwesenheit eines Projekts mit einer bestimmten Funktion anstelle von Start laden verwendet werden. erlauben oder die [Befehl Sichtbarkeit mit einem benutzerdefinierten Kontext](visibilityconstraints-element.md) basierend auf Projektfunktionen oder anderen verfügbaren Begriffe somit Dadurch entfällt die Notwendigkeit ein Paket zu laden, wenn einen Befehl Status Abfrage Handler registriert.

[Unterstützung für asynchrone Paket](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): die neue AsyncPackage Basisklasse in Visual Studio 2015 mit der Visual Studio-Pakete werden im Hintergrund geladen asynchron, wenn das Laden des Pakets durch ein automatisches Laden-Attribut oder eine asynchrone Abfrage angefordert wurde . Diese Hintergrund laden kann die IDE reaktionsfähig bleiben, während die Erweiterung im Hintergrund initialisiert wird und kritische Szenarien wie starten und die Projektmappe laden wäre nicht beeinträchtigt werden.

[Asynchrone Dienste](how-to-provide-an-asynchronous-visual-studio-service.md): mit Unterstützung für asynchrone Paket wir auch Unterstützung für asynchrone Dienste registriert werden und Abfragen von Diensten asynchron hinzugefügt. Wir arbeiten vor allem zum Konvertieren von Visual Studio-Kerndienste, um asynchrone Abfrage unterstützt, sodass der Großteil der Arbeit in einer Async-Abfrage in Hintergrundthreads auftritt. SComponentModel (Visual Studio-MEF-Host) ist eine der wichtigsten Dienste, die unterstützt jetzt die asynchrone Abfrage von Erweiterungen zur Unterstützung asynchronen vollständig laden können.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reduzieren der Auswirkungen von "Auto" Erweiterungen geladen

Wenn ein Paket weiterhin automatisch beim Start geladen werden muss, ist es wichtig, um die Arbeit, die während der Paket-Initialisierung reduziert die Wahrscheinlichkeit der Auswirkungen auf die Autostart-Erweiterung zu minimieren.

Sind einige Beispiele, die Paket-Initialisierung teuer verursachen könnte:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Verwenden des synchronen Paket Last statt für das Laden des Pakets asynchrone

Da die synchrone Pakete standardmäßig auf den Hauptthread geladen werden, empfehlen wir Erweiterung Besitzer auf, die automatisch geladen-Pakete, die die Basisklasse für asynchrone Paket verwenden Sie stattdessen, wie bereits erwähnt wurden. Ändern eine automatische geladene Paket zur Unterstützung von asynchronen Laden von wird auch der anderen unten Problemen vereinfachen.

### <a name="synchronous-filenetwork-io-requests"></a>Synchrone Datei/Netzwerk-e/a-Anforderungen

Im Idealfall sollten alle synchronen Datei- oder Netzwerk-e/a-Anforderung im Hauptthread vermieden werden, wie ihre Auswirkungen vom Status des Computers hängt und kann für längere Zeit in einigen Fällen blockieren.

Verwenden von asynchronen Paket laden und asynchrone e/a-APIs sollten sicherstellen, dass Paket Initialisierung nicht den Hauptthread in solchen Fällen blockiert und Benutzer können für die Interaktion mit Visual Studio, beim Auftreten von e/a-Anforderungen im Hintergrund fortgesetzt.

### <a name="early-initialization-of-services-components"></a>Frühe Initialisierung des Services, Komponenten

Eine allgemeine Schemas im Paket-Initialisierung ist initialisieren Dienste entweder verwendet oder von diesem Paket in der Paket-Konstruktor oder die Initialize-Methode bereitgestellt. Während dadurch wird, dass die Dienste sichergestellt zu verwendende bereit sind, können sie auch hinzufügen unnötige Kosten zum Packen von laden, wenn diese Dienste nicht sofort verwendet werden. Diese Dienste sollten stattdessen bei Bedarf, um die Arbeit, die im Paket-Initialisierung zu minimieren initialisiert werden.

Für globale Dienste, die von einem Paket bereitgestellt werden können Sie die AddService-Methoden, die übernimmt eine Funktion des Diensts verzögert initialisiert wird, nur, wenn sie von einer Komponente angefordert werden. Für Dienste, die innerhalb des Pakets verwendet werden, können Sie verwenden und Lazy<T> oder AsyncLazy<T> um sicherzustellen, dass Dienste sind bei der ersten Verwendung initialisiert/abgefragt.

## <a name="measuring-impact-of-auto-loaded-extensions-using-activity-log"></a>Messen der Auswirkungen von "Auto" Aktivitätsprotokoll mit Erweiterungen geladen

Ab Visual Studio 2017 Update 3 wird Aktivitätsprotokoll für Visual Studio jetzt Einträge für die Auswirkungen auf die Leistung von Paketen beim Laden von Start- und Lösung enthalten. Um diese Maße angezeigt wird, müssen Sie starten Sie Visual Studio mit/Log-Schalter und ActivityLog.xml-Datei zu öffnen.

Im Aktivitätsprotokoll, die Einträge werden unter "Verwalten von Visual Studio-Leistung" Quelle und sieht wie folgt aus:

```Component: 3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c, Inclusive Cost: 2008.9381, Exclusive Cost: 2008.9381, Top Level Inclusive Cost: 2008.9381```

Dies bedeutet, dass das Paket mit GUID "3cd7f5bf-6662-4ff0-ade8-97b5ff12f39c" hat 2008 Millisekunden in Start von Visual Studio. Beachten Sie, dass Visual Studio die Kosten für die oberste Ebene als primäre Telefonnummer betrachtet, bei der Berechnung der Auswirkungen eines Pakets wie, die der Benutzer Savigs wäre finden Sie, wenn sie die Erweiterung für das Paket zu deaktivieren.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Messen der Auswirkungen von "Auto" Erweiterungen unter Verwendung von PerfView geladen

Während der Codeanalyse Codepfade zu identifizieren, die Paket-Initialisierung verlangsamt helfen kann, können Sie auch Ablaufverfolgung verwenden, mithilfe von Anwendungen wie PerfView zu einem Laden des Pakets in Visual Studio starten auswirkt.

PerfView ist ein Tool zum System wide verfolgen, die zum Verständnis der hot Pfade in einer Anwendung entweder aufgrund von CPU-Auslastung oder Systemaufrufe blockiert wird. Im folgenden finden Sie ein kurzes Beispiel für eine beispielerweiterung mit PerfView zur Analyse der [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Beispielcode:**

Dieses Beispiel beruht auf dem Beispiel einige häufige Ursachen für die Verzögerung case-Code unten, zum Anzeigen vorgesehen ist:

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

Nachdem Sie Ihr Visual Studio-Umgebung, die Erweiterung installiert einrichten, können Sie eine Ablaufverfolgung Starten von PerfView öffnen und erfassen Dialogfeld "Erfassen" Menü aufzeichnen.

![Perfview erfassen Menü](media/perfview-collect-menu.png)

Die Standardoptionen gebe Aufruflisten für die CPU-Nutzung, doch da wir auch Blockierungszeit interessiert sind, Sie sollten aktivieren "Zeitraum der Thread" Stapel. Sobald die Einstellungen bereit sind können Sie klicken Sie auf "Sammlung starten" und starten Sie Visual Studio aus, sobald die Aufzeichnung gestartet wird.

Bevor Sie die Datenerfassung beenden, um sicherzustellen, dass Visual Studio vollständig initialisiert, das Hauptfenster vollständig sichtbar ist und weist die Erweiterung alle Teile der Benutzeroberfläche, die automatisch angezeigt, sie werden auch angezeigt werden soll. Sobald Visual Studio vollständig geladen ist, und die Erweiterung wird initialisiert, können Sie die zum Analysieren der Aufzeichnung beenden.

**Analysieren eine Ablaufverfolgung mit PerfView:**

Nach Abschluss der Aufzeichnung PerfView automatisch Trace öffnen und expand-Optionen.

Für die Zwecke dieses Beispiels können sind wir die "Thread-Zeit" Stapelansicht finden Sie unter"Advanced" können vor allem interessiert. In dieser Ansicht zeigt die Gesamtzeit, die mit einer anderen Methode einschließlich CPU-Zeit und blockierte Zeit, z. B. Datenträger-e/a oder warten auf Handles an einen Thread aufgewendet wurde.

 ![Zeit Threadstapel](media/perfview-thread-time-stacks.png)

 Beim Öffnen von "Thread-Zeit" Stapelansicht, sollten Sie den Prozess "Devenv" Analyse starten auswählen.

PerfView detaillierte Anleitungen zum Thread Zeit Stapel im eigenen Menü "Hilfe" für eine ausführlichere Analyse lesen. Für die Zwecke dieses Beispiels möchten wir diese Ansicht noch weiter zu filtern, indem nur einschließlich Stapel mit unserem Pakete-Modul und der Starttyp Thread.

1. Legen Sie "GroupPats" auf leerer Text So entfernen Sie alle Gruppierung standardmäßig hinzugefügt.
2. Gruppe "IncPats", um einen Teil der Name der Assembly enthalten und starten-Thread zusätzlich zu vorhandenen Prozessfilter. In diesem Fall sollten sie "Devenv; sein. Startupthread. MakeVsSlowExtension".

Die Ansicht zeigt jetzt nur Kosten, die die Assemblys, die im Zusammenhang mit der Erweiterung zugeordnet ist. In dieser Ansicht können jederzeit "Inc" (einschließlich Kosten)-Spalte der Startupthread bezieht sich auf unser gefilterte Erweiterung und wird Auswirkungen auf Start.

Im Beispiel oben einige interessante Aufruf wäre Stapel:

1. E/a über System.IO-Klasse: während inklusive Kosten dieser Frames nicht in der Ablaufverfolgung sehr aufwendig ist, können sie eine mögliche Ursache für ein Problem sind, da die Datei-e/a-Geschwindigkeit von Computer zu Computer unterschiedlich sind.

  ![System-e/a-frames](media/perfview-system-io-frames.png)

2. Blockierende Aufrufe, die auf anderen asynchroner Arbeit warten: In diesem Fall würden inklusive Zeit die Zeit der Haupt-Thread wird, auf den Abschluss asynchroner Arbeit blockiert darstellen.

  ![blockierenden Aufruf frames](media/perfview-blocking-call-frames.png)

Zum Erstellen anderer Ansichten in der Ablaufverfolgung, die Auswirkungen herausfinden werden wird "Bild laden Stapel" sein. Dieselben Filter anwenden, entsprechend der Anwendung auf "Thread-Zeit" Stapelansicht können und herauszufinden, alle Assemblys, die aufgrund der Code ausgeführt, indem Ihr Auto geladene Paket nicht geladen werden.

Es ist wichtig, die Anzahl der geladenen Assemblys in einem Paket Initialisierungsroutine zu minimieren, wie jede zusätzliche Assemblyverweise zusätzlichen Datenträger-e/a umfassen die Systemstart erheblich langsamer Computer verlangsamen können.

## <a name="summary"></a>Zusammenfassung

Starten von Visual Studio wurde einer der Bereiche fortlaufend Feedback erhalten wir auf. Unser Ziel wie bereits erwähnt ist für alle Benutzer haben einen konsistente Start auftreten, unabhängig von Komponenten und die Erweiterungen aus, die sie installiert haben, und wir arbeiten mit Besitzern der Erweiterung auf die Umsetzung helfen, dieses Ziel zu erreichen möchten. In den Anweisungen oben sollte hilfreich sein, zum verstehen Erweiterungen wirkt sich auf Start und entweder vermieden das automatische Laden oder asynchron, sodass nur minimal beeinträchtigt, auf die Benutzerproduktivität zu laden.
