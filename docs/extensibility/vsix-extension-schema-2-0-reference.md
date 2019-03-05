---
title: Referenz zum VSIX-Erweiterung 2.0-Schema | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af4fd52b28846228f447f70320babbdd357bac89
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324129"
---
# <a name="vsix-extension-schema-20-reference"></a>Referenz zum VSIX-Erweiterung Schema 2.0
Eine VSIX-Bereitstellung-Manifestdatei beschreibt den Inhalt einer VSIX-Paket. Das Dateiformat wird durch ein Schema bestimmt. Version 2.0 von diesem Schema unterstützt das Hinzufügen von benutzerdefinierten Typen und Attribute.  Das Schema des Manifests ist erweiterbar. Das Ladeprogramm des Manifeste ignoriert XML-Elemente und Attribute, die sie nicht versteht.

> [!IMPORTANT]
>  Visual Studio 2015 können VSIX-Dateien in den Formaten für Visual Studio 2010, Visual Studio 2012 oder Visual Studio 2013 laden.

## <a name="package-manifest-schema"></a>Paket-manifest-schema
 Das Stammelement der XML-Manifestdatei ist `<PackageManifest>`. Es wurde ein einzelnes Attribut `Version`, dies ist die Version des Manifests-Formats. Wenn das Format wesentliche Änderungen vorgenommen werden, wird das Versionsformat geändert. In diesem Artikel wird beschrieben, Manifestformat Version 2.0, die im Manifest, durch Festlegen angegeben ist der `Version` -Attributs auf den Wert der-Version = "2.0".

### <a name="packagemanifest-element"></a>PackageManifest-element
 In der `<PackageManifest>` "Root"-Element können Sie die folgenden Elemente:

-   `<Metadata>` -Metadaten und Werbung Informationen für das Paket selbst. Nur ein `Metadata` Element ist im Manifest zulässig.

-   `<Installation>` : In diesem Abschnitt werden die Möglichkeit, die dieses Erweiterungspaket installiert werden kann, einschließlich der Anwendung-SKUs, die sie installieren kann, die definiert. Nur eine einzige `Installation` Element ist im Manifest zulässig. Ein Manifest benötigen eine `Installation` Element oder das Paket kann nicht in einer anderen SKU installiert.

-   `<Dependencies>` – Eine optionale Liste von Abhängigkeiten für dieses Paket sind hier definiert.

-   `<Assets>` – Dieser Abschnitt enthält alle Ressourcen in diesem Paket enthalten sind. Dieses Paket wird keine Inhalte auftreten, ohne zu diesem Abschnitt.

-   `<AnyElement>*` – Die manifest-Schema ist flexibel genug ist, um andere Elemente zu ermöglichen. Keine untergeordneten Elemente, die vom manifest-Ladeprogramm nicht erkannt werden als zusätzliche XmlElement-Objekte in der Erweiterungs-Manager-API verfügbar gemacht. Verwenden diese untergeordneten Elemente, können VSIX-Erweiterungen zusätzliche Daten in der Manifestdatei definieren, die Ausführung in Visual Studio Code zur Laufzeit zugreifen können. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> und <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.

### <a name="metadata-element"></a>Metadata-element
 Dieser Abschnitt enthält die Metadaten zum Paket, dessen Identität und Informationen ankündigen. `<Metadata>` enthält die folgenden Elemente:

