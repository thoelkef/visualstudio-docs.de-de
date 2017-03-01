---
title: 'Gewusst wie: Diagnose-Erweiterung Leistung | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/08/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46b0a1e3-7e69-47c9-9d8d-a1815d6c3896
caps.latest.revision: 1
author: BertanAygun
ms.author: bertaygu
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f1226c9bd42476acc9fb57be0a6df8058174fd4d
ms.lasthandoff: 02/22/2017

---
# <a name="measuring-extension-impact-in-startup"></a>Messen der Erweiterung Auswirkung starten

## <a name="focus-on-extension-performance-in-visual-studio-2017"></a>Konzentrieren Sie sich auf die Leistung der Erweiterung in Visual Studio 2017

Basierend auf Feedback von Kunden, wurde die Schwerpunkte für Visual Studio 2017 Version eines Leistung beim Start und Lösung. Während als Visual Studio-Platform-Team, wir zur Verbesserung der Leistung beim Starten und die Lösung im Allgemeinen gearbeitet haben, schlägt unserer Telemetrie installierte Erweiterungen in solchen Szenarien auch eine erhebliche Auswirkung haben.

Um diese Auswirkungen Benutzern erleichtern, haben wir ein neues Feature in Visual Studio Validierungsfehlern langsam Erweiterungen hinzugefügt. Wenn Visual Studio eine neue Erweiterung, die Sie Laden der Projektmappe oder Start verlangsamt wird erkennt, wird Benutzern eine Benachrichtigung in der IDE zeigen sie im Dialogfeld neuen "Verwalten von Visual Studio Performance" angezeigt. Dieses Dialogfeld kann auch immer vom Menü Hilfe, um die zuvor erkannte Erweiterungen durchsuchen zugegriffen werden.

![Verwalten von Visual Studio für Datenereignis](media/manage-performance.png)

Dieses Dokument soll Entwicklern zu helfen Erweiterung beschreiben, wie die Erweiterung Auswirkung berechnet wird und wie es lokal analysiert werden kann zum Testen, ob eine Erweiterung als Erweiterung Beeinträchtigung der Leistung angezeigt werden kann.

## <a name="how-extensions-can-impact-startup"></a>Erweiterungen können wie Start auswirken.

Eine der häufigsten Verwendungsmöglichkeiten für Erweiterungen für Start Leistungseinbußen ist automatisch Laden eines bekannten Start Benutzeroberflächen-Kontexte wie NoSolutionExists oder ShellInitialized auswählen, indem. Diese Benutzeroberflächen-Kontexte abrufen während des Starts aktiviert und alle Pakete, die das Attribut "ProvideAutoLoad" in ihrer Definition mit diesen Kontexten gehören geladen und zu diesem Zeitpunkt initialisiert werden.

Wenn wir die Auswirkung einer Erweiterung messen, konzentrieren wir uns in erster Linie auf Zeitdauer von Erweiterungen, die automatisch laden in den oben aufgeführten Kontexten auswählen. Gemessene Zeiten sind jedoch nicht darauf beschränkt:

* Laden von Assemblys für die Erweiterung für synchrone Pakete
* In der Paket-Klassenkonstruktor für synchrone Pakete verstrichene Zeit.
* Zeit zum synchronen Pakete Paket initialisieren (oder SetSite)-Methode
* Für asynchrone Pakete die oben genannten Vorgänge Hintergrundthread ausgeführt werden und daher von der Überwachung ausgeschlossen werden
* Irgendwelche asynchronen Vorgänge, die während der Initialisierung des Pakets auf geplant Hauptthread verbrachte Zeit
* Ereignishandler, insbesondere Shell initialisiert Kontext Aktivierung oder die Änderung des Shell Zombie verbrachte Zeit

Wir haben mehrere beginnend mit Visual Studio 2015 um Hilfe zum Entfernen müssen zum automatischen Laden von Paketen, verschieben ihre Arbeitslast weitere Fälle, in denen Benutzer mehr sicher wären, dass die Erweiterung oder Erweiterung Auswirkungen verringern, wenn das automatische Laden von, Funktionen hinzugefügt.

Weitere Informationen zu diesen Funktionen finden Sie in den folgenden Dokumenten:

