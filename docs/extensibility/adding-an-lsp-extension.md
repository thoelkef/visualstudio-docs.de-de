---
title: "Hinzufügen einer Erweiterung der Sprache Serverprotokoll | Microsoft Docs"
ms.custom: 
ms.date: 11/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: ea93ddee9c47f80322db2403aeecc0fb7dddb209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="adding-a-language-server-protocol-extension"></a>Hinzufügen einer Sprache Serverprotokoll-Erweiterung

Die Language-Server-Protokoll (LSP) ist ein gemeinsames Protokoll, in Form von JSON-RPC v2. 0, verwendet, um die Sprache Dienstfunktionen für verschiedene Codeeditoren bieten. Mit dem Protokoll können Entwickler schreiben ein Servers einsprachige Language Servicefunktionen wie IntelliSense, Fehlerdiagnosen angeben, suchen alle Verweise usw. zu verschiedenen Codeeditoren, die die LSP unterstützen. Bisher können Dienste für die Sprachen in Visual Studio hinzugefügt werden, entweder mithilfe von TextMate Grammatikdateien bieten grundlegende Funktionen, z. B. syntaxhervorhebung, oder durch Schreiben von benutzerdefinierten Language-Diensten, die mit den vollständigen Satz von Visual Studio-Erweiterbarkeits-APIs auf Bereitstellen Sie umfangreichere Daten. Jetzt Unterstützung für LSP als dritte Möglichkeit bietet.

