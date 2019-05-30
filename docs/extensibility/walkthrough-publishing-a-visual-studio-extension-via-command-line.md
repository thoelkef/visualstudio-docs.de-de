---
title: Veröffentlichen Sie die Erweiterung, die mithilfe der Befehlszeile
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6b5531bc5dc138f2f90a0a67da39f9583bc4b0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320647"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Exemplarische Vorgehensweise: Veröffentlichen einer Visual Studio-Erweiterung über die Befehlszeile

Diese exemplarische Vorgehensweise zum Veröffentlichen von Visual Studio-Erweiterung in Visual Studio Marketplace über die Befehlszeile. Wenn Sie die Erweiterung zum Marketplace hinzufügen, können Entwickler die [ **Erweiterungen und Updates** ](../ide/finding-and-using-visual-studio-extensions.md) Dialogfeld, um Sie dort nach neuen und aktualisierten Erweiterungen suchen.

VsixPublisher.exe ist das Befehlszeilentool für Visual Studio-Erweiterungen im Marketplace veröffentlichen. Es ist möglich über ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. Zu diesem Tool verfügbare Befehle sind: **veröffentlichen**, **CreatePublisher**, **DeletePublisher**, **DeleteExtension**,  **Anmeldung**, **Logout**.

## <a name="commands"></a>Befehle

### <a name="publish"></a>publish

Eine Erweiterung veröffentlicht in Marketplace. Die Erweiterung möglich einer VSIX-Datei, eine EXE-Datei/Msi-Datei oder einen Link. Wenn die Erweiterung bereits mit der gleichen Version vorhanden ist, überschreibt er die Erweiterung. Wenn die Erweiterung nicht bereits vorhanden ist, wird eine neue Erweiterung erstellt.

