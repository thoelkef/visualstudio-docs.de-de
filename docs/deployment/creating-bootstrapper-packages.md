---
title: Erstellen von Bootstrapperpaketen
ms.date: 05/02/2018
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [Visual Studio], prerequisites
- deploying applications [Visual Studio], custom prerequisites
- prerequisites, custom
- RedistList file
- custom prerequisites
- redistributables list
ms.assetid: ba1a785b-693d-446b-bcae-b88cadee73d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 960ecd2680585602b2c026b00b36bf7d93b8021d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900230"
---
# <a name="create-bootstrapper-packages"></a>Erstellen von Bootstrapperpaketen
Das Setupprogramm ist ein generisches Installationsprogramm, das für die Ermittlung und die Installation von weitervertreibbaren Komponenten wie Windows Installer (*MSI*-Format) und ausführbaren Programmen konfiguriert werden kann. Das Installationsprogramm wird auch als Bootstrapper bezeichnet. Der Bootstrapper wird mithilfe einer Reihe von XML-Manifesten programmiert, mit denen die Metadaten zur Verwaltung der Komponenteninstallation angegeben werden.  Jede verteilbare Komponente "oder" Prerequisite, angezeigt, die der **Voraussetzungen** im Dialogfeld für ClickOnce ist ein Bootstrapperpaket. Bei einem Bootstrapperpaket handelt es sich um eine Gruppe von Verzeichnissen und Dateien, die Manifestdateien enthalten, mit denen beschrieben wird, wie die erforderliche Komponente installiert werden muss.

Der Bootstrapper ermittelt zunächst, ob erforderliche Komponenten bereits installiert sind. Ist dies nicht der Fall, werden vom Bootstrapper die Lizenzverträge angezeigt. Nachdem der Endbenutzer die Lizenzverträge akzeptiert hat, beginnt die Installation der erforderlichen Komponenten. Wurden alle erforderlichen Komponenten ermittelt, wird direkt das Installationsprogramm der Anwendung gestartet.

## <a name="create-custom-bootstrapper-packages"></a>Erstellen Sie benutzerdefinierte Bootstrapperpakete
Sie können die Bootstrapper-Manifeste generieren, indem Sie mit der XML-Editor in Visual Studio. Ein Beispiel zum Erstellen eines Bootstrapperpakets finden Sie unter [Exemplarische Vorgehensweise: Erstellen eines benutzerdefinierten Bootstrappers einer datenschutzeingabeaufforderung](../deployment/walkthrough-creating-a-custom-bootstrapper-to-show-a-privacy-prompt.md).

Zum Erstellen eines Bootstrapper-Pakets Sie zum Erstellen eines Produktmanifests und, für jede lokalisierte Version einer Komponente, die auch ein Paketmanifest.

* Das Produktmanifest, *product.xml*, alle sprachneutralen Metadaten für das Paket enthält. Es enthält Metadaten, die für alle lokalisierten Versionen der verteilbaren Komponente gleich sind.  Um diese Datei zu erstellen, finden Sie unter [Vorgehensweise: Erstellen eines Produktmanifests](../deployment/how-to-create-a-product-manifest.md).

* Das Paketmanifest *"Package.xml"*, enthält sprachspezifische Metadaten; sie in der Regel lokalisierte Fehlermeldungen enthält. Eine Komponente benötigt für jede lokalisierte Version dieser Komponente mindestens ein Paketmanifest. Um diese Datei zu erstellen, finden Sie unter [Vorgehensweise: Erstellen eines Paketmanifests](../deployment/how-to-create-a-package-manifest.md).

Nachdem diese Dateien erstellt wurden, platzieren Sie die Produktmanifestdatei in einen entsprechend benannten Ordner für den benutzerdefinierten Bootstrapper. Die Paketmanifestdatei muss in einem Ordner, der dem Gebietsschema entsprechend benannt wurde, abgelegt werden. Wenn die Paketmanifestdatei z. B. für die Neuverteilung in englischer Sprache vorgesehen ist, legen Sie die Datei in einen Ordner mit der Bezeichnung "en" ab. Wiederholen Sie diesen Prozess für jedes Gebietsschema, z. B. "ja" für Japanisch und "de" für Deutsch. Das abschließende benutzerdefinierte Bootstrapperpaket könnte beispielsweise über die folgende Ordnerstruktur verfügen.

    ```xml
    CustomBootstrapperPackage
      product.xml
      CustomBootstrapper.msi
      de
        eula.rtf
        package.xml
      en
        eula.rtf
        package.xml
      ja
        eula.rtf
        package.xml
    ```

Kopieren Sie anschließend die verteilbaren Dateien in den Bootstrapperordner. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen eines lokalisierten Bootstrapperpakets](../deployment/how-to-create-a-localized-bootstrapper-package.md).

    *\Program Files\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*

oder

    *\Program Files (x86)\Microsoft Visual Studio 14.0\SDK\Bootstrapper\Packages*