-   `<Identity>` : Definiert die Identifikationsinformationen für dieses Paket, und enthält die folgenden Attribute:

    -   `Id` – Dieses Attribut muss es sich um eine eindeutige ID für das Paket von dessen Autor ausgewählt sein. Der Name sollte die gleiche Weise qualifiziert werden, die CLR-Typen mit Namespace angegeben werden: Company.Product.Feature.Name. Die `Id` -Attribut ist auf maximal 100 Zeichen umfassen.

    -   `Version` : Definiert die Version der dieses Paket und dessen Inhalt. Dieses Attribut weist das folgende CLR-Assembly Versioning Format: Major.Minor.Build.Revision (1.2.40308.00). Ein Paket mit einer höheren Versionsnummer Aktualisierungen des Pakets gilt, und kann über die vorhandene installierte Version installiert werden.

    -   `Language` – Dieses Attribut ist die Standardsprache für das Paket und die Textdaten in diesem Manifest entspricht. Dieses Attribut folgt der CLR Gebietsschema Code-Konvention für Ressourcenassemblys, zum Beispiel: En-us, En, fr-fr. Sie können angeben, `neutral` eine sprachneutrale-Erweiterung zu deklarieren, die auf eine beliebige Version von Visual Studio ausgeführt wird. Der Standardwert ist `neutral`.

    -   `Publisher` – Dieses Attribut identifiziert den Herausgeber der dieses Paket, ein Unternehmen oder eine einzelne Name. Die `Publisher` -Attribut ist auf maximal 100 Zeichen umfassen.

-   `<DisplayName>` : Dieses Element gibt den benutzerfreundlichen Paketnamen an, der in der Erweiterungs-Manager-UI angezeigt wird. Die `DisplayName` Inhalt ist auf 50 Zeichen begrenzt.

-   `<Description>` – Dieses optionale Element ist eine kurze Beschreibung des Pakets und dessen Inhalt, die im Erweiterungs-Manager-UI angezeigt wird. Die `Description` Inhalt kann einen beliebigen Text ein, die Sie möchten, aber hat enthalten auf 1000 Zeichen begrenzt.

-   `<MoreInfo>` – Dieses optionale Element ist eine URL zu einer Seite online, die eine vollständige Beschreibung der dieses Paket enthält. Das Protokoll muss als http angegeben werden.

-   `<License>` – Dieses optionale Element ist ein relativer Pfad in eine Lizenzdatei (".txt", "RTF") im Paket enthalten.

-   `<ReleaseNotes>` – Dieses optionale Element ist entweder einen relativen Pfad zu einer Release Notes-Datei, die innerhalb des Pakets (".txt", "RTF"), oder andernfalls eine URL zu einer Website, in dem die Anmerkungen zu dieser Version angezeigt.

-   `<Icon>` – Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei (Png, Bmp, Jpeg, Ico), der im Paket enthalten sind. Das Symbolbild muss 32 x 32 Pixel (oder wird auf diese Größe verkleinert werden kann) und in "ListView"-Benutzeroberfläche angezeigt wird. Wenn kein `Icon` -Element angegeben wird, der Benutzeroberfläche verwendet den Standardwert.

-   `<PreviewImage>` – Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei (Png, Bmp, Jpeg), der im Paket enthalten sind. Das Vorschaubild sollte 200 x 200 Pixel und in den Details-Benutzeroberfläche angezeigt. Wenn kein `PreviewImage` -Element angegeben wird, der Benutzeroberfläche verwendet den Standardwert.

-   `<Tags>` – Dieses optionale Element enthält zusätzliche durch Semikolons getrennten Text-Tags, die für suchhinweise verwendet werden. Die `Tags` -Elements ist auf 100 Zeichen beschränkt.

-   `<GettingStartedGuide>` – Dieses optionale Element ist entweder einen relativen Pfad zu einer HTML-Datei oder eine URL zu einer Website, die Informationen zur Verwendung der Erweiterung oder der Inhalt dieses Pakets enthält. Dieses Handbuch ist als Teil einer Installation gestartet.

-   `<AnyElement>*` – Die manifest-Schema ist flexibel genug ist, um andere Elemente zu ermöglichen. Keine untergeordneten Elemente, die vom manifest-Ladeprogramm erkannt werden nicht werden als eine Liste der XmlElement-Objekte verfügbar gemacht. Verwenden diese untergeordneten Elemente, VSIX-Erweiterungen definieren zusätzliche Daten in der Manifestdatei und zur Laufzeit aufzulisten.