|Befehlsoptionen |Beschreibung |
|---------|---------|
|Nutzlast (erforderlich) | Entweder ein Pfad zu der Nutzlast zum Veröffentlichen oder einen Link zu als die "Weitere Informationen-URL" verwenden. |
|PublishManifest (erforderlich) | Pfad zu der veröffentlichen-Manifestdatei zu verwenden. |
|ignoreWarnings | Liste mit Warnungen beim Veröffentlichen einer Extension ignoriert werden sollen. Diese Warnungen werden als Nachrichten von der Befehlszeile angezeigt, beim Veröffentlichen einer Extension. (z. B. "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Persönliches Zugriffstoken (PAT), die verwendet wird, auf den Verleger zu authentifizieren. Wenn nicht angegeben, wird die PAT der angemeldeten Benutzer abgerufen. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Erstellt ein Publisher im Marketplace an. Protokolliert ebenfalls den Verleger, auf dem Computer, für die zukünftige Aktionen (z. B. eine Erweiterung löschen bzw. veröffentlichen).

|Befehlsoptionen |Beschreibung |
|---------|---------|
|"DisplayName" (erforderlich) | Der Anzeigename des Herausgebers. |
|PublisherName (erforderlich) | Der Name des Verlegers (z. B. den Bezeichner). |
|PersonalAccessToken (erforderlich) | Persönliche Zugriffstoken, das zum Authentifizieren von des Verlegers verwendet wird. |
|shortDescription | Eine kurze Beschreibung des Verlegers (nicht-Datei). |
|longDescription | Eine lange Beschreibung des Verlegers (nicht-Datei). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Löscht ein Publisher im Marketplace.

|Befehlsoptionen |Beschreibung |
|---------|---------|
|PublisherName (erforderlich) | Der Name des Verlegers (z. B. den Bezeichner). |
|PersonalAccessToken (erforderlich) | Persönliche Zugriffstoken, das zum Authentifizieren von des Verlegers verwendet wird. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Löscht eine Erweiterung aus dem Marketplace an.

|Befehlsoptionen |Beschreibung |
|---------|---------|
|ExtensionName (erforderlich) | Der Name der Erweiterung zu löschen. |
|PublisherName (erforderlich) | Der Name des Verlegers (z. B. den Bezeichner). |
|personalAccessToken | Persönliche Zugriffstoken, das zum Authentifizieren von des Verlegers verwendet wird. Wenn nicht angegeben, wird die Pat der angemeldeten Benutzer abgerufen. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>Anmeldung

Protokolliert einen Verleger auf dem Computer an.

|Befehlsoptionen |Beschreibung |
|---------|---------|
|PersonalAccessToken (erforderlich | Persönliche Zugriffstoken, das zum Authentifizieren von des Verlegers verwendet wird. |
|PublisherName (erforderlich) | Der Name des Verlegers (z. B. den Bezeichner). |
|overwrite | Gibt an, dass alle vorhandenen Herausgeber mit dem neuen personal Access Token überschrieben werden soll. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>Abmelden

Protokolliert einen Verleger vom Computer.

|Befehlsoptionen |Beschreibung |
|---------|---------|
|PublisherName (erforderlich) | Der Name des Verlegers (z. B. den Bezeichner). |
|ignoreMissingPublisher | Gibt an, dass das Tool nicht Fehler sollten, wenn dem angegebenen Herausgeber nicht bereits angemeldet ist. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>PublishManifest-Datei

Eine PublishManifest-Datei wird verwendet, durch die **veröffentlichen** Befehl. Es stellt alle Metadaten für die Erweiterung, die im Marketplace wissen muss, dar. Wenn die Erweiterung, die hochgeladen wird von einer VSIX-Erweiterung ist, muss die "Identity"-Eigenschaft nur "InternalName" festgelegt sein. Das liegt der Rest der Eigenschaften "Identity" aus der Vsixmanifest-Datei generiert werden kann. Wenn die Erweiterung eine MSI-Datei/exe-Datei oder eine Erweiterung der Link ist, muss der Benutzer die erforderlichen Felder in der Eigenschaft "Identity" angeben. Der Rest des Manifests enthält spezielle Informationen zur Marketplace (z. B. Kategorien gibt an, ob f & A aktiviert ist, usw..).

VSIX-Erweiterung PublishManifest-Beispieldatei:

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

MSI-Datei/exe-Dateien oder LINK PublishManifest-Beispieldatei:

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

## <a name="asset-files"></a>Medienobjektdateien

Medienobjektdateien können für das Einbetten von Dinge wie Bilder in der Readme-Datei angegeben werden. Wenn beispielsweise eine Erweiterung der folgenden "Übersicht" markdowndokument hat:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Um "images/testlogo.png" im vorherigen Beispiel zu beheben, kann Benutzer "AssetFiles" angeben, deren veröffentlichen wie unten manifest:

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

## <a name="publishing-walkthrough"></a>Veröffentlichung Exemplarische Vorgehensweise

### <a name="prerequisites"></a>Vorraussetzungen

Um diese exemplarische Vorgehensweise befolgen zu können, müssen Sie das Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Erstellen Sie eine Visual Studio-Erweiterung

In diesem Fall verwenden wir eine Standard-VSPackage-Erweiterung, aber die gleichen Schritte gelten für jede Art von Erweiterung.

1. Erstellen Sie ein VSPackage in c# mit dem Namen "TestPublish", das einen Menübefehl verfügt. Weitere Informationen finden Sie unter [Erstellen Ihrer ersten Erweiterung: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Packen Sie die Erweiterung

1. Aktualisieren Sie die Erweiterung Vsixmanifest mit den richtigen Informationen zu den Produktnamen, Autor und Version.

   ![Aktualisieren Sie die Erweiterung vsixmanifest](media/update-extension-vsixmanifest.png)

2. Erstellen Sie Ihre Erweiterung **Version** Modus. Die Erweiterung wird jetzt als einer im Ordner \bin\Release des VSIX-Datei verpackt werden.

3. Sie können die Überprüfung die Installation des VSIX-Datei doppelklicken.

### <a name="test-the-extension"></a>Testen Sie die Erweiterung

 Bevor Sie die Erweiterung verteilen, erstellen Sie und Testen Sie, um sicherzustellen, dass es in der experimentellen Instanz von Visual Studio ordnungsgemäß installiert ist.

1. In Visual Studio debuggen. Um eine experimentelle Instanz von Visual Studio zu öffnen.

2. Wechseln Sie in der experimentellen Instanz zu den **Tools** Menü **Erweiterungen und Updates...** . Die Erweiterung TestPublish sollten im mittleren Bereich angezeigt werden, und aktiviert werden.

3. Auf der **Tools** Menü sicherzustellen, dass den Testbefehl.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Veröffentlichen der Extension im Marketplace, über die Befehlszeile

1. Stellen Sie sicher, dass Sie die endgültigen Produktversion von Ihrer Erweiterung erstellt haben und dass sie auf dem neuesten Stand ist.

2. Stellen Sie sicher, dass Sie publishmanifest.json und overview.md Dateien erstellt haben.

3. Öffnen Sie über die Befehlszeile, und navigieren Sie zum Verzeichnis "${VSInstallDir}" \VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Um einen neuen Herausgeber erstellen möchten, verwenden Sie den folgenden Befehl aus:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Bei der erfolgreichen Erstellung des Verlegers sehen Sie die folgende Befehlszeile angezeigt:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. Sie können überprüfen, ob Sie erstellt haben, navigieren Sie zum neuen Verleger [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Um eine neue Erweiterung zu veröffentlichen, verwenden Sie den folgenden Befehl ein:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Bei der erfolgreichen Erstellung des Verlegers sehen Sie die folgende Befehlszeile angezeigt:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. Sie können überprüfen, ob die neue Erweiterung, die Sie durch Navigieren zu veröffentlicht [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installieren Sie die Erweiterung von Visual Studio Marketplace

Nun, dass die Erweiterung veröffentlicht wurde, installieren Sie es in Visual Studio, und Testen sie dort.

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates...** .

2. Klicken Sie auf **Online** und suchen Sie nach TestPublish.

3. Klicken Sie auf **Download**. Die Erweiterung wird dann für die Installation geplant werden.

4. Schließen Sie alle Instanzen von Visual Studio, um die Installation abzuschließen.

## <a name="remove-the-extension"></a>Entfernen der Erweiterung

Sie können die Erweiterung von Visual Studio Marketplace und auf Ihrem Computer entfernen.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>So entfernen Sie die Erweiterung aus dem Marketplace über die Befehlszeile

1. Wenn Sie eine Erweiterung entfernen möchten, verwenden Sie den folgenden Befehl aus:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Nach erfolgreichem Löschen der Erweiterung sehen Sie die folgende Befehlszeile angezeigt:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Um die Erweiterung auf Ihrem Computer zu entfernen.

1. In Visual Studio auf die **Tools** Menü klicken Sie auf **Erweiterungen und Updates**.

2. Wählen Sie "MyVsixExtension" aus, und klicken Sie dann auf **Deinstallieren**. Die Erweiterung wird dann für die Deinstallation geplant.

3. Schließen Sie alle Instanzen von Visual Studio, um die Deinstallation abzuschließen.