Sie können auch den Speicherort des Bootstrapperordners mithilfe des Werts **Pfad** im folgenden Registrierungsschlüssel bestimmen:

    *HKLM\Software\Microsoft\GenericBootstrapper\11.0*

Auf 64-Bit-Systemen verwenden Sie den folgenden Registrierungsschlüssel:

    *HKLM\Software\Wow6432Node\Microsoft\GenericBootstrapper\11.0*

Jede verteilbare Komponente wird unter dem Paketverzeichnis in einem eigenen Unterordner angezeigt. Das Produkt Produktmanifest und die verteilbaren Dateien müssen in diesem Unterordner abgelegt werden. Lokalisierte Versionen der Komponente und Paketmanifeste müssen in Unterordnern, die mit dem Namen entsprechend dem Kulturnamen abgelegt werden.

Nachdem diese Dateien in den Bootstrapperordner kopiert wurden, wird das Bootstrapperpaket in Visual Studio automatisch im Dialogfeld **Erforderliche Komponenten** angezeigt. Wird das benutzerdefinierte Bootstrapperpaket nicht angezeigt, schließen Sie das Dialogfeld **Erforderliche Komponenten**, und öffnen Sie es erneut. Weitere Informationen finden Sie unter [Dialogfeld „Erforderliche Komponenten“](../ide/reference/prerequisites-dialog-box.md).

In der folgenden Tabelle werden die Eigenschaften angezeigt, die automatisch vom Bootstrapper eingetragen werden.

|Eigenschaft|Beschreibung|
|--------------|-----------------|
|ApplicationName|Der Name der Anwendung.|
|ProcessorArchitecture|Der Prozessor und die Bits pro Wort für die Plattform, auf die eine ausführbare Datei zielt. Folgende Werte sind gültig:<br /><br /> –   Intel<br />–   IA64<br />–   AMD64|
|[Version9x](/windows/desktop/Msi/version9x)|Die Versionsnummer für Microsoft Windows 95, Windows 98 oder Windows ME. Die Syntax der Version lautet "Major.Minor.ServicePack".|
|[VersionNT](/windows/desktop/Msi/versionnt)|Die Versionsnummer für Windows NT, Windows 2000, Windows XP, Windows Vista, Windows Server 2008 oder Windows 7. Die Syntax der Version lautet "Major.Minor.ServicePack".|
|[VersionMSI](/windows/desktop/Msi/versionmsi)|Die Version der Windows Installer-Assembly (msi.dll), die während der Installation ausgeführt werden soll.|
|[AdminUser](/windows/desktop/Msi/adminuser)|Diese Eigenschaft wird festgelegt, wenn der Benutzer über Administratorrechte verfügt. Gültige Werte sind "true" und "false".|
|InstallMode|Der Installationsmodus gibt an, von welchem Speicherort die Komponente installiert werden muss. Folgende Werte sind gültig:<br /><br /> –   HomeSite: Die erforderlichen Komponenten werden von der Website des Anbieters installiert.<br />–   SpecificSite: Die erforderlichen Komponenten werden vom ausgewählten Speicherort installiert.<br />–   SameSite: Die erforderlichen Komponenten werden vom gleichen Speicherort wie die Anwendung installiert.|

## <a name="separate-redistributables-from-application-installations"></a>Separate verteilbare Komponenten von Anwendungsinstallationen
Sie können die Bereitstellung von verteilbaren Dateien in Setupprojekten auch deaktivieren. Erstellen Sie hierzu im Ordner "RedistList" im Verzeichnis von .NET Framework eine verteilbare Liste:

`%ProgramFiles%\Microsoft.NET\RedistList`

Die verteilbare Liste ist eine XML-Datei, die Sie entsprechend dem folgenden Format benennen sollten: *\<Name des Unternehmens >. \<Komponentenname >. RedistList.xml*. Beispiel: Wenn die Komponente „DataWidgets“ heißt und von der Firma Acme stammt, nennen Sie die Datei *Acme.DataWidgets.RedistList.xml*. Der Inhalt der verteilbaren Liste könnte in etwa so aussehen:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<FileList Redist="Acme.DataWidgets" >
<File AssemblyName="Acme.DataGrid" Version="1.0.0.0" PublicKeyToken="b03f5f7f11d50a3a" Culture="neutral" ProcessorArchitecture="MSIL" InGAC="true" />
</FileList>
```

## <a name="see-also"></a>Siehe auch
- [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Prerequisites dialog box (Dialogfeld „Erforderliche Komponenten“)](../ide/reference/prerequisites-dialog-box.md)
- [Referenz zum Produkt- und Paketschema](../deployment/product-and-package-schema-reference.md)
- [Artikel zum Verwenden des Visual Studio 2005-Bootstrappers zum Starten der Installation](http://go.microsoft.com/fwlink/?LinkId=107537)
