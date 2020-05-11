---
title: Veröffentlichen der Erweiterung mithilfe der Befehlszeile
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697128"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung über die Befehlszeile

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie eine Visual Studio-Erweiterung im Visual Studio Marketplace mithilfe der Befehlszeile veröffentlichen. Wenn Sie Ihre Erweiterung zum Marketplace hinzufügen, können Entwickler das Dialogfeld [**Erweiterungen und Updates**](../ide/finding-and-using-visual-studio-extensions.md) verwenden, um dort nach neuen und aktualisierten Erweiterungen zu suchen.

VsixPublisher.exe ist das Befehlszeilentool zum Veröffentlichen von Visual Studio-Erweiterungen im Marketplace. Auf sie kann von der Datei "VSInstallDir" und "VSSDK" und "VisualStudioIntegration" auf die Datei "Tools" und "Bin" und "VsixPublisher.exe" zugegriffen werden. Die in diesem Tool verfügbaren Befehle sind: **publish**, **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **logout**.

## <a name="commands"></a>Befehle

### <a name="publish"></a>Veröffentlichen

Veröffentlicht eine Erweiterung für den Marketplace. Die Erweiterung kann eine vsix, eine exe/msi-Datei oder ein Link sein. Wenn die Erweiterung bereits mit derselben Version vorhanden ist, wird die Erweiterung überschrieben. Wenn die Erweiterung noch nicht vorhanden ist, wird eine neue Erweiterung erstellt.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|Nutzlast (erforderlich) | Entweder ein Pfad zur zu veröffentlichenden Nutzlast oder ein Link, der als "mehr Info-URL" verwendet werden soll. |
|publishManifest (erforderlich) | Pfad zur zu verwendenden Veröffentlichungsmanifestdatei. |
|IgnoreWarnings | Liste der Warnungen, die beim Veröffentlichen einer Erweiterung ignoriert werden sollen. Diese Warnungen werden beim Veröffentlichen einer Erweiterung als Befehlszeilenmeldungen angezeigt. (z. B. "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Persönlicher Zugriffstoken (PERSONAL Access Token, PAT), der zur Authentifizierung des Herausgebers verwendet wird. Wenn dies nicht angegeben wird, wird die PAT von den angemeldeten Benutzern übernommen. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Erstellt einen Herausgeber auf dem Marketplace. Protokolliert den Herausgeber auch für zukünftige Aktionen (z. B. Löschen/Veröffentlichen einer Erweiterung) am Computer.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|displayName (erforderlich) | Anzeigename des Herausgebers. |
|publisherName (erforderlich) | Der Name des Herausgebers (z. B. der Bezeichner). |
|personalAccessToken (erforderlich) | Persönliches Zugriffstoken, das zum Authentifizieren des Herausgebers verwendet wird. |
|shortBeschreibung | Eine kurze Beschreibung des Herausgebers (keine Datei). |
|longDescription | Eine lange Beschreibung des Herausgebers (keine Datei). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Löscht einen Herausgeber auf dem Marketplace.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|publisherName (erforderlich) | Der Name des Herausgebers (z. B. der Bezeichner). |
|personalAccessToken (erforderlich) | Persönliches Zugriffstoken, das zum Authentifizieren des Herausgebers verwendet wird. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Löscht eine Erweiterung aus dem Marketplace.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|extensionName (erforderlich) | Der Name der zu löschenden Erweiterung. |
|publisherName (erforderlich) | Der Name des Herausgebers (z. B. der Bezeichner). |
|personalAccessToken | Persönliches Zugriffstoken, das zum Authentifizieren des Herausgebers verwendet wird. Wenn dies nicht angegeben wird, wird der Pat von den angemeldeten Benutzern übernommen. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Protokolliert einen Herausgeber in den Computer.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|personalAccessToken (erforderlich | Persönliches Zugriffstoken, das zum Authentifizieren des Herausgebers verwendet wird. |
|publisherName (erforderlich) | Der Name des Herausgebers (z. B. der Bezeichner). |
|overwrite | Gibt an, dass jeder vorhandene Herausgeber mit dem neuen persönlichen Zugriffstoken überschrieben werden soll. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Protokolliert einen Herausgeber vom Computer.

|Befehlsoptionen |BESCHREIBUNG |
|---------|---------|
|publisherName (erforderlich) | Der Name des Herausgebers (z. B. der Bezeichner). |
|ignoreMissingPublisher | Gibt an, dass das Tool nicht fehlerfrei sein soll, wenn der angegebene Herausgeber noch nicht angemeldet ist. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest-Datei

Eine publishManifest-Datei wird vom **Publish-Befehl** verwendet. Sie stellt alle Metadaten über die Erweiterung dar, die der Marketplace kennen muss. Wenn die hochgeladene Erweiterung von einer VSIX-Erweiterung stammt, muss die Eigenschaft "identity" nur den "internalName"-Satz haben. Dies liegt daran, dass die restlichen "Identitäts"-Eigenschaften aus der datei vsixmanifest generiert werden können. Wenn es sich bei der Erweiterung um eine msi/exe- oder eine Linkerweiterung handelt, muss der Benutzer die erforderlichen Felder in der Eigenschaft "identity" angeben. Der Rest des Manifests enthält Informationen, die für den Marketplace spezifisch sind (z. B. Kategorien, ob Q&A aktiviert ist usw.).

VSIX-Erweiterung publishManifest Dateibeispiel:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE- oder LINK publishManifest-Dateibeispiel:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>Asset-Dateien

Asset-Dateien können zum Einbetten von Dingen wie Bildern in die Readme-Datei bereitgestellt werden. Wenn eine Erweiterung beispielsweise über das folgende Markdown-Dokument "Übersicht" verfügt:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Um "images/testlogo.png" im vorherigen Beispiel aufzulösen, kann ein Benutzer "assetFiles" in seinem Veröffentlichungsmanifest wie folgt bereitstellen:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Veröffentlichen der exemplarischen Vorgehensweise

### <a name="prerequisites"></a>Voraussetzungen

Um dieser exemplarischen Vorgehensweise folgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Erstellen einer Visual Studio-Erweiterung

In diesem Fall verwenden wir eine standardmäßige VSPackage-Erweiterung, aber die gleichen Schritte gelten für jede Art von Erweiterung.

1. Erstellen Sie ein VSPackage mit dem Namen "TestPublish" mit einem Menübefehl. Weitere Informationen finden Sie unter [Erstellen Ihrer ersten Erweiterung: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Packen der Erweiterung

1. Aktualisieren Sie die Erweiterung vsixmanifest mit den richtigen Informationen zu Produktname, Autor und Version.

   ![Update-Erweiterung vsixmanifest](media/update-extension-vsixmanifest.png)

2. Erstellen Sie **Release** Ihre Erweiterung im Release-Modus. Jetzt wird Ihre Erweiterung als VSIX im Ordner .bin-Release verpackt.

3. Sie können auf den VSIX doppelklicken, um die Installation zu überprüfen.

### <a name="test-the-extension"></a>Testen der Erweiterung

 Bevor Sie die Erweiterung verteilen, erstellen und testen Sie sie, um sicherzustellen, dass sie in der experimentellen Instanz von Visual Studio ordnungsgemäß installiert ist.

1. Beginnen Sie in Visual Studio mit dem Debuggen. , um eine experimentelle Instanz von Visual Studio zu öffnen.

2. Wechseln Sie in der experimentellen Instanz zum Menü **Extras** und klicken Sie auf **Erweiterungen und Updates...**. Die TestPublish-Erweiterung sollte im mittleren Bereich angezeigt und aktiviert sein.

3. Stellen Sie im Menü **Extras** sicher, dass der Testbefehl angezeigt wird.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Veröffentlichen der Erweiterung auf dem Marketplace über die Befehlszeile

1. Stellen Sie sicher, dass Sie die Release-Version Ihrer Erweiterung erstellt haben und dass sie auf dem neuesten Stand ist.

2. Stellen Sie sicher, dass Sie publishmanifest.json und overview.md Dateien erstellt haben.

3. Öffnen Sie die Befehlszeile, und navigieren Sie zu dem Verzeichnis "VSInstallDir", "VSSDK" und "VisualStudioIntegration", "Tools" und "Bin"-Verzeichnis.

4. Um einen neuen Herausgeber zu erstellen, verwenden Sie den folgenden Befehl:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Bei erfolgreicher Erstellung des Herausgebers wird die folgende Befehlszeilenmeldung angezeigt:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Sie können den neuen Herausgeber überprüfen, den Sie erstellt haben, indem Sie zu [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers) navigieren.

7. Um eine neue Erweiterung zu veröffentlichen, verwenden Sie den folgenden Befehl:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Bei erfolgreicher Erstellung des Herausgebers wird die folgende Befehlszeilenmeldung angezeigt:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Sie können die neue Erweiterung, die Sie veröffentlicht haben, überprüfen, indem Sie zu [Visual Studio Marketplace](https://marketplace.visualstudio.com/) navigieren.

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installieren der Erweiterung aus dem Visual Studio Marketplace

Nachdem die Erweiterung veröffentlicht wurde, installieren Sie sie in Visual Studio und testen Sie sie dort.

1. Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungen und Updates...**.

2. Klicken Sie auf **Online,** und suchen Sie dann nach TestPublish.

3. Klicken Sie auf **Download**. Die Erweiterung wird dann für die Installation geplant.

4. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

Sie können die Erweiterung aus dem Visual Studio Marketplace und von Ihrem Computer entfernen.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>So entfernen Sie die Erweiterung aus dem Marketplace über die Befehlszeile

1. Wenn Sie eine Erweiterung entfernen möchten, verwenden Sie den folgenden Befehl:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Beim erfolgreichen Löschen der Erweiterung wird die folgende Befehlszeilenmeldung angezeigt:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>So entfernen Sie die Erweiterung von Ihrem Computer

1. Klicken Sie in Visual Studio im Menü **Extras** auf **Erweiterungen und Updates**.

2. Wählen Sie "MyVsixExtension" und klicken Sie dann auf **Deinstallieren**. Die Erweiterung wird dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Deinstallation abzuschließen.