### <a name="installation-element"></a>Installationselement
 Dieser Abschnitt definiert die Möglichkeit, die dieses Paket installiert werden kann und die Anwendung-SKUs, die sie installieren kann. Dieser Abschnitt enthält die folgenden Attribute:

-   `Experimental` – Legen Sie dieses Attribut auf "true", wenn Sie eine Erweiterung, die derzeit für alle Benutzer installiert ist, aber Sie eine aktualisierte Version auf demselben Computer entwickeln. Zum Beispiel, wenn MyExtension 1.0 für alle Benutzer installiert haben, aber Sie debuggen möchten MyExtension 2.0 auf dem gleichen Computer, legen Sie experimentell = "true". Dieses Attribut ist in Visual Studio 2015 Update 1 und höher verfügbar.

-   `Scope` – Dieses Attribut kann den Wert "Global" oder "ProductExtension" annehmen:

    -   "Global" gibt an, dass die Installation nicht für eine bestimmte SKU begrenzt ist. Beispielsweise wird dieser Wert verwendet, wenn eine Erweiterungs-SDK installiert ist.

    -   "ProductExtension" gibt an, dass eine herkömmliche VSIX-Erweiterung (Version 1.0) auf den einzelnen Visual Studio-SKUs begrenzt installiert ist. Dies ist der Standardwert.

