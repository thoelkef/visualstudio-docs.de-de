---
title: VSIX-Erweiterungsschema 2.0-Referenz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78e260c62d67afc10fea25d52169c48b64c82f72
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697900"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX-Erweiterungsschema 2.0-Referenz
Eine VSIX-Bereitstellungsmanifestdatei beschreibt den Inhalt eines VSIX-Pakets. Das Dateiformat wird durch ein Schema gesteuert. Version 2.0 dieses Schemas unterstützt das Hinzufügen von benutzerdefinierten Typen und Attributen.  Das Schema des Manifests ist erweiterbar. Der Manifestlader ignoriert XML-Elemente und -Attribute, die er nicht versteht.

> [!IMPORTANT]
> Visual Studio 2015 kann VSIX-Dateien in den Formaten Visual Studio 2010, Visual Studio 2012 oder Visual Studio 2013 laden.

## <a name="package-manifest-schema"></a>Paketmanifestschema
 Das Stammelement der XML-Manifestdatei ist `<PackageManifest>`. Es hat ein `Version`einzelnes Attribut , das die Version des Manifestformats ist. Wenn größere Änderungen am Format vorgenommen werden, wird das Versionsformat geändert. Dieser Artikel beschreibt manifestformat version 2.0, die im `Version` Manifest angegeben wird, indem das Attribut auf den Wert Version="2.0" festgelegt wird.

### <a name="packagemanifest-element"></a>PackageManifest-Element
 Innerhalb `<PackageManifest>` des Stammelements können Sie die folgenden Elemente verwenden:

- `<Metadata>`- Metadaten und Werbeinformationen über das Paket selbst. Im `Metadata` Manifest ist nur ein Element zulässig.

- `<Installation>`- Dieser Abschnitt definiert die Art und Weise, wie dieses Erweiterungspaket installiert werden kann, einschließlich der Anwendungs-SKUs, in die es installiert werden kann. Im Manifest `Installation` ist nur ein einzelnes Element zulässig. Ein Manifest muss `Installation` über ein Element verfügen, oder dieses Paket wird nicht in einer SKU installiert.

- `<Dependencies>`- Hier wird eine optionale Liste der Abhängigkeiten für dieses Paket definiert.

- `<Assets>`- Dieser Abschnitt enthält alle in diesem Paket enthaltenen Assets. Ohne diesen Abschnitt wird in diesem Paket kein Inhalt angezeigt.

- `<AnyElement>*`- Das Manifestschema ist flexibel genug, um andere Elemente zuzulassen. Alle untergeordneten Elemente, die vom Manifestlader nicht erkannt werden, werden in der Erweiterungs-Manager-API als zusätzliche XmlElement-Objekte verfügbar gemacht. Mithilfe dieser untergeordneten Elemente können VSIX-Erweiterungen zusätzliche Daten in der Manifestdatei definieren, auf die Code, der in Visual Studio ausgeführt wird, zur Laufzeit zugreifen kann. Siehe [Microsoft.VisualStudio.ExtensionManager.iExtension.AdditionalElements](/previous-versions/visualstudio/visual-studio-2013/hh265266(v=vs.120)).

### <a name="metadata-element"></a>Metadatenelement
 Dieser Abschnitt enthält die Metadaten zu dem Paket, seiner Identität und Werbeinformationen. `<Metadata>`enthält die folgenden Elemente:

- `<Identity>`- Definiert Identifikationsinformationen für dieses Paket und enthält die folgenden Attribute:

  - `Id`- Dieses Attribut muss eine eindeutige ID für das vom Autor ausgewählte Paket sein. Der Name sollte auf die gleiche Weise qualifiziert werden, wie CLR-Typen Namespaced sind: Company.Product.Feature.Name. Das `Id` Attribut ist auf 100 Zeichen beschränkt.

  - `Version`- Definiert die Version dieses Pakets und seinen Inhalt. Dieses Attribut folgt dem CLR-Assemblyversionsformat: Major.Minor.Build.Revision (1.2.40308.00). Ein Paket mit einer höheren Versionsnummer gilt als Updates für das Paket und kann über die vorhandene installierte Version installiert werden.

  - `Language`- Dieses Attribut ist die Standardsprache für das Paket und entspricht den Textdaten in diesem Manifest. Dieses Attribut folgt der CLR-Gebietsschemacodekonvention für Ressourcenassemblys, z. B.: en-us, en, fr-fr. Sie können `neutral` angeben, eine sprachneutrale Erweiterung zu deklarieren, die auf jeder Version von Visual Studio ausgeführt wird. Der Standardwert ist `neutral`.

  - `Publisher`- Dieses Attribut identifiziert den Herausgeber dieses Pakets, entweder ein Unternehmen oder einen individuellen Namen. Das `Publisher` Attribut ist auf 100 Zeichen beschränkt.

