---
title: Hinzufügen einer Erweiterung Sprachserverprotokoll | Microsoft-Dokumentation
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d9b268c0c15ce468ca40a90583c5b7310364c189
ms.sourcegitcommit: 283f2dbce044a18e9f6ac6398f6fc78e074ec1ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2019
ms.locfileid: "65805112"
---
# <a name="add-a-language-server-protocol-extension"></a>Hinzufügen einer Erweiterung Sprachserverprotokoll

Der Language-Server-Protokoll (LSP) ist ein häufig verwendetes Protokoll, in Form von JSON RPC v2. 0 verwendet, um Language Service-Features für Codeeditoren, die verschiedene bereitzustellen. Verwenden das Protokoll, können Entwickler schreiben, ein einzelne Sprache Server Sprachdienst zu Funktionen wie IntelliSense, Fehlerdiagnosen, finden Sie alle Verweise, und So weiter, um verschiedene Code-Editoren, die die LSP unterstützen. In der Vergangenheit können Sprachdienste in Visual Studio hinzugefügt werden, mithilfe von TextMate-Grammatik-Dateien zu grundlegenden Funktionen wie die syntaxhervorhebung oder durch Schreiben von benutzerdefinierten Sprachdienste, die den vollständigen Satz von Visual Studio-Erweiterbarkeits-APIs verwenden, um bereitzustellen umfangreichere Daten. Bei Visual Studio-Unterstützung für LSP besteht eine dritte Option zur Verfügung.