-   `AllUsers` – Dieses optionale Attribut gibt an, ob dieses Paket für alle Benutzer installiert werden soll. Standardmäßig ist dieses Attribut false gibt an, der angibt, dass das Paket pro Benutzer ist. (Wenn Sie diesen Wert auf "true" festlegen, muss der installierende Benutzer Administratorrechte auf die resultierende VSIX installiert erhöhen.

-   `InstalledByMsi` – Dieses optionale Attribut gibt an, ob dieses Paket von einem MSI installiert ist. Pakete installiert, indem Sie eine MSI-Datei installiert und von MSI-Datei (Programme und Funktionen) und nicht von der Visual Studio Erweiterungs-Manager verwaltet werden.  Standardmäßig ist dieses Attribut false gibt an, der angibt, dass das Paket nicht von einem MSI installiert ist.

-   `SystemComponent` – Dieses optionale Attribut gibt an, ob dieses Paket eine Systemkomponente berücksichtigt werden soll. Komponenten des Informationssystems nicht in der Erweiterungs-Manager-UI anzeigen und können nicht aktualisiert werden. Standardmäßig ist dieses Attribut false gibt an, die angibt, dass das Paket eine Systemkomponente ist.

-   `AnyAttribute*` – Die `Installation` -Element akzeptiert einen offenen Satz von Attributen, die zur Laufzeit als Wörterbuch mit Name-Wert-Paar verfügbar gemacht werden.

-   `<InstallationTarget>` : Dieses Element steuert den Speicherort, in dem das VSIX-Installationsprogramm für das Paket installiert. Wenn der Wert des der `Scope` -Attribut ist "ProductExtension" das Paket muss als Ziel eine SKU, die eine Manifestdatei im Rahmen der Inhalt in seine Verfügbarkeit Erweiterungen ankündigen installiert wurde. Die `<InstallationTarget>` Element verfügt über die folgenden Attribute, wenn die `Scope` Attribut hat den expliziten oder Standardwert "ProductExtension":

    -   `Id` – Dieses Attribut identifiziert das Paket.  Das Attribut folgt der Konvention: Company.Product.Feature.Name. Die `Id` -Attribut darf nur alphanumerische Zeichen und maximal 100 Zeichen umfassen. Erwartete Werte:

        -   Microsoft.VisualStudio.IntegratedShell

        -   Microsoft.VisualStudio.Pro

        -   Microsoft.VisualStudio.Premium

        -   Microsoft.VisualStudio.Ultimate

        -   Microsoft.VisualStudio.VWDExpress

        -   Microsoft.VisualStudio.VPDExpress

        -   Microsoft.VisualStudio.VSWinExpress

        -   Microsoft.VisualStudio.VSLS

        -   My.Shell.App

    -   `Version` – Dieses Attribut gibt einen Versionsbereich, mit der minimalen und maximalen unterstützten Versionen dieser SKU. Ein Paket kann die Versionen der SKUs ausführlich beschrieben, die es unterstützt. Die Bereichsangabe Version ist [10.0-11.0], wo

        -   [-Mindestversion inklusive.

        -   ]-Maximalversion inklusive.

        -   (-Mindestversion, die exklusiv.

        -   ) – maximale Version des exklusiven.

        -   Einzelne Version # - nur die angegebene Version.

        > [!IMPORTANT]
        > Version 2.0 des VSIX-Schema wurde in Visual Studio 2012 eingeführt. Dieses Schema verwenden. Sie benötigen Visual Studio 2012 oder höher auf dem Computer installiert und die VSIXInstaller.exe, die Teil des Produkts verwenden. Sie können frühere Versionen von Visual Studio mit einem Visual Studio 2012 oder höher VSIX-Installationsprogramm, aber nur mit den neueren Versionen des Installationsprogramms.

        Visual Studio 2017-Versionsnummern finden Sie unter [Visual Studio-Buildnummern und-Veröffentlichungstermine](../install/visual-studio-build-numbers-and-release-dates.md).

        Wenn die Version für Visual Studio 2017-Versionen auszudrücken, sollte immer die Nebenversion sein **0**. Z. B. sollten Visual Studio 2017 Version 15.3.26730.0 ausgedrückt werden, als [15.0.26730.0,16.0). Dies ist nur für Visual Studio 2017 und höher Versionsnummern erforderlich sind.

    -   `AnyAttribute*` – Die `<InstallationTarget>` -Element ermöglicht einen offenen Satz von Attributen, die zur Laufzeit als Wörterbuch mit Name-Wert-Paar verfügbar gemacht wird.

### <a name="dependencies-element"></a>Abhängigkeitselement
 Dieses Element enthält eine Liste der Abhängigkeiten, die dieses Paket deklariert. Wenn alle Abhängigkeiten angegeben sind, diese Pakete (identifizierte ihre `Id`) müssen vor dem installiert wurden.

-   `<Dependency>` Element - hat dieses untergeordnete Element die folgenden Attribute:

    -   `Id` – Dieses Attribut muss es sich um eine eindeutige ID für das abhängige Paket sein. Dieser Identitätswert muss übereinstimmen der `<Metadata><Identity>Id` Attribut eines Pakets, das dieses Paket abhängig ist. Die `Id` folgt der Konvention Namespace, Attribut: Company.Product.Feature.Name. Das Attribut darf nur alphanumerische Zeichen enthalten und ist auf 100 Zeichen beschränkt.

    -   `Version` – Dieses Attribut gibt einen Versionsbereich, mit der minimalen und maximalen unterstützten Versionen dieser SKU. Ein Paket kann die Versionen der SKUs ausführlich beschrieben, die es unterstützt. Die Version Bereich Notation ist [12.0, 13.0], wobei:

        -   [-Mindestversion inklusive.

        -   ]-Maximalversion inklusive.

        -   (-Mindestversion, die exklusiv.

        -   ) – maximale Version des exklusiven.

        -   Einzelne Version # - nur die angegebene Version.

    -   `DisplayName` – Dieses Attribut ist der Anzeigename, der das abhängige Paket, die im UI-Elemente wie z. B. Dialogfelder und Fehlermeldungen verwendet wird. Das Attribut ist optional, es sei denn, das abhängige Paket von MSI-Datei installiert wird.

    -   `Location` – Dieses optionale Attribut gibt an, entweder den relativen Pfad innerhalb dieser VSIX zu einem geschachtelten VSIX-Paket oder eine URL zu den Downloadpfad für die Abhängigkeit. Dieses Attribut wird verwendet, damit der Benutzer, die das erforderliche Paket suchen kann.

    -   `AnyAttribute*` – Die `Dependency` -Element akzeptiert einen offenen Satz von Attributen, die zur Laufzeit als Wörterbuch mit Name-Wert-Paar verfügbar gemacht werden.

### <a name="assets-element"></a>Ressourcen-element
 Dieses Element enthält eine Liste der `<Asset>` Tags für jedes Element Erweiterung oder des Inhalts, die von diesem Paket verfügbar gemacht.

- `<Asset>` : Dieses Element enthält die folgenden Attribute und Elemente:

  - `Type` -Typ der Erweiterung oder Inhalte, die durch dieses Element dargestellt wird. Jede `<Asset>` Element benötigen einen einzigen `Type`, aber mehrere `<Asset>` möglicherweise Elemente verfügen über denselben `Type`. Dieses Attribut muss als vollständig qualifizierter Name, nach Namespace Konventionen dargestellt werden. Die bekannten Typen sind:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Sie können eigene Typen erstellen, und geben sie eindeutige Namen. Zur Laufzeit in Visual Studio kann Ihr Code auflisten und Zugriff auf diese benutzerdefinierte Typen über die Erweiterungs-Manager-API.

  - `Path` -der relative Pfad in die Datei oder Ordner innerhalb des Pakets, das das Objekt enthält.

  - `TargetVersion` -der Versionsbereich für die das angegebene Objekt gilt. Wird verwendet, um den rückversand für mehrere Versionen der Objekte auf verschiedene Versionen von Visual Studio. Erfordert Visual Studio 2017.3 oder höher angewendet werden kann.

  - `AnyAttribute*` -Einen offenen Satz von Attributen, der zur Laufzeit als ein Wörterbuch mit Name-Wert-Paaren verfügbar gemacht wird.

     `<AnyElement>*` – Beliebige strukturierten Inhalten kann zwischen einem `<Asset>` Begin- und end-Tag. Alle Elemente werden als eine Liste der XmlElement-Objekte verfügbar gemacht. VSIX-Erweiterungen können strukturierte typspezifische Metadaten definieren, in der Manifestdatei und zur Laufzeit aufzulisten.

### <a name="sample-manifest"></a>Beispielmanifest

```
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
  <Metadata>
    <Identity Id="0000000-0000-0000-0000-000000000000" Version="1.0" Language="en-US" Publisher="Company" />
    <DisplayName>Test Package</DisplayName>
    <Description>Information about my package</Description>
    <MoreInfo>http://www.fabrikam.com/Extension1/</MoreInfo>
    <License>eula.rtf</License>
    <ReleaseNotes>notes.txt</ReleaseNotes>
    <Icon>Images\icon.png</Icon>
    <PreviewImage>Images\preview.png</PreviewImage>
  </Metadata>
  <Installation InstalledByMsi="false" AllUsers="false" SystemComponent="false" Scope="ProductExtension">
    <InstallationTarget Id="Microsoft.VisualStudio.Pro" Version="[11.0, 12.0]" />
  </Installation>
  <Dependencies>
    <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="[4.5,)" />
    <Dependency Id="Microsoft.VisualStudio.MPF.12.0" DisplayName="Visual Studio MPF 12.0" d:Source="Installed" Version="[12.0]" />
  </Dependencies>
  <Assets>
    <Asset Type="Microsoft.VisualStudio.VsPackage" d:Source="Project" d:ProjectName="%CurrentProject%" Path="|%CurrentProject%;PkgdefProjectOutputGroup|" />
  </Assets>
</PackageManifest>
```

## <a name="see-also"></a>Siehe auch
- [Versand von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)