- `<DisplayName>`- Dieses Element gibt den benutzerfreundlichen Paketnamen an, der in der Extension Manager-Benutzeroberfläche angezeigt wird. Der `DisplayName` Inhalt ist auf 50 Zeichen beschränkt.

- `<Description>`- Dieses optionale Element ist eine kurze Beschreibung des Pakets und seines Inhalts, die in der Extension Manager-Benutzeroberfläche angezeigt wird. Der `Description` Inhalt kann beliebigen Text enthalten, ist jedoch auf 1000 Zeichen beschränkt.

- `<MoreInfo>`- Dieses optionale Element ist eine URL zu einer Online-Seite, die eine vollständige Beschreibung dieses Pakets enthält. Das Protokoll muss als http angegeben werden.

- `<License>`- Dieses optionale Element ist ein relativer Pfad zu einer Lizenzdatei (.txt, .rtf), die im Paket enthalten ist.

- `<ReleaseNotes>`- Dieses optionale Element ist entweder ein relativer Pfad zu einer im Paket enthaltenen Release Notes-Datei (.txt, .rtf) oder eine URL zu einer Website, die die Versionshinweise anzeigt.

- `<Icon>`- Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei (png, bmp, jpg, ico), die im Paket enthalten ist. Das Symbolbild sollte 32x32 Pixel groß sein (oder auf diese Größe verkleinert werden) und wird in der Listenansichtsbenutzeroberfläche angezeigt. Wenn `Icon` kein Element angegeben ist, verwendet die Benutzeroberfläche einen Standardwert.

- `<PreviewImage>`- Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei (png, bmp, jpg), die im Paket enthalten ist. Das Vorschaubild sollte 200x200 Pixel groß sein und in der Detailbenutzeroberfläche angezeigt werden. Wenn `PreviewImage` kein Element angegeben ist, verwendet die Benutzeroberfläche einen Standardwert.

- `<Tags>`- Dieses optionale Element listet zusätzliche durch Semikolons getrennte Text-Tags auf, die für Suchhinweise verwendet werden. Das `Tags` Element ist auf 100 Zeichen beschränkt.

- `<GettingStartedGuide>`- Dieses optionale Element ist entweder ein relativer Pfad zu einer HTML-Datei oder eine URL zu einer Website, die Informationen über die Verwendung der Erweiterung oder des Inhalts in diesem Paket enthält. Dieses Handbuch wird als Teil einer Installation gestartet.

- `<AnyElement>*`- Das Manifestschema ist flexibel genug, um andere Elemente zuzulassen. Alle untergeordneten Elemente, die vom Manifestlader nicht erkannt werden, werden als Liste von XmlElement-Objekten verfügbar gemacht. Mithilfe dieser untergeordneten Elemente können VSIX-Erweiterungen zusätzliche Daten in der Manifestdatei definieren und zur Laufzeit aufzählen.

### <a name="installation-element"></a>Installationselement
 In diesem Abschnitt wird definiert, wie dieses Paket installiert werden kann und in welche Anwendungs-SKUs es installiert werden kann. Dieser Abschnitt enthält die folgenden Attribute:

- `Experimental`- Legen Sie dieses Attribut auf true fest, wenn Sie eine Erweiterung haben, die derzeit für alle Benutzer installiert ist, aber Sie entwickeln eine aktualisierte Version auf demselben Computer. Wenn Sie beispielsweise MyExtension 1.0 für alle Benutzer installiert haben, MyExtension 2.0 jedoch auf demselben Computer debuggen möchten, legen Sie Experimental="true" fest. Dieses Attribut ist in Visual Studio 2015 Update 1 und höher verfügbar.

- `Scope`- Dieses Attribut kann den Wert "Global" oder "ProductExtension" annehmen:

  - "Global" gibt an, dass die Installation nicht auf eine bestimmte SKU beschränkt ist. Dieser Wert wird z. B. verwendet, wenn ein Extension SDK installiert wird.

  - "ProductExtension" gibt an, dass eine herkömmliche VSIX-Erweiterung (Version 1.0) installiert ist, die auf einzelne Visual Studio-SKUs beschränkt ist. Dies ist der Standardwert.