![Server-Protokoll-Sprachdienst in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Sprachserverprotokoll

![Language-Server-protokollimplementierung](media/lsp-implementation.png)

In diesem Artikel wird beschrieben, wie Sie Visual Studio-Erweiterung zu erstellen, die einen LSP-basierte Sprache-Server verwendet, wird. Es wird davon ausgegangen, dass Sie bereits einen Server LSP-basierte Sprache entwickelt haben und nur in Visual Studio integrieren möchten.

Für die Unterstützung in Visual Studio können Language-Servern kommunizieren mit dem Client (Visual Studio) über alle streambasierte Übertragungsmechanismus, z. B.:

* Standard-e/a-streams
* Named pipes
* Sockets (nur TCP)

Die Absicht der LSP und Unterstützung in Visual Studio besteht darin, integrieren Sprachdienste, die nicht Teil von Visual Studio-Produkt sind. Es sollen keine vorhandenen Sprachdienste erweitern (z. B. C#) in Visual Studio. Um vorhandene Sprachen erweitern zu können, finden Sie im Handbuch für den Sprachdienst Erweiterbarkeit (z. B. die ["Roslyn".NET Compiler Platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)).

Weitere Informationen über das Protokoll selbst betrifft, finden Sie in der Dokumentation [hier](https://github.com/Microsoft/language-server-protocol).

Weitere Informationen zum Erstellen eines Beispiel-Language-Servers oder ein vorhandenen Servers für die Sprache in Visual Studio Code integriert finden Sie in der Dokumentation [hier](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Sprachserverprotokoll unterstützte Funktionen

Die folgende Tabelle zeigt, welche LSP-Funktionen in Visual Studio unterstützt werden:

Meldung | Verfügt über Unterstützung in Visual Studio
--- | ---
Initialisieren | ja
initialisiert | ja
Herunterfahren | ja
Beenden | ja
$/cancelRequest | ja
Fenster/showMessage | ja
window/showMessageRequest | ja
window/logMessage | ja
telemetrieereignis / |
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
TextDocument/Vervollständigung | ja
Abschluss/auflösen | ja
textDocument/hover | ja
textDocument/signatureHelp | ja
textDocument/references | ja
textDocument/documentHighlight | ja
textDocument/documentSymbol | ja
textDocument/formatting | ja
textDocument/rangeFormatting | ja
textDocument/onTypeFormatting |
textDocument/definition | ja
textDocument/codeAction | ja
textDocument/codeLens |
codeLens/resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/rename | ja

## <a name="get-started"></a>Erste Schritte

> [!NOTE]
> Beginnend mit Visual Studio 2017 Version 15.8, Unterstützung für das common Language-Server-Protokoll ist in Visual Studio integriert. Wenn Sie LSP-Erweiterungen, die unter Verwendung der Vorschau erstellt haben [Sprache Server Client VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) Version, sie funktioniert nicht mehr nach dem upgrade auf Version 15,8 oder höher. Sie benötigen Sie Folgendes ein, um Ihren LSP Erweiterungen wieder funktionsfähig zu erhalten:
>
> 1. Deinstallieren Sie die Microsoft Visual Studio Server-Protokoll Vorschau VSIX.
>
>    Ab Version 15.8 führen immer Sie ein Upgrade in Visual Studio die Vorschau VSIX automatisch erkannt und entfernt wird.
>
> 2. Aktualisieren Sie den Nuget-Verweis auf die neueste Version von nicht-Vorschau für [LSP Pakete](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Entfernen Sie die Abhängigkeit auf der Microsoft Visual Studio-Sprache-Server-Protokoll Vorschau VSIX im VSIX-Manifest.
>
> 4. Vergewissern Sie sich Ihre VSIX gibt Visual Studio 2017 Version 15.8 Preview 3 als die untere Grenze für das Ziel der Installation.
>
> 5. Neu erstellen und bereitstellen.

### <a name="create-a-vsix-project"></a>Erstellen Sie ein VSIX-Projekt

Um eine Dienst-spracherweiterung, die mit einem LSP-basierte Sprache-Server zu erstellen, stellen Sie zunächst sicher, dass die **Visual Studio-extensionentwicklung** Arbeitsauslastung für die Instanz von Visual Studio installiert.

Als Nächstes erstellen Sie ein neues VSIX-Projekt durch Navigieren zu **Datei** > **neues Projekt** > **Visual C#**   >  **Erweiterbarkeit** > **VSIX-Projekt**:

![Erstellen Sie die Vsix-Projekt](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Language-Server und -Runtime-installation

In der Standardeinstellung enthalten nicht die Erweiterungen zur Unterstützung von LSP-basierte Sprache-Server in Visual Studio erstellt die Language-Server selbst oder die Laufzeiten erforderlich, um sie auszuführen. Entwickler von Erweiterungen sind verantwortlich für die Verteilung der Language-Server und die Laufzeiten erforderlich sind. Es gibt mehrere Möglichkeiten zur Verfügung:

* Language-Server können als Inhaltsdateien in die VSIX-Datei eingebettet werden.
* Erstellen Sie eine MSI-Datei, um das Language-Server zu installieren bzw. Laufzeiten erforderlich.
* Bieten Sie Anweisungen Hinweis Marketplace-Benutzer wie Laufzeiten und Language-Server abgerufen.

### <a name="textmate-grammar-files"></a>TextMate-Grammatik-Dateien

LSP umfasst keine Spezifikation zum Text farbliche Kennzeichnung für Sprachen bereitstellen. Um benutzerdefinierte farbliche Kennzeichnung für Sprachen in Visual Studio zu ermöglichen, können Entwickler von Erweiterungen eine TextMate-Grammatik-Datei verwenden. Um benutzerdefinierte TextMate-Grammatik oder eines Designs Dateien hinzuzufügen, gehen Sie folgendermaßen vor:

1. Erstellen Sie einen Ordner mit dem Namen "Grammatiken" innerhalb der Erweiterung (oder beliebige von Ihnen gewählten Namen sind möglich).

2. In der *Grammatiken* Ordner enthalten  *\*.tmlanguage*,  *\*plist*,  *\*.tmtheme*, oder  *\*JSON* Dateien, die Sie möchten, die farbliche Kennzeichnung von benutzerdefinierten bereitstellen.

   > [!TIP]
   > Ein *.tmtheme* -Datei definiert, wie die Bereiche für Visual Studio-Klassifizierungen (eine benannte Farbe Schlüssel) zugeordnet. Anleitungen können Sie die globale verweisen *.tmtheme* Datei die *% ProgramFiles% (x86) %\Microsoft Visual Studio\\\<Version >\\\<SKU > \Common7\ IDE\CommonExtensions\Microsoft\TextMate\Starterkit\Themesg* Verzeichnis.

3. Erstellen Sie eine *PKGDEF* Datei, und fügen eine Zeile, die etwa wie folgt hinzu:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Mit der rechten Maustaste auf die Dateien, und wählen **Eigenschaften**. Ändern der **erstellen** Aktion aus, um **Content** , und ändern Sie die **Include in VSIX-Datei** Eigenschaft **"true"**.

Nach Abschluss der vorherigen Schritte, eine *Grammatiken* Ordner wird die Paket Installation hinzugefügt Verzeichnis als repositoryquelle mit dem Namen 'MyLang' ("MyLang" ist nur ein Name für Mehrdeutigkeit und können eine beliebige eindeutige Zeichenfolge sein). Alle Grammatiken (*.tmlanguage* Dateien) und Designdateien (*.tmtheme* Dateien) in diesem Verzeichnis als potenziellen übernommen werden, und setzen alle integrierten beiliegenden TextMate Grammatiken. Wenn die Grammatikdatei deklarierten Erweiterungen die Erweiterung der die zu öffnende Datei übereinstimmen, wird in TextMate Schritt.

## <a name="create-a-simple-language-client"></a>Erstellen Sie einen einfache Sprache-client

### <a name="main-interface---ilanguageclientdotnetapimicrosoftvisualstudiolanguageserverclientilanguageclientviewvisualstudiosdk-2017"></a>Hauptfenster der Benutzeroberfläche - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Fügen Sie nach Erstellung des VSIX-Projekts Ihrem Projekt die folgenden NuGet-Pakete hinzu:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Wenn Sie eine Abhängigkeit auf das NuGet-Paket erstellen, nachdem Sie die vorherigen Schritte abgeschlossen, werden die Pakete "newtonsoft.JSON" und StreamJsonRpc ebenfalls dem Projekt hinzugefügt. **Diese Pakete werden nicht aktualisiert werden, es sei denn, Sie sich sicher sind, dass diese neuen Versionen auf die Version von Visual Studio installiert werden, die Ihre Erweiterung als Ziel**. Die Assemblys werden nicht in Ihre VSIX-Datei einbezogen; Stattdessen werden sie aus dem Installationsverzeichnis von Visual Studio übernommen. Verweis auf eine neuere Version der Assemblys als auf dem Computer des Benutzers installiert ist, funktioniert die Erweiterung nicht.

Sie können dann erstellen Sie eine neue Klasse, die implementiert die [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) -Schnittstelle, die die Hauptschnittstelle für die von Sprachclients Verbindungen mit einem LSP-basierte Sprache-Server erforderlich ist.

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
            await StartAsync.InvokeAsync(this, EventArgs.Empty);
        }

        public Task OnServerInitializeFailedAsync(Exception e)
        {
            return Task.CompletedTask;
        }

        public Task OnServerInitializedAsync()
        {
            return Task.CompletedTask;
        }
    }
}
```

Die wichtigsten Methoden, die implementiert werden müssen, sind [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) und [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) wird aufgerufen, wenn Visual Studio die Erweiterung geladen hat und der Language-Server kann jetzt gestartet werden soll. In dieser Methode Sie aufrufen, die ["startasync"](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) Delegat, der sofort zu signalisieren, dass der Language-Server gestartet werden soll, oder Sie können zusätzlichen Logik und rufen Sie ["startasync"](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) später noch mal. **Um den Server für die Sprache zu aktivieren, müssen Sie an einem bestimmten Punkt "startasync" aufrufen.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) ist die Methode, die schließlich aufgerufen durch Aufrufen der ["startasync"](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) delegieren. Sie enthält die Logik zum Starten des Servers für die Sprache und Herstellen der Verbindung. Ein Verbindungsobjekt, die Datenströme für an den Server schreiben und Lesen aus dem Server enthält, muss zurückgegeben werden. Alle hier ausgelösten Ausnahmen abgefangen und Benutzer über eine Infoleiste-Meldung in Visual Studio angezeigt.

### <a name="activation"></a>Aktivierung

Sobald Ihre Clientklasse Sprache implementiert wird, müssen Sie definieren zwei Attribute, dafür zu definieren, wie es in Visual Studio geladen und aktiviert werden:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio verwendet [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework) ihre Erweiterungspunkte zu verwalten. Die [exportieren](/dotnet/api/system.componentmodel.composition.exportattribute) Attribut Visual Studio zeigt an, dass diese Klasse als Erweiterungspunkt übernommen und zum richtigen Zeitpunkt geladen werden soll.

Um MEF verwenden zu können, müssen Sie MEF auch als Ressource im VSIX-Manifest definieren.

Öffnen Sie Ihre VSIX-manifest-Designer, und navigieren Sie zu der **Assets** Registerkarte:

![MEF-Anlage hinzufügen](media/lsp-add-asset.png)

Klicken Sie auf **neu** um ein neues Medienobjekt zu erstellen:

![Definieren von MEF-asset](media/lsp-define-asset.png)

* **Typ**: Microsoft.VisualStudio.MefComponent
* **Quelle**: Ein Projekt in der aktuellen Projektmappe
* **Projekt**: [Ihr Projekt]

### <a name="content-type-definition"></a>Inhaltstypdefinition

Derzeit ist die einzige Möglichkeit zum Laden Ihrer Server-Erweiterungs LSP-basierte Sprache nach Inhaltstyp der Datei ein. D. h. beim Definieren Ihrer Sprache-Client-Klasse (implementiert [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)), müssen Sie definieren die Typen von Dateien, die beim geöffnet ist, führt dazu, dass die Erweiterung zu laden. Wenn keine Dateien, die mit Ihren definierten Inhaltstyp übereinstimmen geöffnet sind, wird die Erweiterung nicht geladen werden.

Dies erfolgt mithilfe eines oder mehrere `ContentTypeDefinition` Klassen:

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

Im vorherigen Beispiel wird eine Content-Type-Definition für Dateien, die auf Enden erstellt *.bar* Dateierweiterung. Die Inhaltstypdefinition erhält den Namen "Bar" und muss von abgeleitet werden [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017).

Nach dem Hinzufügen einer Content-Type-Definition, können Sie beim Laden Ihrer Client-spracherweiterung in der Sprache-Client-Klasse definieren:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Hinzufügen von Unterstützung für die Sprache Server LSP erfordert implementieren Sie Ihre eigenen-Projektsystem in Visual Studio keine. Kunden können eine einzelne Datei oder einen Ordner in Visual Studio zum Einstieg in den Sprachdienst öffnen. In der Tat die Unterstützung für LSP Sprache Server Einsatz konzipiert ist nur in Ordner/Datei öffnen-Szenarien. Wenn eine benutzerdefinierte Projektsystem implementiert wird, funktioniert einige Funktionen (z. B. Einstellungen) nicht.

## <a name="advanced-features"></a>Erweiterte Features

### <a name="settings"></a>Einstellungen

Unterstützung für benutzerdefinierte Sprache-Server-spezifische Einstellungen ist verfügbar, aber noch verbessert werden kann. Einstellungen gelten, was die Language-Server unterstützt, und in der Regel zu steuern, wie der Server für die Sprache Daten ausgibt. Z. B. möglicherweise ein Sprache-Server eine Einstellung für die maximale Anzahl der gemeldeten Fehler. Erweiterungsautoren würde einen Standardwert definieren, die von Benutzern für bestimmte Projekte geändert werden können.

Führen Sie diese Schritte unten aus, um Unterstützung für Einstellungen für die LSP Language Service-Erweiterung hinzufügen:

1. Fügen Sie eine JSON-Datei (z. B. *MockLanguageExtensionSettings.json*) zu Ihrem Projekt, das die Einstellungen und Standardwerte enthält. Zum Beispiel:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Mit der rechten Maustaste auf die JSON-Datei, und wählen Sie **Eigenschaften**. Ändern der **erstellen** Aktion aus, um den "Content" und "Include in VSIX-Datei"-Eigenschaft auf **"true"**.

3. Implementieren von ConfigurationSections und Zurückgeben der Liste der Präfixe für die Einstellungen, die in der JSON-Datei definiert (In Visual Studio Code, dies würde zugeordnet, der Name des Konfigurationsabschnitts in "Package.JSON"):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Fügen Sie dem Projekt eine PKGDEF-Datei (neuen Text-Datei hinzufügen und ändern Sie die Dateierweiterung in PKGDEF). Die Pkgdef-Datei sollte diese Informationen enthalten:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Beispiel:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Klicken Sie mit der rechten Maustaste auf die PKGDEF-Datei, und wählen Sie **Eigenschaften**. Ändern der **erstellen** Aktion aus, um **Content** und **Include in VSIX-Datei** Eigenschaft **"true"**.

6. Öffnen Sie die *"Source.Extension.vsixmanifest"* -Datei und fügen Sie ein Medienobjekt in der **Asset** Registerkarte:

   ![Bearbeiten von Vspackage-asset](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft.VisualStudio.VsPackage
   * **Quelle**: Datei im Dateisystem
   * **Pfad**: [Pfad zu Ihrem *PKGDEF* Datei]

### <a name="user-editing-of-settings-for-a-workspace"></a>Benutzer Bearbeiten der Einstellungen für einen Arbeitsbereich

1. Benutzer öffnet einen Arbeitsbereich mit den Dateien, die der Server besitzt.
2. Hinzufügen eine Datei in die *.vs* Ordner mit dem Namen *VSWorkspaceSettings.json*.
3. Hinzufügen eine Zeile, um die *VSWorkspaceSettings.json* -Datei für eine Einstellung, die der Server bietet. Zum Beispiel:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Aktivieren der Diagnose-Ablaufverfolgung

Diagnose-Ablaufverfolgung kann aktiviert werden, um alle Meldungen zwischen Client und Server, der beim Debuggen von Problemen hilfreich sein kann. Um die diagnoseablaufverfolgung zu aktivieren, führen Sie folgende Schritte aus:

1. Öffnen oder erstellen Sie die Datei mit den Arbeitsbereich *VSWorkspaceSettings.json* (siehe "Benutzer Bearbeiten der Einstellungen für einen Arbeitsbereich").
2. Fügen Sie in der JSON-Datei die folgende Zeile hinzu:

```json
{
    "foo.trace.server": "Off"
}
```

Es gibt drei mögliche Werte für die Ausführlichkeit der Ablaufverfolgung:

* "Off": Ablaufverfolgung vollständig deaktiviert
* "Messages": Ablaufverfolgung aktiviert ist, aber nur Name und die Antwort-ID nachverfolgt werden.
* "Verbose":-Ablaufverfolgung aktiviert; die gesamte RPC-Nachricht wird nachverfolgt.

Wenn Ablaufverfolgung aktiviert ist, auf dem Inhalt in eine Datei im richtet die *%temp%\VisualStudio\LSP* Verzeichnis. Das Protokoll folgt das Namensformat *[LanguageClientName]-[Datums-/ Zeitstempel] .log*. Derzeit kann die Ablaufverfolgung nur für Szenarien mit "Ordner öffnen" aktiviert werden. Öffnen eine einzelne Datei zum Aktivieren eines Servers für die Sprache muss sich nicht auf Diagnose nachverfolgungsunterstützung aus.

### <a name="custom-messages"></a>Benutzerdefinierte Meldungen

Es gibt zu erleichtern, übergeben von Nachrichten an und Empfangen von Nachrichten vom Server Sprache, die nicht Teil der standard Sprachserverprotokoll sind APIs vorhanden. Behandeln Sie benutzerdefinierte Meldungen implementieren [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) Schnittstelle in Ihrer Sprache-Client-Klasse. [Visual Studio-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) Bibliothek wird verwendet, um benutzerdefinierte Nachrichten zwischen Ihrem Sprache Client- und Sprache übertragen. Da Ihre LSP-spracherweiterung Client genau wie alle anderen Visual Studio-Erweiterung ist, können Sie zusätzliche Funktionen hinzufügen (die nicht vom LSP unterstützt werden) zu Visual Studio (mit anderen Visual Studio-APIs) in Ihrer Erweiterung mithilfe von benutzerdefinierten Nachrichten.

#### <a name="receive-custom-messages"></a>Benutzerdefinierte Meldungen erhalten

Um benutzerdefinierte Nachrichten vom Server Sprache zu empfangen, implementieren die [CustomMessageTarget](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) Eigenschaft [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) und ein Objekt zurück, das weiß, wie Sie Ihren benutzerdefinierten Nachrichten behandeln . Das Beispiel unten:

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

#### <a name="send-custom-messages"></a>Senden Sie benutzerdefinierte Meldungen

Implementieren Sie zum Senden von benutzerdefinierter Nachrichten an den Server für die Sprache der [AttachForCustomMessageAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) Methode [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Diese Methode wird aufgerufen, wenn der Language-Server gestartet wurde und nun an Meldungen empfangen kann. Ein [JsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) Objekt als Parameter, die Sie dann zum Senden von Nachrichten mit dem Language Server behalten übergeben [VS-StreamJsonRpc](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) APIs. Das Beispiel unten:

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

### <a name="middle-layer"></a>Mittlere Schicht

Manchmal kann ein Entwickler für die Erweiterung LSP Nachrichten gesendet und empfangen, die vom Server Sprache abfangen möchten. Z. B. kann ein Entwickler für die Erweiterung zum Ändern der Meldungsparameter für eine bestimmte LSP-Nachricht gesendet werden soll, oder ändern die Sprache für vom Server eine LSP-Funktion (z. B. vervollständigungen) zurückgegebenen Ergebnisse. Wenn dies erforderlich ist, können Entwickler von Erweiterungen der MiddleLayer-API verwenden, um LSP Nachrichten abzufangen.

Jede Nachricht LSP verfügt über eine eigene Benutzeroberfläche für die mittlere Schicht für die Abfangfunktion. Um eine bestimmte Nachricht abzufangen zu können, erstellen Sie eine Klasse, die für diese Nachricht die mittlere Schicht-Schnittstelle implementiert. Implementieren Sie anschließend die [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) Schnittstelle in Ihrer Sprache-Client-Klasse und zurückgeben eine Instanz des Objekts in der [MiddleLayer](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) Eigenschaft. Das Beispiel unten:

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

Die mittlere Schicht-Funktion ist noch in Entwicklung und nicht noch vollständig.

## <a name="sample-lsp-language-server-extension"></a>Server-Erweiterung der Sprache des Beispiel-LSP

Den Quellcode einer Beispiel-Erweiterung, die mithilfe der LSP-Client-API in Visual Studio finden Sie unter VSSDK-Erweiterbarkeit – Beispiele [LSP Beispiel](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>FAQ

**Ich würde gerne, erstellen Sie eine benutzerdefinierte Projektsystem als Ergänzung für meinen Server LSP Sprache, um umfangreichere Unterstützung dieser Funktion in Visual Studio bieten wie Stelle ich Informationen zu tun?**

Unterstützung für Server LSP-basierte Sprache, in Visual Studio basiert auf der [open Folder-Feature](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) und ist für eine benutzerdefinierte Projektsystem nicht erforderlich. Sie können eigene benutzerdefinierte Projektsystem Anweisungen erstellen [hier](https://github.com/Microsoft/VSProjectSystem), aber einige Funktionen, z. B. Einstellungen, funktionieren nicht. Die Standardlogik für die Initialisierung für LSP Language-Server wird im Ordner Stamm des Ordners, die gerade geöffnet wird, übergeben werden, sodass, wenn Sie eine benutzerdefinierte Projektsystem verwenden, Sie möglicherweise während der Initialisierung, um sicherzustellen, dass Ihre Sprache-Server kann benutzerdefinierte Logik bereitzustellen müssen ordnungsgemäß gestartet.

**Wie füge ich den Debugger-Support?**

Es bietet Unterstützung für die [allgemeine Debuggen Protokoll](https://code.visualstudio.com/docs/extensionAPI/api-debugging) in einer zukünftigen Version.

**Wenn bereits ein Visual Studio unterstützten Sprachdienst installiert (z. B. JavaScript) vorhanden ist, kann ich noch ein LSP-spracherweiterung Server installieren, die zusätzliche Features (z. B. "Linting) bietet?**

Ja, aber nicht alle Funktionen funktioniert ordnungsgemäß. Das ultimative Ziel für die Server-spracherweiterungen LSP werden Sprachdienste, die keine systemeigene Unterstützung durch Visual Studio zu aktivieren. Sie können Erweiterungen, die bieten zusätzliche Unterstützung, die mit LSP Sprache Servern erstellen, aber einige Funktionen (z. B. IntelliSense) werden keine reibungslos funktionierende Umgebung. Im Allgemeinen wird empfohlen, dass LSP spracherweiterungen-Server verwendet werden, für die Bereitstellung neuer Language-Funktionen, die nicht vorhandene zu erweitern.

**In denen veröffentliche ich meinen abgeschlossenen LSP Sprache Servers VSIX?**

Lesen Sie die Marketplace-Anweisungen [hier](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Siehe auch

- [Hinzufügen von Visual Studio-Editor-Unterstützung für andere Sprachen](../ide/adding-visual-studio-editor-support-for-other-languages.md)