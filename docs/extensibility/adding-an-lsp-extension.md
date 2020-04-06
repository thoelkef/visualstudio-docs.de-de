---
title: Hinzufügen einer Language Server-Protokollerweiterung | Microsoft Docs
ms.date: 11/14/2017
ms.topic: conceptual
ms.assetid: 52f12785-1c51-4c2c-8228-c8e10316cd83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ef2093915538f09f425fc961420c4a3078043c91
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740229"
---
# <a name="add-a-language-server-protocol-extension"></a>Hinzufügen der Sprachserverprotokollerweiterung

Das Language Server Protocol (LSP) ist ein gängiges Protokoll in Form von JSON RPC v2.0, das verwendet wird, um verschiedenen Code-Editoren Sprachdienstfunktionen zur Verfügung zu stellen. Mithilfe des Protokolls können Entwickler einen einzelnen Sprachserver schreiben, um Sprachdienstfunktionen wie IntelliSense, Fehlerdiagnose, Suchen aller Verweise usw. für verschiedene Codeeditoren bereitzustellen, die den LSP unterstützen. Traditionell können Sprachdienste in Visual Studio hinzugefügt werden, indem TextMate-Grammatikdateien verwendet werden, um grundlegende Funktionen wie Syntaxhervorhebung bereitzustellen oder benutzerdefinierte Sprachdienste zu schreiben, die den vollständigen Satz von Visual Studio-Erweiterbarkeits-APIs verwenden, um umfangreichere Daten bereitzustellen. Mit Visual Studio-Unterstützung für LSP gibt es eine dritte Option.

![Sprachserverprotokolldienst in Visual Studio](media/lsp-service-in-VS.png)

## <a name="language-server-protocol"></a>Sprachserverprotokoll

![Implementierung des Sprachserverprotokolls](media/lsp-implementation.png)

In diesem Artikel wird beschrieben, wie Sie eine Visual Studio-Erweiterung erstellen, die einen LSP-basierten Sprachserver verwendet. Es wird davon ausgegangen, dass Sie bereits einen LSP-basierten Sprachserver entwickelt haben und ihn nur in Visual Studio integrieren möchten.

Für die Unterstützung in Visual Studio können Sprachserver mit dem Client (Visual Studio) über einen beliebigen streambasierten Übertragungsmechanismus kommunizieren, z. B.:

* Standard-Eingangs-/Ausgangsströme
* Named Pipes
* Sockets (nur TCP)

Die Absicht des LSP und die Unterstützung dafür in Visual Studio besteht darin, Sprachdienste zu onginieren, die nicht Teil des Visual Studio-Produkts sind. Es ist nicht beabsichtigt, vorhandene Sprachdienste (z. B. C-Dienste) in Visual Studio zu erweitern. Um vorhandene Sprachen zu erweitern, lesen Sie das Erweiterbarkeitshandbuch des Sprachdienstes (z. B. die ["Roslyn" .NET Compiler platform](../extensibility/dotnet-compiler-platform-roslyn-extensibility.md)) oder finden Sie unter [Erweitern des Editors und der Sprachdienste](../extensibility/extending-the-editor-and-language-services.md).