[Regel-basierten Benutzeroberflächen-Kontexte](how-to-use-rule-based-ui-context-for-visual-studio-extensions.md): eine umfangreichere basierend Regelmodul erstellt werden, um Benutzeroberflächen-Kontexte ermöglichen es Ihnen, benutzerdefinierte Kontexte basierend auf Projekttypen, Typen und Funktionen erstellen. Diese benutzerdefinierten Kontext können verwendet werden, ein Paket während der spezifische Szenarien wie z. B. das Vorhandensein eines Projekts mit einer bestimmten Funktion anstelle von Start laden. oder [Befehl Sichtbarkeit an einen benutzerdefinierten Kontext gebunden](https://msdn.microsoft.com/en-us/library/bb166512.aspx) basierend auf Projektfunktionen oder anderen verfügbaren Begriffe beseitigen, muss ein Paket zu laden, einen Befehl Status Abfrage Handler registriert.

[Unterstützung für asynchrone Paket](how-to-use-asyncpackage-to-load-vspackages-in-the-background.md): neue Basisklasse AsyncPackage in Visual Studio 2015 mit der Visual Studio-Pakete werden im Hintergrund geladen asynchron Laden des Pakets durch ein automatisches Laden oder eine asynchrone Abfrage angefordert wurde. Diese laden im Hintergrund kann die IDE reaktionsfähig bleiben, während die Erweiterung wird im Hintergrund und kritische Szenarien wie Auslastung starten und Lösung würde nicht betroffen.

[Asynchrone Dienste](how-to-provide-an-asynchronous-visual-studio-service.md): mit Unterstützung für asynchrone Paket, wir auch Unterstützung für asynchrone Abfragen von Diensten und asynchrone Dienste registrieren wird hinzugefügt. Darüber hinaus arbeiten wir zum Konvertieren von Visual Studio-Basisdienste, um asynchrone Abfrage unterstützt, sodass der größte Teil der Arbeit in einer Async-Abfrage in Hintergrundthreads auftritt. SComponentModel (Visual Studio-MEF-Host) ist eine der wichtigsten Dienste, die asynchrone Abfrage zu Erweiterungen zur Unterstützung der asynchronen Laden von vollständig unterstützt.

## <a name="reducing-impact-of-auto-loaded-extensions"></a>Reduzieren die Auswirkung des Auto Erweiterungen geladen

Wenn ein Paket weiterhin automatisch beim Start geladen werden muss, ist es wichtig, die Arbeit während der Initialisierung von Paket reduziert das Risiko der Erweiterung beeinträchtigen Start zu minimieren.

Werden einige Beispiele, die Paket-Initialisierung teuer sein könnte:

### <a name="use-of-synchronous-package-load-instead-of-asynchronous-package-load"></a>Verwendung von synchronen Paket Last statt für asynchrone Paket laden

Da synchrone Pakete auf den Hauptthread standardmäßig geladen werden, empfehlen wir die Erweiterung Besitzer auf, die automatisch geladen-Pakete, die die Basisklasse für asynchrone Paket stattdessen, wie bereits erwähnt verwendet haben. Ändern eines Pakets automatisch geladen, zur Unterstützung der asynchronen Laden von werden auch andere unten Fehlerbehebung erleichtern.

### <a name="synchronous-filenetwork-io-requests"></a>Synchrone Datei/Netzwerk-e/a-Anfragen

Im Idealfall sollte synchrone Anforderung zum Datei- oder Netzwerk-e/a im Hauptthread vermieden werden, ihre Auswirkung hängt Computerstatus und kann für längere Zeit in einigen Fällen blockiert.

Mithilfe von asynchronen Laden und asynchrone e/a-APIs sollten sicherstellen, dass Paket Initialisierung den Hauptthread in solchen Fällen blockiert nicht, und Benutzer mit Visual Studio arbeiten weiterhin können, während der e/a-Anforderungen im Hintergrund erfolgen.

### <a name="early-initialization-of-services-components"></a>Frühe Initialisierung von Services, Komponenten

Eines der allgemeine Muster bei der Initialisierung des Pakets ist Dienste entweder verwendet oder von diesem Paket in der Paket-Konstruktor oder in der Initialize-Methode bereitgestellten nicht initialisieren. Während dies wird, dass Dienste verwendet werden sichergestellt, können sie auch hinzufügen unnötige Kosten für das Paket geladen wird, wenn diese Dienste nicht sofort verwendet werden. Stattdessen sollten solche Dienste bei Bedarf, um die Arbeit in Paket Initialisierung zu minimieren initialisiert werden.

Für globale Dienste von einem Paket bereitgestellt wird können Sie die AddService-Methoden, die eine Funktion, die der Dienst verzögert initialisieren, nur, wenn sie von einer Komponente angefordert wird. Für Dienste, die innerhalb des Pakets verwendet werden, können Sie nutzen, Lazy<T> oder AsyncLazy<T> um sicherzustellen, dass Dienste werden bei der ersten Verwendung initialisiert/abgefragt.

## <a name="measuring-impact-of-auto-loaded-extensions-using-perfview"></a>Messen der Auswirkungen des automatischen Erweiterungen unter Verwendung von PerfView geladen

Codeanalyse Codepfade zu identifizieren, die Paket-Initialisierung verlangsamen können helfen kann, können Sie auch Tracing mithilfe der Auswirkungen einer Laden des Pakets in Visual Studio starten wie PerfView nutzen.

PerfView ist ein Tool zum System wide verfolgen, die Ihnen das Verständnis Langsamster Pfade in einer Anwendung aufgrund der CPU-Auslastung oder Blockierung Systemaufrufe helfen. Im folgenden finden Sie ein kurzes Beispiel zum Analysieren einer Beispiel-Erweiterungs, die PerfView unter Verwendung der [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=28567).

**Beispielcode:**

Dieses Beispiel basiert auf dem Beispiel folgenden Code, zum Anzeigen vorgesehen ist Fall einige häufige Ursachen für die Verzögerung:

```c#
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

**Aufzeichnen von Ablaufverfolgungsdaten mithilfe PerfView:**

Nachdem Sie Ihre Visual Studio-Umgebung, mit der Erweiterung installiert einrichten, können Sie eine Verfolgung des Startvorgangs aufzeichnen, indem PerfView öffnen und sammeln Dialogfeld "Erfassen" im Menü.

![Perfview erfassen Menü](media/perfview-collect-menu.png)

Standardoptionen bietet Aufruflisten für die CPU-Nutzung, doch da sowie Blockierungszeit interessiert sind, Sie sollten aktivieren "Thread Time" Stapel. Nachdem die Einstellungen bereit sind, können klicken Sie auf "Start-Sammlung" und starten Sie Visual Studio nach der Aufzeichnung gestartet wird.

Bevor Sie die Sammlung beenden, soll sicherstellen, dass Visual Studio vollständig initialisiert, das Hauptfenster ist vollständig sichtbar und weist die Erweiterung auf beliebige Teile der Benutzeroberfläche, die automatisch angezeigt, sie sind auch sichtbar werden. Nachdem Visual Studio vollständig geladen ist, und die Erweiterung initialisiert wird, können Sie zum Analysieren der Aufzeichnung beenden.

**Analysieren mit PerfView Trace:**

Nach Abschluss der Aufzeichnung PerfView automatisch Trace öffnen und Optionen.

Für die Zwecke dieses Beispiels ist sind es in erster Linie der "Thread-Zeit" Stapelansicht finden Sie unter "Advanced Group" interessiert. In dieser Ansicht wird die gesamte Zeit in einem Thread, eine Methode, einschließlich CPU-Zeit und blockierte Zeit, z. B. Datenträger-e/a oder warten auf Handles angezeigt.

 ![Threadstapel Zeit](media/perfview-thread-time-stacks.png)

 Wählen Sie beim Öffnen von "Thread Zeit Stapel" angezeigt, den Prozess "Devenv" Analyse zu starten.

PerfView detaillierte Anleitung zum Thread Zeit Stapel unter eigene Menü "Hilfe", um eine ausführlichere Analyse lesen. Dieses Beispiel möchten wir diese Ansicht noch weiter zu filtern, indem nur einschließlich Stapel mit Paketen-Modul und der Starttyp Thread.

1. Legen Sie "GroupPats" auf leerer Text So entfernen Sie alle möglichen Gruppierungen standardmäßig hinzugefügt.
2. Gruppe "IncPats", um einen Teil der Name der Assembly enthalten und Start-Thread neben vorhandenen Prozessfilter. In diesem Fall sollten sie "Devenv; sein. Startupthread. MakeVsSlowExtension".

Die Ansicht zeigt jetzt nur Kosten, die mit den Assemblys, die im Zusammenhang mit der Erweiterung zugeordnet ist. In dieser Ansicht können jederzeit "Inc" (einschließlich Kosten) Spalte des Start-Thread bezieht sich auf die gefilterten Erweiterung und wird Auswirkungen auf Start.

Für das Beispiel über einige interessante Aufruf wäre Stapel:

1. E/a über System.IO-Klasse: inklusive Kosten für diese Frames nicht sehr teuer in der Ablaufverfolgung möglicherweise, können sie eine mögliche Ursache für ein Problem sind, da Datei-e/a-Geschwindigkeit von Computer zu Computer unterschiedlich sind.

  ![System-e/a-frames](media/perfview-system-io-frames.png)

2. Blockierende Aufrufe, die auf andere asynchrone Arbeit warten: In diesem Fall würde der inklusiven Zeit der Hauptthread, auf den Abschluss des asynchronen Vorgänge blockiert ist Zeit darstellen.

  ![blockierenden Aufruf frames](media/perfview-blocking-call-frames.png)

Einer der anderen Ansichten in der Ablaufverfolgung, die Auswirkung bestimmt werden werden die "Image Load-Stacks". Sie können dieselben Filter anwenden, die auf "Thread-Zeit" Stapelansicht angewendet und erfahren Sie, alle Assemblys, die aufgrund der Code ausgeführt, indem die automatische geladene Paket geladen.

Es ist wichtig, die Anzahl der geladenen Assemblys in einem Paket Initialisierungsroutine zu minimieren, wie jede zusätzliche Assembly zusätzliche Datenträger-e/a umfasst die Start auf langsameren Computern erheblich verlangsamen können.

## <a name="summary"></a>Zusammenfassung

Starten von Visual Studio wurde einer der Bereiche, die ständig Feedback erhalten wir bei. Unser Ziel, wie bereits erwähnt ist es für alle Benutzer haben einen konsistenten Start auftreten, unabhängig von Komponenten und Erweiterungen, die sie installiert haben, und wir arbeiten mit Erweiterung Besitzer können ihnen helfen, dieses Ziel zu erreichen möchten. In den Anweisungen oben sind hilfreich zum Verständnis der Auswirkungen Extensions auf Start und die entweder entfällt die Notwendigkeit automatisch laden oder Laden sie asynchron, um die Beeinträchtigung der Benutzerproduktivität zu minimieren.