- `AllUsers`- Dieses optionale Attribut gibt an, ob dieses Paket für alle Benutzer installiert wird. Standardmäßig ist dieses Attribut false, was angibt, dass das Paket pro Benutzer ist. (Wenn Sie diesen Wert auf true festlegen, muss der installierende Benutzer auf die Administratorberechtigungsebene anheben, um die resultierende VSIX zu installieren.

- `InstalledByMsi`- Dieses optionale Attribut gibt an, ob dieses Paket von einem MSI installiert wird. Pakete, die von einem MSI installiert werden, werden von MSI (Programme und Features) und nicht vom Visual Studio Extension Manager installiert und verwaltet.  Standardmäßig ist dieses Attribut false, was angibt, dass das Paket nicht von einer MSI installiert wird.

- `SystemComponent`- Dieses optionale Attribut gibt an, ob dieses Paket als Systemkomponente betrachtet werden soll. Systemkomponenten werden nicht in der Erweiterungs-Manager-Benutzeroberfläche angezeigt und können nicht aktualisiert werden. Standardmäßig ist dieses Attribut false, was angibt, dass das Paket keine Systemkomponente ist.

- `AnyAttribute*`- `Installation` Das Element akzeptiert einen offenen Satz von Attributen, die zur Laufzeit als Name-Wert-Paarwörterbuch verfügbar gemacht werden.

- `<InstallationTarget>`-Dieses Element steuert den Speicherort, an dem das VSIX-Installationsprogramm das Paket installiert. Wenn der Wert `Scope` des Attributs "ProductExtension" ist, muss das Paket auf eine SKU abzielen, die eine Manifestdatei als Teil ihres Inhalts installiert hat, um ihre Verfügbarkeit für Erweiterungen anzukündigen. Das `<InstallationTarget>` Element hat die folgenden `Scope` Attribute, wenn das Attribut den expliziten oder Standardwert "ProductExtension" hat:

  - `Id`- Dieses Attribut identifiziert das Paket.  Das Attribut folgt der Namespacekonvention: Company.Product.Feature.Name. Das `Id` Attribut darf nur alphanumerische Zeichen enthalten und ist auf 100 Zeichen beschränkt. Erwartete Werte:

    - Microsoft.VisualStudio.IntegratedShell

    - Microsoft.VisualStudio.Pro

    - Microsoft.VisualStudio.Premium

    - Microsoft.VisualStudio.Ultimate

    - Microsoft.VisualStudio.VWDExpress

    - Microsoft.VisualStudio.VPDExpress

    - Microsoft.VisualStudio.VSWinExpress

    - Microsoft.VisualStudio.VSLS

    - My.Shell.App

  - `Version`- Dieses Attribut gibt einen Versionsbereich mit den minimalen und maximal unterstützten Versionen dieser SKU an. Ein Paket kann die Versionen der unterstützten SKUs detailliert beschreiben. Die Versionsbereichsnotation ist [10.0 - 11.0], wobei

    - [ - Mindestversion inklusive.

    - ] - maximale Version inklusive.

    - ( - Exklusive Mindestversion.

    - ) - maximale Exklusive Version.

    - Einzelne Version - nur die angegebene Version.

    > [!IMPORTANT]
    > Version 2.0 des VSIX-Schemas wurde in Visual Studio 2012 eingeführt. Um dieses Schema verwenden zu können, müssen Sie Visual Studio 2012 oder höher auf dem Computer installiert haben und die VSIXInstaller.exe verwenden, die Teil dieses Produkts ist. Sie können frühere Versionen von Visual Studio mit einem Visual Studio 2012 oder höher VSIXInstaller zielen, jedoch nur mithilfe der späteren Versionen des Installationsprogramms.

    Visual Studio 2017 Versionsnummern finden Sie unter [Visual Studio Buildnummern und Veröffentlichungsdaten](../install/visual-studio-build-numbers-and-release-dates.md).

    Beim Ausdrücken der Version für Visual Studio 2017-Versionen sollte die Nebenversion immer **0**sein. Visual Studio 2017 Version 15.3.26730.0 sollte beispielsweise als [15.0.26730.0,16.0) ausgedrückt werden. Dies ist nur für Visual Studio 2017 und neuere Versionsnummern erforderlich.

  - `AnyAttribute*`- `<InstallationTarget>` Das Element ermöglicht einen offenen Satz von Attributen, der zur Laufzeit als Name-Wert-Paarwörterbuch verfügbar gemacht wird.

### <a name="dependencies-element"></a>Abhängigkeitselement
 Dieses Element enthält eine Liste der Abhängigkeiten, die dieses Paket deklariert. Wenn Abhängigkeiten angegeben werden, müssen diese `Id`Pakete (die durch ihre identifiziert wurden) bereits zuvor installiert worden sein.

- `<Dependency>`element - Dieses untergeordnete Element hat die folgenden Attribute:

  - `Id`- Dieses Attribut muss eine eindeutige ID für das abhängige Paket sein. Dieser Identitätswert `<Metadata><Identity>Id` muss mit dem Attribut eines Pakets übereinstimmen, von dem dieses Paket abhängig ist. Das `Id` Attribut folgt der Namespacekonvention: Company.Product.Feature.Name. Das Attribut darf nur alphanumerische Zeichen enthalten und ist auf 100 Zeichen beschränkt.

  - `Version`- Dieses Attribut gibt einen Versionsbereich mit den minimalen und maximal unterstützten Versionen dieser SKU an. Ein Paket kann die Versionen der unterstützten SKUs detailliert beschreiben. Die Versionsbereichsnotation ist [12.0, 13.0], wobei:

    - [ - Mindestversion inklusive.

    - ] - maximale Version inklusive.

    - ( - Exklusive Mindestversion.

    - ) - maximale Exklusive Version.

    - Einzelne Version - nur die angegebene Version.

  - `DisplayName`- Dieses Attribut ist der Anzeigename des abhängigen Pakets, der in UI-Elementen wie Dialogfeldern und Fehlermeldungen verwendet wird. Das Attribut ist optional, es sei denn, das abhängige Paket wird von MSI installiert.

  - `Location`- Dieses optionale Attribut gibt entweder den relativen Pfad innerhalb dieses VSIX zu einem geschachtelten VSIX-Paket oder eine URL zum Downloadspeicherort für die Abhängigkeit an. Dieses Attribut wird verwendet, um dem Benutzer zu helfen, das erforderliche Paket zu finden.

  - `AnyAttribute*`- `Dependency` Das Element akzeptiert einen offenen Satz von Attributen, die zur Laufzeit als Name-Wert-Paarwörterbuch verfügbar gemacht werden.

### <a name="assets-element"></a>Assets-Element
 Dieses Element enthält `<Asset>` eine Liste von Tags für jede Erweiterung oder jedes Inhaltselement, die von diesem Paket angezeigt werden.

- `<Asset>`- Dieses Element enthält die folgenden Attribute und Elemente:

  - `Type`- Art der Erweiterung oder des Inhalts, der durch dieses Element dargestellt wird. Jedes `<Asset>` Element muss `Type`über ein `<Asset>` einzelnes verfügen, aber mehrere Elemente können dass. `Type` Dieses Attribut sollte gemäß Namespacekonventionen als vollqualifizierter Name dargestellt werden. Die bekannten Typen sind:

    1. Microsoft.VisualStudio.VsPackage

    2. Microsoft.VisualStudio.MefComponent

    3. Microsoft.VisualStudio.ToolboxControl

    4. Microsoft.VisualStudio.Samples

    5. Microsoft.VisualStudio.ProjectTemplate

    6. Microsoft.VisualStudio.ItemTemplate

    7. Microsoft.VisualStudio.Assembly

       Sie können eigene Typen erstellen und ihnen eindeutige Namen geben. Zur Laufzeit in Visual Studio kann Ihr Code diese benutzerdefinierten Typen über die Extension Manager-API aufzählen und darauf zugreifen.

  - `Path`- der relative Pfad zur Datei oder zum Ordner innerhalb des Pakets, das das Asset enthält.

  - `TargetVersion`- den Versionsbereich, auf den das angegebene Asset anwendung. Wird für den Versand mehrerer Versionen von Assets an verschiedene Versionen von Visual Studio verwendet. Visual Studio 2017.3 oder neuer muss wirkungslos sein.

  - `AnyAttribute*`- Ein offener Satz von Attributen, der zur Laufzeit als Name-Wert-Paarwörterbuch verfügbar gemacht wird.

    `<AnyElement>*`- Jeder strukturierte Inhalt `<Asset>` ist zwischen einem Anfangs- und End-Tag zulässig. Alle Elemente werden als Liste von XmlElement-Objekten verfügbar gemacht. VSIX-Erweiterungen können strukturierte typspezifische Metadaten in der Manifestdatei definieren und zur Laufzeit aufzählen.

### <a name="sample-manifest"></a>Beispielmanifest

```xml
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

## <a name="see-also"></a>Weitere Informationen

- [Visual Studio-Erweiterungen versenden](../extensibility/shipping-visual-studio-extensions.md)