![Language-Server-Protokoll-Dienst in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Language-Server-Protokoll

Weitere Informationen über das Protokoll selbst, finden Sie in der Dokumentation [hier](https://github.com/Microsoft/language-server-protocol). Visual Studio-Implementierung der Sprache Serverprotokolls ist in der Vorschau und Unterstützung experimentellen berücksichtigt werden sollten. Die Preview-Version wird in Form einer Erweiterung ([Sprache Server Protokoll Client Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)), **dieser Erweiterung kann nur auf die Vorschau Kanal von Visual Studio installiert werden, aber**. Eine höhere Version von Visual Studio umfasst integrierten Unterstützung für das Language-Server-Protokoll zu diesem Zeitpunkt das Preview-Flag gelöscht werden. **Sie sollten die Preview-Version nicht für Produktionszwecke verwenden.**

Weitere Informationen zum Erstellen einer Beispiel-Language-Server oder Vorgehensweise beim Integrieren von eines vorhandenen Servers für die Sprache in Visual Studio-Code finden Sie die Dokumentation [hier](https://code.visualstudio.com/docs/extensions/example-language-server).

![Language-Server-protokollimplementierung](media/lsp-implementation.png)

In diesem Artikel wird beschrieben, wie eine Visual Studio-Erweiterung zu erstellen, die einen Server LSP-basierte Sprache verwendet wird. Es wird davon ausgegangen, dass Sie bereits einen Server LSP-basierte Sprache entwickelt haben und nur in Visual Studio integrieren möchten.

Für die Unterstützung in Visual Studio können Language-Server mit dem Client (Visual Studio) über die folgenden Mechanismen kommunizieren:

* Standard-e/a-streams
* Benannte pipes
* Sockets

Der Zweck der LSP und Unterstützung in Visual Studio besteht darin, Dienste für integrierte Sprachen, die nicht Teil der Visual Studio-Produkten sind. Es ist nicht vorgesehen, um vorhandene Sprachdienste (z. B. c#) in Visual Studio erweitern. Um vorhandene Sprachen zu erweitern, finden Sie in der Sprachdienst Erweiterbarkeit Handbuch (z. B. die ["Roslyn".NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

## <a name="language-server-protocol-features-supported"></a>Server-Protokoll-Sprachfunktionen unterstützt

Bisher werden die folgenden LSP-Funktionen in Visual Studio unterstützt:

Meldung | Verfügt über Unterstützung in Visual Studio
--- | ---
Initialisieren | ja
initialisiert | ja
Herunterfahren | ja
Beenden | ja
$/cancelRequest | ja
window/showMessage | ja
window/showMessageRequest | ja
window/logMessage | ja
Telemetrie-Ereignis |
client/registerCapability |
client/unregisterCapability |
workspace/didChangeConfiguration | ja
workspace/didChangeWatchedFiles | ja
workspace/symbol | ja
workspace/executeCommand | ja
workspace/applyEdit | ja
textDocument/publishDiagnostics | ja
textDocument/didOpen | ja
textDocument/didChange | ja
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | ja
textDocument/didClose | ja
textDocument/completion | ja
Abschluss/auflösen | ja
TextDocument/gezeigt wird | ja
textDocument/signatureHelp | ja
textDocument/references | ja
textDocument/documentHighlight |
textDocument/documentSymbol | ja
TextDocument/Formatierung | ja
textDocument/rangeFormatting | ja
textDocument/onTypeFormatting |
textDocument/definition | ja
textDocument/codeAction | ja
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | ja

## <a name="getting-started"></a>Erste Schritte

### <a name="create-a-vsix-project"></a>Erstellen Sie ein VSIX-Projekt

Um eine Erweiterung der Sprache mithilfe eines Servers LSP-basierte Sprache zu erstellen, stellen Sie zunächst sicher, dass Sie die **Development für Visual Studio-Erweiterung** Arbeitslast für die Instanz von Visual Studio installiert.

Als Nächstes erstellen Sie eine neue leere VSIXProject empfängerrollenbildschirm **Datei** > **neues Projekt** > **Visual C#-**  >   **Erweiterbarkeit** > **VSIX-Projekt**:

![Erstellen Sie die Vsix-Projekt](media/lsp-vsix-project.png)

Für die Vorschauversion werden in Form einer VSIX VS-Unterstützung für LSP ([Microsoft.VisualStudio.LanguageServer.Client.Preview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)). Erweiterung-Entwickler, die eine Erweiterung mit LSP Sprache Servern erstellen möchten, müssen eine Abhängigkeit auf diese VSIX schalten. Deshalb Kunden, die zum Installieren von Server-spracherweiterung **müssen zunächst die Sprache Server Protokoll Client Preview VSIX installieren.**

Zum Definieren der VSIX-Abhängigkeit für die VSIX im VSIX-Manifesten-Designer (durch Doppelklicken auf die Datei "Source.Extension.vsixmanifest" in Ihrem Projekt) öffnen, und navigieren Sie zu **Abhängigkeiten**:

![Verweis auf die Sprache, Server-Protokoll-Client hinzufügen](media/lsp-reference-lsp-dependency.png)

Erstellen Sie eine neue Abhängigkeit wie folgt:

![Definieren von Language Server-Protokoll-Client-Abhängigkeit](media/lsp-define-lsp-dependency.png)

* **Quelle**: manuell definiert werden
* **Namen**: Sprache Server-Protokoll-Client-Vorschau
* **Identifier**: Microsoft.VisualStudio.LanguageServer.Client.Preview
* **Versionsbereich**: [1.0,2.0)
* **Wie Abhängigkeit aufgelöst wird**: vom Benutzer installiert
* **Download-URL**: [https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview)

> [!NOTE]
> Die **Download-URL** muss ausgefüllt werden, damit Benutzer die Erweiterung installieren wissen, wie Sie die Installation der erforderlichen Abhängigkeit.

### <a name="language-server-and-runtime-installation"></a>Sprachinstallation Server- und Laufzeit

Standardmäßig werden die Erweiterungen zur Unterstützung von Servern LSP-basierte Sprache in Visual Studio erstellt nicht die Language-Server selbst oder die Laufzeiten erforderlich, um sie auszuführen enthalten. Erweiterung Entwickler sind verantwortlich für das Verteilen der Sprache und die Laufzeiten erforderlich sind. Es gibt mehrere Arten erreichen:

* Language-Servern können in VSIX-Pakete als Inhaltsdateien eingebettet werden.
* Erstellen Sie eine MSI-Datei, um das Language-Server zu installieren und/oder Laufzeiten erforderlich.
* Enthalten Sie Anweisungen Marketplace Hinweis Benutzer so Laufzeiten und Language-Servern zu erhalten.

### <a name="textmate-grammar-files"></a>TextMate Grammatik-Dateien

LSP umfasst keine Spezifikation zum Text farbliche Kennzeichnung für Sprachen bereitstellen. Um benutzerdefinierte farbliche Kennzeichnung für Sprachen in Visual Studio zu gewährleisten, können Entwickler Erweiterung eine TextMate Grammatik-Datei. Um benutzerdefinierte TextMate Grammatik oder Design-Dateien hinzuzufügen, gehen Sie folgendermaßen vor:

1. Erstellen einen Ordner namens "Grammatiken" innerhalb der Erweiterung (oder sie können einen beliebigen Namen, die Sie auswählen, werden).

2. Umfassen Sie in diesem Ordner "Grammatiken" alle *.tmlanguage, *.plist, *.tmtheme oder *.JSON Dateien, Sie möchten die farbliche Kennzeichnung von benutzerdefinierten bereitstellt.

3. Mit der rechten Maustaste auf die Dateien, und wählen **Eigenschaften**. Ändern Sie den Buildvorgang, **Content** und **Include in VSIX** Eigenschaft auf "true".

4. Erstellen Sie eine PKGDEF-Datei, und fügen eine Zeile, die etwa wie folgt hinzu:

  ```xml
  [$RootKey$\TextMate\Repositories]
  "MyLang"="$PackageFolder$\Grammars"
  ```

5. Mit der rechten Maustaste auf die Dateien, und wählen **Eigenschaften**. Ändern Sie den Buildvorgang, **Content** und **Include in VSIX** Eigenschaft auf "true".

Nach Abschluss der vorherigen Schritte, wird ein Ordner "Grammatiken" zum Installieren des Pakets hinzugefügt Verzeichnis als Quelle Repository mit dem Namen "MyLang" ("MyLang" ist nur ein Name für Mehrdeutigkeit und jede eindeutige Zeichenfolge sein kann). Alle Grammatiken (.tmlanguage-Dateien) und Design (.tmtheme)-Dateien in diesem Verzeichnis werden als Potenziale übernommen, und setzen alle integrierten Grammatiken mit TextMate bereitgestellt. Wenn die Grammatikdatei deklarierten Erweiterungen die Erweiterung der Datei geöffnet, die übereinstimmen, wird in TextMate Schritt.

## <a name="creating-a-simple-language-client"></a>Erstellen einen einfache Sprache-client

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Hauptschnittstelle - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Nach dem Erstellen eines VSIX-Projekts, fügen Sie dem Projekt die folgenden NuGet-Pakete hinzu:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Wenn Sie übernehmen eine Abhängigkeit auf der NuGet-Paket aus, nachdem Sie die vorherigen Schritte abgeschlossen, werden die Pakete Newtonsoft.Json und StreamJsonRpc ebenfalls dem Projekt hinzugefügt. **Diese Pakete werden nicht aktualisiert werden, es sei denn, Sie sind sich sicher, dass diese neuen Versionen auf die Version von Visual Studio installiert werden, die Ihre Erweiterung Ziele**. Assemblys werden nicht eingeschlossen in Ihre VSIX--stattdessen sie werden upgradetest werden aus dem Visual Studio-Installationsverzeichnis. Wenn Sie eine neuere Version der Assemblys als auf dem Computer eines Benutzers, die Erweiterung Komponenten installierten referenzieren *funktioniert nicht*.

Sie können dann erstellen Sie eine neue Klasse, die implementiert die [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) -Schnittstelle, die Hauptschnittstelle für die von Sprachclients Verbindungen mit einem Server LSP-basierte Sprache erforderlich sind.

Im folgenden finden ein Beispiel:

```csharp
namespace MockLanguageExtension
{
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
        public string Name => "Bar Language Extension";

        public IEnumerable<string> ConfigurationSections => null;

        public object InitializationOptions => null;

        public IEnumerable<string> FilesToWatch => null;

        public event AsyncEventHandler<EventArgs> StartAsync;
        public event AsyncEventHandler<EventArgs> StopAsync;

        public async Task<Connection> ActivateAsync(CancellationToken token)
        {
            await Task.Yield();

            ProcessStartInfo info = new ProcessStartInfo();
            info.FileName = Path.Combine(Path.GetDirectoryName(Assembly.GetExecutingAssembly().Location), "Server", @"MockLanguageServer.exe");
            info.Arguments = "bar";
            info.RedirectStandardInput = true;
            info.RedirectStandardOutput = true;
            info.UseShellExecute = false;
            info.CreateNoWindow = true;

            Process process = new Process();
            process.StartInfo = info;

            if (process.Start())
            {
                return new Connection(process.StandardOutput.BaseStream, process.StandardInput.BaseStream);
            }

            return null;
        }

        public async Task OnLoadedAsync()
        {
            await StartAsync?.InvokeAsync(this, EventArgs.Empty);
        }

        public async Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public async Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Die wichtigsten Methoden, die implementiert werden müssen, sind [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) und [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) wird aufgerufen, wenn Visual Studio die Erweiterung geladen wurde und der Language-Server kann jetzt gestartet werden soll. In dieser Methode rufen Sie die [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) sofort zu signalisieren, dass die Language-Server gestartet werden soll, oder Sie können zusätzliche Logik und Aufrufen Delegaten [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) später. **Um den Server für die Sprache zu aktivieren, müssen Sie irgendwann StartAsync aufrufen.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) letztendlich von Aufrufen aufgerufene Methode wird die [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegieren; es enthält die Logik zum Starten Sie den Server für die Sprache und die Verbindung damit herstellen. Ein Verbindungsobjekt, Streams zum Schreiben auf den Server und vom Server gelesen enthält, muss zurückgegeben werden. Alle Ausnahmen abgefangen und Benutzer über eine Nachricht Infoleiste in Visual Studio angezeigt.

### <a name="activation"></a>Aktivierung

Nachdem die Language-Client-Klasse implementiert ist, müssen Sie definieren zwei Attribute zum definieren, wie es in Visual Studio geladen und aktiviert:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio verwendet [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) zum Verwalten der Erweiterungspunkte. Die [exportieren](https://msdn.microsoft.com/library/system.componentmodel.composition.exportattribute(v=vs.110).aspx) Attribut zeigt Visual Studio an, dass diese Klasse als ein Erweiterungspunkt übernommen und zum geeigneten Zeitpunkt geladen werden soll.

Um MEF verwenden zu können, müssen Sie auch MEF als Ressource im VSIX-Manifest definieren.

Öffnen Sie die VSIX-manifest-Designer, und navigieren Sie zu der **Bestand** Registerkarte:

![MEF-Anlage hinzufügen](media/lsp-add-asset.png)

Klicken Sie auf "Neu", um ein neues Objekt zu erstellen:

![Definieren von MEF-Medienobjekt](media/lsp-define-asset.png)

* **Type**: Microsoft.VisualStudio.MefComponent
* **Quelle**: ein Projekt in der aktuellen Projektmappe
* **Projekt**: [Ihr Projekt]

### <a name="content-type-definition"></a>Content-Type-Definition

Derzeit ist die einzige Möglichkeit, Ihre servererweiterung LSP-basierte Sprache Laden von Datei-Inhaltstyp. D. h. beim Definieren Ihrer Sprache-Client-Klasse (implementiert [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), müssen Sie definieren die Typen von Dateien, die beim geöffnet ist, führt dazu, dass eine Erweiterung zu laden. Wenn keine Dateien, die die definierten Inhaltstyp entsprechen geöffnet sind, wird die Erweiterung nicht geladen werden.

Dies erfolgt über eine oder mehrere ContentTypeDefinition Klassen definieren:

```csharp
namespace MockLanguageExtension
{
    public class BarContentDefinition
    {
        [Export]
        [Name("bar")]
        [BaseDefinition(CodeRemoteContentDefinition.CodeRemoteContentTypeName)]
        internal static ContentTypeDefinition BarContentTypeDefinition;


        [Export]
        [FileExtension(".bar")]
        [ContentType("bar")]
        internal static FileExtensionToContentTypeDefinition BarFileExtensionDefinition;
    }
}
```

Im vorherigen Beispiel wird eine Content-Type-Definition für Dateien, die am Ende erstellt `.bar` Dateierweiterung. Die Content-Type-Definition erhält den Namen "Balken" und **müssen** abgeleitet [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Nach dem Hinzufügen einer Content-Type-Definition, können Sie beim Laden Sie Ihre Client-Erweiterungs der Sprache in der Sprache-Client-Klasse definieren:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Hinzufügen von Unterstützung für LSP Sprache Server erfordert implementieren Ihre eigenen Projektsystem in Visual Studio keine. Kunden können eine einzelne Datei oder einen Ordner in Visual Studio zum Starten der Verwendung von Ihrem Sprachdienst öffnen. In der Tat die Unterstützung für LSP Sprache Servern dient in nur in Ordner/Datei öffnen-Szenarien. Eine benutzerdefinierte Projektsystem implementiert ist, funktionieren einige Funktionen (z. B. Einstellungen) nicht.

## <a name="advanced-features"></a>Erweiterte Funktionen

### <a name="settings"></a>Einstellungen

Unterstützung für benutzerdefinierte Sprache-Server-spezifische Einstellungen für die Preview-Version von LSP-Unterstützung in Visual Studio verfügbar ist, aber es wird noch verbessert wird. Einstellungen gelten nur für was die Language-Server unterstützt und in der Regel zu steuern, wie der Server Sprache Daten ausgibt. Z. B. möglicherweise ein Sprache-Server eine Einstellung für die maximale Anzahl der Fehler gemeldet. Erweiterung Autoren würde einen Standardwert definieren, die von Benutzern für bestimmte Projekte geändert werden kann.

Führen Sie die Schritte unten, um Unterstützung für Einstellungen Ihrer LSP Language-Erweiterung hinzufügen:

1. Hinzufügen einer JSON-Datei (z. B. "MockLanguageExtensionSettings.json") in Ihrem Projekt, das die Einstellungen und Standardwerte enthält. Zum Beispiel:

  ```json
  {
    "foo.maxNumberOfProblems": -1
  }
  ```
2. Klicken Sie mit der rechten Maustaste auf die JSON-Datei, und wählen Sie **Eigenschaften**. Ändern der **erstellen** Aktion aus, um den "Content" und "Include in VSIX" Eigenschaft auf "true".

3. Implementieren Sie ConfigurationSections und Zurückgeben der Liste der Präfixe für die Einstellungen in der JSON-Datei definiert (In Visual Studio Code Dies würde Zuordnen der Konfigurationsabschnittsname in "Package.JSON"):

  ```csharp
  public IEnumerable<string> ConfigurationSections
  {
      get
      {
          yield return "foo";
      }
  }
  ```
4. Fügen Sie dem Projekt eine PKGDEF-Datei (Fügen Sie neue Textdatei hinzu, und ändern Sie die Erweiterung in der PKGDEF). Die Pkgdef-Datei sollte diese Informationen enthalten:

  ```xml
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
  ```

5. Klicken Sie mit der rechten Maustaste auf die PKGDEF-Datei, und wählen Sie **Eigenschaften**. Ändern der **erstellen** Aktion aus, um den "Content" und die Eigenschaft "In VSIX einschließen" auf "true".

6. Öffnen Sie die `source.extension.vsixmanifest` Datei, und fügen Sie ein Medienobjekt in der **Asset** Registerkarte:

  ![edit vspackage asset](media/lsp-add-vspackage-asset.png)

  * **Type**: Microsoft.VisualStudio.VsPackage
  * **Quelle**: Datei im Dateisystem
  * **Pfad**: [Pfad zu der Pkgdef-Datei]

### <a name="user-editing-of-settings-for-a-workspace"></a>Benutzer Bearbeiten der Einstellungen für einen Arbeitsbereich

1. Benutzer öffnet einen Arbeitsbereich mit Dateien, die der Server besitzt.
2. Benutzer fügt eine Datei im Ordner "VS" namens "VSWorkspaceSettings.json" hinzu.
3. Benutzer hinzugefügt der VSWorkspaceSettings.json-Datei für eine Einstellung, die vom Server wird eine Zeile. Zum Beispiel:

  ```json
  {
    "foo.maxNumberOfProblems": 10
  }
  ```
### <a name="enabling-diagnostics-tracing"></a>Aktivieren der Diagnose-Ablaufverfolgung
Diagnose-Ablaufverfolgung kann aktiviert werden, um alle Ausgabenachrichten zwischen Client und Server, die beim Debuggen von Problemen hilfreich sein können.  Um die diagnosenachverfolgung aktiviert werden, führen Sie folgende Schritte aus:

1. Öffnen oder erstellen Sie die Datei mit den Arbeitsbereich "VSWorkspaceSettings.json" (siehe "Benutzer Bearbeiten der Einstellungen für einen Arbeitsbereich").
2. Fügen Sie in den Einstellungen Json-Datei die folgende Zeile hinzu:

```json
{
    "foo.server.trace": "Off"
}
```

Es gibt drei mögliche Werte für die Ausführlichkeit der Ablaufverfolgung:
* "Off": vollständig deaktiviert die Ablaufverfolgung
* "Nachrichten": Ablaufverfolgung aktiviert ist, jedoch nur diejenige Methode und die Antwort-ID werden nachverfolgt.
* "Verbose": Ablaufverfolgung, die eingeschaltet; die gesamte Rpc-Nachricht wird nachverfolgt.

Wenn Ablaufverfolgung aktiviert ist, der Inhalt wird in eine Datei im Verzeichnis "% temp%\VisualStudio\LSP" geschrieben.  Das Protokoll folgt das Namensformat `[LanguageClientName]-[Datetime Stamp].log`.  Ablaufverfolgung kann derzeit nur für Szenarien mit geöffneten Ordner aktiviert werden.  Öffnen eine einzelne Datei zum Aktivieren eines Servers für die Sprache muss sich nicht auf nachverfolgungsunterstützung Diagnose aus.

### <a name="custom-messages"></a>Benutzerdefinierte Meldungen

APIs festliegen zu erleichtern, übergeben von Nachrichten an und Empfangen von Nachrichten vom Server Sprache, die nicht Teil der standardmäßigen Sprache Serverprotokoll sind sind vorhanden. Um benutzerdefinierte Nachrichten zu behandeln, implementieren [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) Schnittstelle in Ihrer Sprache-Client-Klasse. [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Bibliothek wird verwendet, um benutzerdefinierte Nachrichten zwischen der Sprache Client-als auch Sprache übertragen. Da Ihre LSP Client spracherweiterung genau wie andere Visual Studio-Erweiterung ist, können Sie entscheiden zusätzliche Funktionen hinzufügen (die nicht vom LSP unterstützt werden) zu Visual Studio (mit anderen Visual Studio-APIs) in der Erweiterung mithilfe von benutzerdefinierten Nachrichten.

#### <a name="receiving-custom-messages"></a>Benutzerdefinierte Nachrichten empfangen

Um benutzerdefinierte Nachrichten vom Server Sprache zu empfangen, implementieren die [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) Eigenschaft [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) und ein Objekt zurück, das weiß, wie Ihre benutzerdefinierte Nachrichten zu verarbeiten . Beispiel:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public object CustomMessageTarget
    {
        get;
        set;
    }

    public class CustomTarget
    {
        public void OnCustomNotification(JToken arg)
        {
            // Provide logic on what happens OnCustomNotification is called from the language server
        }

        public string OnCustomRequest(string test)
        {
            // Provide logic on what happens OnCustomRequest is called from the language server
        }
    }
}
```

#### <a name="sending-custom-messages"></a>Benutzerdefinierte Meldungen senden

Implementieren Sie zum Senden von benutzerdefinierter Nachrichten an den Server für die Sprache der [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) Methode [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Diese Methode wird aufgerufen, wenn der Language-Server gestartet wurde und zum Empfangen von Nachrichten bereit ist. Ein [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) Objekt als Parameter, die Sie dann zum Senden von Nachrichten mit dem Language Server stets übergeben [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) APIs. Beispiel:

```csharp
internal class MockCustomLanguageClient : MockLanguageClient, ILanguageClientCustomMessage
{
    private JsonRpc customMessageRpc;

    public MockCustomLanguageClient() : base()
    {
        CustomMessageTarget = new CustomTarget();
    }

    public async Task AttachForCustomMessageAsync(JsonRpc rpc)
    {
        await Task.Yield();

        this.customMessageRpc = rpc;
    }

    public async Task SendServerCustomNotification(object arg)
    {
        await this.customMessageRpc.NotifyWithParameterObjectAsync("OnCustomNotification", arg);
    }

    public async Task<string> SendServerCustomMessage(string test)
    {
        return await this.customMessageRpc.InvokeAsync<string>("OnCustomRequest", test);
    }
}
```

### <a name="middle-layer"></a>Mittlere Ebene

In einigen Fällen kann ein Entwickler Erweiterung LSP Nachrichten gesendet und Empfangen von der Language-Server abfangen möchten. Z. B. kann ein Entwickler Erweiterung alter Message-Parameter für eine bestimmte LSP-Nachricht gesendet werden soll, oder vom Server Sprache für eine LSP-Funktion (z. B. Beendigungen) zurückgegebenen Ergebnisse ändern. Wenn dies erforderlich ist, können Erweiterung Entwickler die MiddleLayer-API verwenden, um LSP Nachrichten abzufangen.

Jede LSP-Nachricht besitzt eine eigene Schnittstelle mittleren Ebene für die Abfangfunktion. Um eine bestimmte Nachricht abfangen zu können, erstellen Sie eine Klasse, die die Schnittstelle der mittleren Ebene für diese Nachricht implementiert. Implementieren Sie anschließend die [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) -Schnittstelle in Ihrer Sprache Clientklasse und zurückgeben eine Instanz des Objekts in der [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Eigenschaft. Beispiel:

```csharp
public class MockLanguageClient: ILanguageClient, ILanguageClientCustomMessage
{
    public object MiddleLayer => MiddleLayerProvider.Instance;

    private class MiddleLayerProvider : ILanguageClientWorkspaceSymbolProvider
    {
        internal readonly static MiddleLayerProvider Instance = new MiddleLayerProvider();

        private MiddleLayerProvider()
        {
        }

        public async Task<SymbolInformation[]> RequestWorkspaceSymbols(WorkspaceSymbolParams param, Func<WorkspaceSymbolParams, Task<SymbolInformation[]>> sendRequest)
        {
            // Send along the request as given
            SymbolInformation[] symbols = await sendRequest(param);

            // Only return symbols that are "files"
            return symbols.Where(sym => string.Equals(new Uri(sym.Location.Uri).Scheme, "file", StringComparison.OrdinalIgnoreCase)).ToArray();
        }
    }
}
```

Die mittlere Schicht-Funktion ist noch in der Entwicklungsphase und noch nicht vollständig.

## <a name="sample-lsp-language-server-extension"></a>Beispiel LSP Language-servererweiterung

Quellcode einer Beispiel-Erweiterung mit der LSP-Client-API in Visual Studio finden Sie Beispiele für VSSDK Erweiterbarkeit [LSP Beispiel](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>FAQ

**Ich möchte ein benutzerdefinierte Projektsystem als Ergänzung für meine LSP Language-Server zum Bereitstellen der umfassenderen Unterstützung dieser Funktion in Visual Studio zu erstellen wie ich mich über auf diese Weise?**

Unterstützung für Server LSP-basierte Sprache, in Visual Studio basiert auf der [Feature open Folder](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) und wurde speziell dazu konzipiert, um eine benutzerdefinierte Projektsystem nicht erforderlich. Sie können eigene benutzerdefinierte Projektsystem Anweisungen erstellen [hier](https://github.com/Microsoft/VSProjectSystem), aber einige Funktionen, wie z. B. Einstellungen, funktionieren möglicherweise nicht. Initialisierung Standardlogik für LSP Language Server ist in den stammordnerspeicherort des Ordners, der zurzeit geöffneten wird übergeben, wenn Sie eine benutzerdefinierte Projektsystem verwenden, Sie möglicherweise während der Initialisierung, um sicherzustellen, dass das Language-Server kann benutzerdefinierte Logik bereitstellen müssen ordnungsgemäß gestartet.

**Wie füge ich Debuggerunterstützung hinzu?**

Wir bieten Unterstützung für die [allgemeine Debuggen Protokoll](https://code.visualstudio.com/docs/extensionAPI/api-debugging) in einer zukünftigen Version.

**Wenn bereits eine VS unterstützten Sprachdienst installiert (z. B. JavaScript) vorhanden ist, kann ich noch ein LSP-spracherweiterung Server installieren, die zusätzliche Funktionen (z. B. Linting) bietet?**

Ja, aber nicht alle Funktionen funktioniert ordnungsgemäß. Das eigentliche Ziel für LSP spracherweiterungen-Server ist zum Aktivieren der Language-Dienste, die keine systemeigene Unterstützung von Visual Studio. Sie können Erweiterungen, die zusätzliche Unterstützung, die mit LSP Sprache Servern bieten erstellen, aber einige Features (z. B. IntelliSense) werden nicht benutzerfreundlichkeit. Im Allgemeinen empfehlen wir LSP spracherweiterungen-Server verwendet werden, für die Bereitstellung von neuen Sprache Erfahrungen, vorhandene nicht erweitern.

**Wobei veröffentlichen Sie abgeschlossenen LSP Sprache Server VSIX**

Lesen Sie die Anweisungen Marketplace [hier](walkthrough-publishing-a-visual-studio-extension.md).