Weitere Informationen zum Protokoll selbst finden Sie in der Dokumentation [hier](https://github.com/Microsoft/language-server-protocol).

Weitere Informationen zum Erstellen eines Beispielsprachenservers oder zum Integrieren eines vorhandenen Sprachservers in Visual Studio Code finden Sie in der Dokumentation [hier](https://code.visualstudio.com/docs/extensions/example-language-server).

## <a name="language-server-protocol-supported-features"></a>Language Server Protocol unterstützte Funktionen

Die folgenden Tabellen zeigen, welche LSP-Features in Visual Studio unterstützt werden:

`Message` | Unterstützung in Visual Studio
--- | ---
initialisieren | ja
initialisiert | ja
shutdown | ja
exit | ja
s/cancelRequest | ja
fenster/showMessage | ja
fenster/showMessageRequest | ja
fenster/logMessage | ja
Telemetrie/Ereignis |
Client/registerFähigkeit |
Client/unregisterFähigkeit |
workspace/didChangeConfiguration | ja
workspace/didChangeWatchedFiles | ja
Arbeitsbereich/Symbol | ja
workspace/executeCommand | ja
arbeitsbereich/applyBearbeiten | ja
textDocument/publishDiagnose | ja
textDocument/didOpen | ja
textDocument/didChange | ja
textDocument/willSave |
textDocument/willSaveWaitUntil |
textDocument/didSave | ja
textDocument/didClose | ja
textDokument/Vervollständigung | ja
Abschluss/Auflösung | ja
textDocument/hover | ja
textDocument/signatureHilfe | ja
textDokument/Referenzen | ja
textDocument/documentHighlight | ja
textDocument/documentSymbol | ja
textDocument/Formatierung | ja
textDocument/rangeFormatierung | ja
textDocument/onTypeFormatting |
textDocument/Definition | ja
textDocument/codeAction | ja
textDocument/codeLens |
codeLens/Resolve |
textDocument/documentLink |
documentLink/resolve |
textDocument/Umbenennung | ja

## <a name="get-started"></a>Erste Schritte

> [!NOTE]
> Ab Visual Studio 2017 Version 15.8 ist die Unterstützung für das gemeinsame Language Server-Protokoll in Visual Studio integriert. Wenn Sie LSP-Erweiterungen mit der Vorschauversion [language Server Client VSIX](https://marketplace.visualstudio.com/items?itemName=vsext.LanguageServerClientPreview) erstellt haben, funktionieren sie nach dem Upgrade auf Version 15.8 oder höher nicht mehr. Sie müssen folgendes tun, damit Ihre LSP-Erweiterungen wieder funktionieren:
>
> 1. Deinstallieren Sie die Microsoft Visual Studio Language Server Protocol Preview VSIX.
>
>    Ab Version 15.8 wird jedes Mal, wenn Sie ein Upgrade in Visual Studio durchführen, die Vorschau-VSIX automatisch erkannt und entfernt.
>
> 2. Aktualisieren Sie Ihren Nuget-Verweis auf die neueste Nicht-Vorschau-Version für [LSP-Pakete](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client).
>
> 3. Entfernen Sie die Abhängigkeit von Microsoft Visual Studio Language Server Protocol Preview VSIX in Ihrem VSIX-Manifest.
>
> 4. Stellen Sie sicher, dass Ihr VSIX Visual Studio 2017 Version 15.8 Preview 3 als untere Grenze für das Installationsziel angibt.
>
> 5. Führen Sie die Neuerstellung und dann die erneute Bereitstellung durch.

### <a name="create-a-vsix-project"></a>Erstellen eines VSIX-Projekts

Um eine Sprachdiensterweiterung mit einem LSP-basierten Sprachserver zu erstellen, stellen Sie zunächst sicher, dass Die **Visual Studio-Erweiterungsentwicklungsarbeitsauslastung** für Ihre VS-Instanz installiert ist.

Erstellen Sie als Nächstes ein neues VSIX-Projekt, indem Sie zu **File** > **New Project** > **Visual C-Extensibility** > **Extensibility** > **VSIX Project**navigieren:

![Vsix-Projekt erstellen](media/lsp-vsix-project.png)

### <a name="language-server-and-runtime-installation"></a>Sprachserver und Laufzeitinstallation

Standardmäßig enthalten die Erweiterungen, die zur Unterstützung von LSP-basierten Sprachservern in Visual Studio erstellt wurden, weder die Sprachserver selbst noch die Laufzeiten, die für ihre Ausführung erforderlich sind. Erweiterungsentwickler sind für die Verteilung der Sprachserver und der erforderlichen Laufzeiten verantwortlich. Es gibt mehrere Möglichkeiten, dies zu tun:

* Sprachserver können als Inhaltsdateien in die VSIX eingebettet werden.
* Erstellen Sie eine MSI, um den Sprachserver und/oder die erforderlichen Laufzeiten zu installieren.
* Geben Sie auf Marketplace Anweisungen an, in denen Sie Benutzer darüber informieren, wie Laufzeiten und Sprachserver erhalten werden.

### <a name="textmate-grammar-files"></a>TextMate-Grammatikdateien

Der LSP enthält keine Spezifikation, wie Textfarben für Sprachen bereitzustellen sind. Um eine benutzerdefinierte Farbgebung für Sprachen in Visual Studio bereitzustellen, können Erweiterungsentwickler eine TextMate-Grammatikdatei verwenden. Gehen Sie folgendzuunter Schritte vor, um benutzerdefinierte TextMate-Grammatik- oder Designdateien hinzuzufügen:

1. Erstellen Sie einen Ordner mit dem Namen "Grammars" in Ihrer Erweiterung (oder es kann sein, welcher Name Sie wählen).

2. Fügen Sie im Ordner *Grammatiken* * \*alle .tmlanguage*, * \*.plist*, * \*.tmtheme*oder * \*.json-Dateien* ein, die eine benutzerdefinierte Farbgebung bereitstellen möchten.

   > [!TIP]
   > Eine *.tmtheme-Datei* definiert, wie die Bereiche Visual Studio-Klassifikationen (benannte Farbschlüssel) zugeordnet werden. Zur Anleitung können Sie auf die globale *.tmtheme-Datei* im Verzeichnis *%ProgramFiles(x86)%-Microsoft Visual Studio\\\<>SKU-version \\ \<>,Common7-IDE-CommonExtensions-Microsoft-TextMate-Starterkit-Themesg-Verzeichnis* verweisen.

3. Erstellen Sie eine *.pkgdef-Datei,* und fügen Sie eine Zeile ähnlich der vorliegenden hinzu:

    ```
    [$RootKey$\TextMate\Repositories]
    "MyLang"="$PackageFolder$\Grammars"
    ```

4. Klicken Sie mit der rechten Maustaste auf die Dateien und wählen Sie **Eigenschaften**aus. Ändern Sie die **Buildaktion** in **Inhalt,** und ändern Sie die **Include in VSIX-Eigenschaft** in **true**.

Nach Abschluss der vorherigen Schritte wird dem Installationsverzeichnis des Pakets ein *Grammatikordner* als Repository-Quelle mit dem Namen "MyLang" hinzugefügt ("MyLang" ist nur ein Name für Diedbiguation und kann eine beliebige eindeutige Zeichenfolge sein). Alle Grammatiken (*.tmlanguage* dateien) und Theme-Dateien (*.tmtheme* dateien) in diesem Verzeichnis werden als Potenziale aufgenommen und sie ersetzt die eingebauten Grammatiken mit TextMate zur Verfügung gestellt. Wenn die deklarierten Erweiterungen der Grammatikdatei mit der Erweiterung der geöffneten Datei übereinstimmen, tritt TextMate ein.

## <a name="create-a-simple-language-client"></a>Erstellen eines einfachen Sprachclients

### <a name="main-interface---ilanguageclient"></a>Hauptschnittstelle - [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)

Fügen Sie nach dem Erstellen Ihres VSIX-Projekts das folgende NuGet-Paket zu Ihrem Projekt hinzu:

* [Microsoft.VisualStudio.LanguageServer.Client](https://www.nuget.org/packages/Microsoft.VisualStudio.LanguageServer.Client)

> [!NOTE]
> Wenn Sie nach Abschluss der vorherigen Schritte eine Abhängigkeit vom NuGet-Paket übernehmen, werden auch die Pakete Newtonsoft.Json und StreamJsonRpc zu Ihrem Projekt hinzugefügt. **Aktualisieren Sie diese Pakete nur, wenn Sie sicher sind, dass diese neuen Versionen auf der Version von Visual Studio installiert werden, auf die Ihre Erweiterung abzielt.** Die Assemblys werden nicht in Ihrem VSIX enthalten sein. Stattdessen werden sie aus dem Visual Studio-Installationsverzeichnis abgeholt. Wenn Sie auf eine neuere Version der Assemblys verweisen, als auf dem Computer eines Benutzers installiert ist, funktioniert die Erweiterung nicht.

Sie können dann eine neue Klasse erstellen, die die [ILanguageClient-Schnittstelle](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017) implementiert, die die Hauptschnittstelle ist, die für Sprachclients benötigt wird, die eine Verbindung zu einem LSP-basierten Sprachserver herstellen.

Beispiel:

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

Die wichtigsten Methoden, die implementiert werden müssen, sind [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) und [ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017). [OnLoadedAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.onloadedasync?view=visualstudiosdk-2017) wird aufgerufen, wenn Visual Studio Ihre Erweiterung geladen hat und Ihr Sprachserver gestartet werden kann. Bei dieser Methode können Sie den [StartAsync-Delegaten](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) sofort aufrufen, um zu signalisieren, dass der Sprachserver gestartet werden soll, oder Sie können zusätzliche Logik verwenden und [StartAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) später aufrufen. **Um Ihren Sprachserver zu aktivieren, müssen Sie StartAsync zu einem bestimmten Zeitpunkt aufrufen.**

[ActivateAsync](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.activateasync?view=visualstudiosdk-2017) ist die Methode, die schließlich durch Aufrufen des [StartAsync-Delegaten](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient.startasync?view=visualstudiosdk-2017) aufgerufen wird. Es enthält die Logik, um den Sprachserver zu starten und eine Verbindung zu ihm herzustellen. Ein Verbindungsobjekt, das Streams zum Schreiben an den Server und zum Lesen vom Server enthält, muss zurückgegeben werden. Alle hier ausgelösten Ausnahmen werden abgefangen und dem Benutzer über eine InfoBar-Nachricht in Visual Studio angezeigt.

### <a name="activation"></a>Aktivierung

Sobald Ihre Sprachclientklasse implementiert ist, müssen Sie zwei Attribute definieren, um zu definieren, wie sie in Visual Studio geladen und aktiviert wird:

```csharp
  [Export(typeof(ILanguageClient))]
  [ContentType("bar")]
```

### <a name="mef"></a>MEF

Visual Studio verwendet [MEF](https://github.com/Microsoft/vs-mef/blob/master/doc/index.md) (Managed Extensibility Framework), um seine Erweiterbarkeitspunkte zu verwalten. Das [Exportattribut](/dotnet/api/system.componentmodel.composition.exportattribute) gibt Visual Studio an, dass diese Klasse als Erweiterungspunkt aufgenommen und zum richtigen Zeitpunkt geladen werden soll.

Um MEF verwenden zu können, müssen Sie MEF auch als Asset im VSIX-Manifest definieren.

Öffnen Sie Ihren VSIX-Manifest-Designer, und navigieren Sie zur Registerkarte **Assets:**

![MEF-Asset hinzufügen](media/lsp-add-asset.png)

Klicken Sie auf **Neu,** um ein neues Asset zu erstellen:

![MEF-Asset definieren](media/lsp-define-asset.png)

* **Typ**: Microsoft.VisualStudio.MefComponent
* **Quelle**: Ein Projekt in der aktuellen Projektmappe
* **Projekt**: [Ihr Projekt]

### <a name="content-type-definition"></a>Inhaltstypdefinition

Derzeit ist die einzige Möglichkeit, Ihre LSP-basierte Sprachservererweiterung zu laden, nach Dateiinhaltstyp. Das heißt, wenn Sie Ihre Sprachclientklasse definieren (die [ILanguageClient](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclient?view=visualstudiosdk-2017)implementiert), müssen Sie die Dateitypen definieren, die beim Öffnen dazu führen, dass die Erweiterung geladen wird. Wenn keine Dateien geöffnet werden, die ihrem definierten Inhaltstyp entsprechen, wird die Erweiterung nicht geladen.

Dies geschieht durch Definieren `ContentTypeDefinition` einer oder mehreren Klassen:

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

Im vorherigen Beispiel wird eine Inhaltstypdefinition für Dateien erstellt, die in der *Dateierweiterung .bar* enden. Die Inhaltstypdefinition erhält den Namen "bar" und muss von [CodeRemoteContentTypeName](/dotnet/api/microsoft.visualstudio.languageserver.client.coderemotecontentdefinition.coderemotecontenttypename?view=visualstudiosdk-2017)ableiten.

Nach dem Hinzufügen einer Inhaltstypdefinition können Sie dann definieren, wann die Sprachclienterweiterung in der Sprachclientklasse geladen werden soll:

```csharp
    [ContentType("bar")]
    [Export(typeof(ILanguageClient))]
    public class BarLanguageClient : ILanguageClient
    {
    }
```

Für das Hinzufügen von Unterstützung für LSP-Sprachserver ist es nicht erforderlich, ein eigenes Projektsystem in Visual Studio zu implementieren. Kunden können eine einzelne Datei oder einen Ordner in Visual Studio öffnen, um ihren Sprachdienst zu verwenden. Tatsächlich ist die Unterstützung für LSP-Sprachserver nur in offenen Ordner-/Dateiszenarien konzipiert. Wenn ein benutzerdefiniertes Projektsystem implementiert ist, funktionieren einige Features (z. B. Einstellungen) nicht.

## <a name="advanced-features"></a>Erweiterte Funktionen

### <a name="settings"></a>Einstellungen

Unterstützung für benutzerdefinierte sprachserverspezifische Einstellungen ist verfügbar, wird jedoch noch verbessert. Die Einstellungen sind spezifisch für die Unterstützung des Sprachservers und steuern in der Regel, wie der Sprachserver Daten ausgibt. Beispielsweise kann ein Sprachserver eine Einstellung für die maximale Anzahl der gemeldeten Fehler haben. Erweiterungsautoren würden einen Standardwert definieren, der von Benutzern für bestimmte Projekte geändert werden kann.

Führen Sie die folgenden Schritte aus, um Unterstützung für Einstellungen zu Ihrer LSP-Sprachdiensterweiterung hinzuzufügen:

1. Fügen Sie Ihrem Projekt eine JSON-Datei (z. B. *MockLanguageExtensionSettings.json*) hinzu, die die Einstellungen und deren Standardwerte enthält. Beispiel:

    ```json
    {
        "foo.maxNumberOfProblems": -1
    }
    ```

2. Klicken Sie mit der rechten Maustaste auf die JSON-Datei und wählen Sie **Eigenschaften**aus. Ändern Sie die **Buildaktion** in "Inhalt" und die Eigenschaft "In VSIX einschließen" in **true**.

3. Implementieren Sie ConfigurationSections, und geben Sie die Liste der Präfixe für die in der JSON-Datei definierten Einstellungen zurück (in Visual Studio Code würde dies dem Konfigurationsabschnittsnamen in package.json zugeordnet):

    ```csharp
    public IEnumerable<string> ConfigurationSections
    {
        get
        {
            yield return "foo";
        }
    }
    ```

4. Fügen Sie dem Projekt eine .pkgdef-Datei hinzu (fügen Sie eine neue Textdatei hinzu und ändern Sie die Dateierweiterung in .pkgdef). Die Datei pkgdef sollte folgende Informationen enthalten:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\[settings-name]]
    @="$PackageFolder$\[settings-file-name].json"
    ```

    Beispiel:

    ```
    [$RootKey$\OpenFolder\Settings\VSWorkspaceSettings\MockLanguageExtension]
    @="$PackageFolder$\MockLanguageExtensionSettings.json"
    ```

5. Klicken Sie mit der rechten Maustaste auf die .pkgdef-Datei und wählen Sie **Eigenschaften**aus. Ändern Sie die **Buildaktion** in **Inhalt** und die **Eigenschaft In VSIX einschließen** in **true**.

6. Öffnen Sie die Datei *source.extension.vsixmanifest,* und fügen Sie ein Asset auf der Registerkarte **Asset** hinzu:

   ![Bearbeiten von vspackage-Asset](media/lsp-add-vspackage-asset.png)

   * **Typ**: Microsoft.VisualStudio.VsPackage
   * **Quelle**: Datei auf Dateisystem
   * **Pfad**: [Pfad zu Ihrer *.pkgdef-Datei]*

### <a name="user-editing-of-settings-for-a-workspace"></a>Benutzerbearbeitung von Einstellungen für einen Arbeitsbereich

1. Der Benutzer öffnet einen Arbeitsbereich, der Dateien enthält, die Ihr Server besitzt.
2. Der Benutzer fügt eine Datei im *.vs-Ordner* VS vs mit dem Namen *VSWorkspaceSettings.json*hinzu.
3. Der Benutzer fügt der Datei *VSWorkspaceSettings.json* eine Zeile für eine Einstellung hinzu, die der Server bereitstellt. Beispiel:

    ```json
    {
        "foo.maxNumberOfProblems": 10
    }
    ```

### <a name="enable-diagnostics-tracing"></a>Aktivieren der Diagnoseablaufverfolgung

Die Diagnoseablaufverfolgung kann aktiviert werden, um alle Nachrichten zwischen Client und Server auszugeben, was beim Debuggen von Problemen nützlich sein kann. Gehen Sie wie folgt vor, um die Diagnoseablaufverfolgung zu aktivieren:

1. Öffnen oder erstellen Sie die Arbeitsbereichseinstellungsdatei *VSWorkspaceSettings.json* (siehe "Benutzerbearbeitung von Einstellungen für einen Arbeitsbereich").
2. Fügen Sie die folgende Zeile in der Json-Datei den Einstellungen hinzu:

```json
{
    "foo.trace.server": "Off"
}
```

Es gibt drei mögliche Werte für die Spurausführlichkeit:

* "Aus": Ablaufverfolgung komplett deaktiviert
* "Nachrichten": Die Ablaufverfolgung aktiviert ist, aber nur der Methodenname und die Antwort-ID werden nachverfolgt.
* "Verbose": Ablaufverfolgung aktiviert; die gesamte rPC-Nachricht wird nachverfolgt.

Wenn die Ablaufverfolgung aktiviert ist, wird der Inhalt in eine Datei im Verzeichnis *%temp%-VisualStudio-LSP* geschrieben. Das Protokoll folgt dem Namensformat *[LanguageClientName]-[Datetime Stamp].log*. Derzeit kann die Ablaufverfolgung nur für offene Ordnerszenarien aktiviert werden. Das Öffnen einer einzelnen Datei zum Aktivieren eines Sprachservers bietet keine Unterstützung für die Diagnoseablaufverfolgung.

### <a name="custom-messages"></a>Benutzerdefinierte Nachrichten

Es gibt APIs, um das Weitersenden von Nachrichten an den Sprachserver, die nicht Teil des Standardmäßigen Language Server-Protokolls sind, zu erleichtern und nachrichten vom Sprachserver zu empfangen. Implementieren Sie die [ILanguageClientCustomMessage-Schnittstelle](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) in Ihrer Sprachclientklasse, um benutzerdefinierte Nachrichten zu verarbeiten. [Die VS-StreamJsonRpc-Bibliothek](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) wird verwendet, um benutzerdefinierte Nachrichten zwischen Ihrem Sprachclient und dem Sprachserver zu übertragen. Da Ihre LSP-Sprachclienterweiterung wie jede andere Visual Studio-Erweiterung ist, können Sie Visual Studio zusätzliche Features (die vom LSP nicht unterstützt werden) in Ihrer Erweiterung über benutzerdefinierte Nachrichten hinzufügen (die vom LSP nicht unterstützt werden).

#### <a name="receive-custom-messages"></a>Empfangen von benutzerdefinierten Nachrichten

Um benutzerdefinierte Nachrichten vom Sprachserver zu empfangen, implementieren Sie die [CustomMessageTarget-Eigenschaft](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.custommessagetarget?view=visualstudiosdk-2017) für [ILanguageClientCustomMessage,](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) und geben Sie ein Objekt zurück, das weiß, wie Sie Ihre benutzerdefinierten Nachrichten verarbeiten. Beispiel unten:

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

#### <a name="send-custom-messages"></a>Senden benutzerdefinierter Nachrichten

Um benutzerdefinierte Nachrichten an den Sprachserver zu senden, implementieren Sie die [AttachForCustomMessageAsync-Methode](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.attachforcustommessageasync?view=visualstudiosdk-2017) für [ILanguageClientCustomMessage](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017). Diese Methode wird aufgerufen, wenn der Sprachserver gestartet wird, und ist bereit, Nachrichten zu empfangen. Ein [JsonRpc-Objekt](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/src/StreamJsonRpc/JsonRpc.cs) wird als Parameter übergeben, den Sie dann behalten können, um Nachrichten mithilfe von [VS-StreamJsonRpc-APIs](https://github.com/Microsoft/vs-streamjsonrpc/blob/master/doc/index.md) an den Sprachserver zu senden. Beispiel unten:

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

Manchmal möchte ein Erweiterungsentwickler möglicherweise LSP-Nachrichten abfangen, die an den Sprachserver gesendet und vom Sprachserver empfangen werden. Beispielsweise kann ein Erweiterungsentwickler den Nachrichtenparameter ändern, der für eine bestimmte LSP-Nachricht gesendet wird, oder die Ergebnisse ändern, die vom Sprachserver für ein LSP-Feature (z. B. Vervollständigungen) zurückgegeben werden. Wenn dies erforderlich ist, können Erweiterungsentwickler die MiddleLayer-API verwenden, um LSP-Nachrichten abzufangen.

Jede LSP-Nachricht verfügt über eine eigene Schnittstelle der mittleren Ebene zum Abfangen. Um eine bestimmte Nachricht abzufangen, erstellen Sie eine Klasse, die die Schnittstelle der mittleren Ebene für diese Nachricht implementiert. Implementieren Sie dann die [ILanguageClientCustomMessage-Schnittstelle](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage?view=visualstudiosdk-2017) in Ihrer Sprachclientklasse, und geben Sie eine Instanz Ihres Objekts in der [MiddleLayer-Eigenschaft](/dotnet/api/microsoft.visualstudio.languageserver.client.ilanguageclientcustommessage.middlelayer?view=visualstudiosdk-2017) zurück. Beispiel unten:

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

Die Funktion der mittleren Ebene befindet sich noch in der Entwicklung und ist noch nicht vollständig.

## <a name="sample-lsp-language-server-extension"></a>Beispiel für die LSP-Sprachservererweiterung

Informationen zum Quellcode einer Beispielerweiterung mithilfe der LSP-Client-API in Visual Studio finden Sie unter VSSDK-Extensibility-Samples [LSP-Beispiel](https://github.com/Microsoft/VSSDK-Extensibility-Samples/tree/master/LanguageServerProtocol).

## <a name="faq"></a>Häufig gestellte Fragen

**Ich möchte ein benutzerdefiniertes Projektsystem erstellen, um meinen LSP-Sprachserver zu ergänzen, um umfangreichere Feature-Unterstützung in Visual Studio bereitzustellen, wie gehe ich damit um?**

Die Unterstützung für LSP-basierte Sprachserver in Visual Studio basiert auf der Funktion für [offene Ordner](https://devblogs.microsoft.com/visualstudio/open-any-folder-with-visual-studio-15-preview/) und ist so konzipiert, dass kein benutzerdefiniertes Projektsystem erforderlich ist. Sie können Ihr eigenes benutzerdefiniertes Projektsystem nach den Anweisungen [hier](https://github.com/Microsoft/VSProjectSystem)erstellen, aber einige Funktionen, z. B. Einstellungen, funktionieren möglicherweise nicht. Die Standardinitialisierungslogik für LSP-Sprachserver besteht darin, den Speicherort des Stammordners des aktuell geöffneten Ordners zu übergeben. Wenn Sie also ein benutzerdefiniertes Projektsystem verwenden, müssen Sie möglicherweise während der Initialisierung benutzerdefinierte Logik bereitstellen, um sicherzustellen, dass der Sprachserver ordnungsgemäß gestartet werden kann.

**Wie füge ich Debugger-Unterstützung hinzu?**

Wir werden das [gemeinsame Debugging-Protokoll](https://code.visualstudio.com/docs/extensionAPI/api-debugging) in einer zukünftigen Version unterstützen.

**Wenn bereits ein VON VS unterstützter Sprachdienst installiert ist (z. B. JavaScript), kann ich trotzdem eine LSP-Sprachservererweiterung installieren, die zusätzliche Funktionen (z. B. Linting) bietet?**

Ja, aber nicht alle Funktionen funktionieren richtig. Das ultimative Ziel für LSP-Sprachservererweiterungen besteht darin, Sprachdienste zu aktivieren, die nicht nativ von Visual Studio unterstützt werden. Sie können Erweiterungen erstellen, die zusätzliche Unterstützung mithilfe von LSP-Sprachservern bieten, aber einige Funktionen (z. B. IntelliSense) sind nicht reibungslos. Im Allgemeinen wird empfohlen, LSP-Sprachservererweiterungen zu verwenden, um neue Spracherlebnisse bereitzustellen und nicht bestehende zu erweitern.

**Wo veröffentliche ich meinen fertigen LSP-Sprachserver VSIX?**

Siehe die Marketplace-Anweisungen [hier](walkthrough-publishing-a-visual-studio-extension.md).

## <a name="see-also"></a>Weitere Informationen

- [Hinzufügen von Visual Studio-Editor-Unterstützung für andere Sprachen](../ide/adding-visual-studio-editor-support-for-other-languages.md)
