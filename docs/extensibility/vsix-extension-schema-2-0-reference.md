---
title: VSIX-Erweiterung Schemareferenz 2.0 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- vsix
- extension schema
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7459b4292220e6bb1e5a00b912efe7eb99cce825
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31148648"
---
# <a name="vsix-extension-schema-20-reference"></a>VSIX-Erweiterung Schemareferenz 2.0
Eine VSIX-Bereitstellung-Manifestdatei beschreibt den Inhalt eines VSIX-Pakets. Das Dateiformat wird durch ein Schema gesteuert. Version 2.0 von diesem Schema unterstützt das Hinzufügen von benutzerdefinierten Typen und Attribute.  Das Schema des Manifests ist erweiterbar. Das manifest Ladeprogramm ignoriert XML-Elemente und Attribute, die sie nicht kennen.  
  
> [!IMPORTANT]
>  Visual Studio 2015 können VSIX-Dateien in den Formaten für Visual Studio 2010, Visual Studio 2012 oder Visual Studio 2013 laden.  
  
## <a name="package-manifest-schema"></a>Paket-Manifestschema  
 Ist das Stammelement der XML-Manifestdatei `<PackageManifest>`, mit einem einzelnen Attribut `Version`, dies ist die Version des manifest-Formats. Wenn größere Änderungen in das Format vorliegen, wird das Standardformat der Produktversion geändert werden. In diesem Thema wird beschrieben, Manifestformat Version 2.0, die im Manifest, durch Festlegen angegeben ist der `Version` -Attributs auf den Wert Version = "2.0".  
  
### <a name="packagemanifest-element"></a>PackageManifest-Element  
 Innerhalb der `<PackageManifest>` "Root"-Element können Sie die folgenden Elemente:  
  
-   `<Metadata>` -Metadaten und Werbung Informationen zu dem Paket selbst. Nur ein `Metadata` Element ist im Manifest zulässig.  
  
-   `<Installation>` – In diesem Abschnitt definiert die Art, die dieses Erweiterungspaket installiert werden kann, einschließlich der Anwendung-SKUs, die in die Installation durchführen können. Nur ein einzelner `Installation` Element ist im Manifest zulässig. Ein Manifest benötigen eine `Installation` Element oder dieses Paket kann nicht in einer anderen SKU installiert.  
  
-   `<Dependencies>` – Hier werden eine optionale Liste von Abhängigkeiten für dieses Paket definiert.  
  
-   `<Assets>` – Dieser Abschnitt enthält alle Objekte in diesem Paket enthalten sind. Dieses Paket wird keine Inhalte, die Entwurfsoberfläche, ohne in diesem Abschnitt.  
  
-   `<AnyElement>*` -Die Manifestschema ist flexibel genug, um andere Elemente zu ermöglichen. Alle untergeordneten Elemente, die nicht vom Ladeprogramm Bereitstellungsmanifests erkannt werden als zusätzliche XmlElement-Objekte in der Erweiterungs-Manager-API verfügbar gemacht. Verwenden diese untergeordneten Elemente, können VSIX-Erweiterungen, zusätzliche Daten in der Manifestdatei definieren, die in Visual Studio ausgeführte Code zur Laufzeit zugreifen können. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> und <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### <a name="metadata-element"></a>Metadaten-Element  
 In diesem Abschnitt sind die Metadaten zum Paket, dessen Identität und Informationen ankündigen. `<Metadata>` enthält die folgenden Elemente:  
  
-   `<Identity>` -Dies Identifikationsinformationen für dieses Paket definiert und enthält die folgenden Attribute:  
  
    -   `Id` – Dieses Attribut muss es sich um eine eindeutige ID für das Paket vom Autor ausgewählt sein. Der Name sollte die gleiche Weise wie CLR-Typen Serversteuerelement sind qualifiziert werden: Company.Product.Feature.Name. Die `Id` -Attribut darf maximal 100 Zeichen lang ist.  
  
    -   `Version` – Hiermit wird die Version der dieses Paket und dessen Inhalt definiert. Dieses Attribut weist das folgende CLR-Assembly Versioning Format: "Hauptversion.Nebenversion.Build.Revision" vorliegen (1.2.40308.00). Ein Paket mit einer höheren Versionsnummer Aktualisierungen des Pakets gilt und kann über die vorhandene installierte Version installiert werden.  
  
    -   `Language` – Dieses Attribut ist die Standardsprache für das Paket und dieses Manifest Textdaten entspricht. Dieses Attribut folgt die CLR Gebietsschema Code Konvention für Ressourcenassemblys, z. B.: de-de, En, fr-fr. Sie können angeben, `neutral` sinnvolles sprachneutrale deklarieren, die auf eine beliebige Version von Visual Studio ausgeführt wird. Der Standardwert ist `neutral`.  
  
    -   `Publisher` – Dieses Attribut identifiziert den Herausgeber des Pakets, ein Unternehmen oder die individuellen Namen. Die `Publisher` -Attribut darf maximal 100 Zeichen lang ist.  
  
-   `<DisplayName>` -Dieses Element gibt den benutzerfreundlichen Paketnamen, der in der Erweiterungs-Manager-UI angezeigt wird. Die `DisplayName` Inhalt ist auf 50 Zeichen begrenzt.  
  
-   `<Description>` -Dieses optionale Element ist eine kurze Beschreibung des Pakets und dessen Inhalt, die in UI Erweiterungs-Manager angezeigt wird. Die `Description` Inhalt kann Text, den Sie möchten, verfügt aber über enthalten auf 1000 Zeichen beschränkt.  
  
-   `<MoreInfo>` -Dieses optionale Element ist eine URL zu einer Seite online, die eine vollständige Beschreibung der dieses Paket enthält. Das Protokoll muss als http angegeben werden.  
  
-   `<License>` -Dieses optionale Element ist ein relativer Pfad auf eine im Paket enthaltenen Lizenzdatei (".txt", RTF).  
  
-   `<ReleaseNotes>` -Dieses optionale Element ist ein relativer Pfad zu einer Release Notes-Datei in das Paket (".txt", RTF), da sonst eine URL zu einer Website handeln, die Anmerkungen zu dieser Version sind, enthalten.  
  
-   `<Icon>` -Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei (Png, Bmp, Jpeg, Ico), der im Paket enthalten sind. Das Symbolbild muss 32 x 32 Pixel (oder wird auf diese Größe verkleinert werden) und in der Listenansicht UI wird angezeigt. Wenn kein `Icon` -Element angegeben wird, die Benutzeroberfläche verwendet den Standardwert.  
  
-   `<PreviewImage>` -Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei (Png, Bmp, Jpeg), der im Paket enthalten sind. Das Vorschaubild sollten 200 x 200 Pixel, und in den Details UI angezeigt. Wenn kein `PreviewImage` -Element angegeben wird, die Benutzeroberfläche verwendet den Standardwert.  
  
-   `<Tags>` -Dieses optionale Element listet zusätzlichen Text ein durch Semikolons getrennte-Tags, die für suchhinweise verwendet werden. Die `Tags` -Elements ist auf 100 Zeichen beschränkt.  
  
-   `<GettingStartedGuide>` -Dieses optionale Element ist entweder ein relativer Pfad in eine HTML-Datei oder eine URL zu einer Website, die Informationen zur Verwendung der Erweiterung oder dem Inhalt innerhalb dieses Paket enthält. Dieses Handbuch ist als Teil einer Installation gestartet.  
  
-   `<AnyElement>*` -Die Manifestschema ist flexibel genug, um andere Elemente zu ermöglichen. All seine untergeordneten Elemente, die vom Ladeprogramm Bereitstellungsmanifests erkannt werden, werden als eine Liste von Objekten XmlElement verfügbar gemacht. Verwenden diese untergeordneten Elemente, VSIX-Erweiterungen definieren zusätzliche Daten in der Manifestdatei und zur Laufzeit aufzulisten.  
  
### <a name="installation-element"></a>Installation-Element  
 Dieser Abschnitt definiert die Möglichkeit, die dieses Paket installiert werden kann, und die Anwendung-SKUs, die in die Installation durchführen können. Dieser Abschnitt enthält die folgenden Attribute:  
  
-   `Experimental` – Legen Sie dieses Attribut auf "true", wenn Sie eine Erweiterung, die zurzeit für alle Benutzer installiert wird, aber Sie eine aktualisierte Version auf demselben Computer entwickeln. Beispielsweise, wenn MyExtension 1.0 für alle Benutzer installiert haben, aber möchten MyExtension 2.0 auf dem gleichen Computer Debuggen, legen Sie die experimentelle = "true". Dieses Attribut ist in Visual Studio 2015 Update 1 und höher verfügbar.  
  
-   `Scope` – Dieses Attribut kann den Wert "Global" oder "ProductExtension" annehmen:  
  
    -   "Global" gibt an, dass die Installation nicht auf eine bestimmte SKU begrenzt ist. Beispielsweise wird dieser Wert verwendet, wenn eine Erweiterungs-SDK installiert ist.  
  
    -   "ProductExtension" gibt an, dass eine einzelne Visual Studio-SKUs Bereich herkömmlichen VSIX-Erweiterung (Version 1.0) installiert ist. Dies ist der Standardwert.  
  
-   `AllUsers` -Dieses optionale Attribut gibt an, ob dieses Paket für alle Benutzer installiert werden soll. Standardmäßig ist dieses Attribut "false" gibt an, dass das Paket pro Benutzer. (Wenn Sie diesen Wert auf "true" festlegen, muss der installierende Benutzer Administratorberechtigungen auf die resultierenden VSIX installieren erhöhen.  
  
-   `InstalledByMsi` -Dieses optionale Attribut gibt an, ob dieses Paket, indem eine MSI-Datei installiert ist. Pakete installiert, indem Sie eine MSI-Datei installiert und von MSI-Datei (Programme und Funktionen) und nicht durch den Visual Studio Erweiterungs-Manager verwaltet werden.  Standardmäßig ist dieses Attribut "false", der angibt, dass das Paket nicht durch eine MSI-Datei installiert wird.  
  
-   `SystemComponent` -Dieses optionale Attribut gibt an, ob dieses Paket eine Systemkomponente berücksichtigt werden sollten. Systemkomponenten nicht mehr in der Erweiterungs-Manager-UI anzeigen und können nicht aktualisiert werden. Standardmäßig ist dieses Attribut "false" gibt an, dass das Paket keine Systemkomponente ist.  
  
-   `AnyAttribute*` – Der `Installation` -Element akzeptiert einen offenen Satz von Attributen, die zur Laufzeit als ein Wörterbuch von Name / Wert-Paar verfügbar gemacht werden.  
  
-   `<InstallationTarget>` -Dieses Element steuert den Speicherort, in dem das VSIX-Installationsprogramm für das Paket installiert. Wenn der Wert der `Scope` -Attribut ist "ProductExtension" das Paket muss als Ziel eine SKU, die eine Manifestdatei als Teil des Inhalts in seine Verfügbarkeit Erweiterungen ankündigen installiert wurde. Die `<InstallationTarget>` Element verfügt über die folgenden Attribute, wenn die `Scope` Attribut hat den expliziten oder Standardwert "ProductExtension":  
  
    -   `Id` – Dieses Attribut identifiziert das Paket.  Das Attribut folgt der Konvention für den Verweisnamespace: Company.Product.Feature.Name. Die `Id` Attribut darf nur alphanumerische Zeichen und darf maximal 100 Zeichen lang ist. Erwartete Werte:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` – Dieses Attribut gibt einen Versionsbereich mit den minimalen und maximalen unterstützten Versionen dieser SKU. Ein Paket kann die Versionen von SKUs ausführlich beschrieben, die es unterstützt. Die Version bereichsschreibweise ist [10.0-11.0], in dem  
  
        -   [-Mindestversion inklusive.  
  
        -   ]-Maximalversion inklusive.  
  
        -   (-exklusive Mindestversion.  
  
        -   )-Maximalversion exklusiv.  
  
        -   Die Version mit einem # - nur die angegebene Version.  
  
        > [!IMPORTANT]
        >  Version 2.0 des VSIX-Schema wurde in Visual Studio 2012 eingeführt. Dieses Schema verwenden Sie benötigen Visual Studio 2012 oder höher auf dem Computer installiert und mit der VSIXInstaller.exe, das Bestandteil des Produkts ist. Sie können frühere Versionen von Visual Studio mit einem Visual Studio 2012 oder höher VSIXInstaller, jedoch nur mithilfe der höheren Versionen des Installationsprogramms.  
  
    -   `AnyAttribute*` – Der `<InstallationTarget>` -Element ermöglicht einen offenen Satz von Attributen, die zur Laufzeit als ein Wörterbuch von Name / Wert-Paar verfügbar gemacht werden müssen.  
  
### <a name="dependencies-element"></a>Dependencies-Element  
 Dieses Element enthält eine Liste der Abhängigkeiten, die dieses Paket deklariert. Wenn keine Abhängigkeiten angegeben sind, diese Pakete (identifizierte ihre `Id`) muss installiert wurde, bevor Sie.  
  
-   `<Dependency>` Element - dieses untergeordnete Element weist folgende Attribute:  
  
    -   `Id` – Dieses Attribut muss eine eindeutige ID für das abhängige Paket. Dieser Identitätswert übereinstimmen der `<Metadata><Identity>Id` Attribut eines Pakets, das dieses Paket abhängig ist. Die `Id` Attribut folgt der Konvention für den Verweisnamespace: Company.Product.Feature.Name. Das Attribut darf nur alphanumerische Zeichen und darf maximal 100 Zeichen lang ist.  
  
    -   `Version` – Dieses Attribut gibt einen Versionsbereich mit den minimalen und maximalen unterstützten Versionen dieser SKU. Ein Paket kann die Versionen von SKUs ausführlich beschrieben, die es unterstützt. Ist die Version bereichsschreibweise [12.0, 13.0], wobei:  
  
        -   [-Mindestversion inklusive.  
  
        -   ]-Maximalversion inklusive.  
  
        -   (-exklusive Mindestversion.  
  
        -   )-Maximalversion exklusiv.  
  
        -   Die Version mit einem # - nur die angegebene Version.  
  
    -   `DisplayName` – Dieses Attribut ist der Anzeigename, der das abhängige Paket die im UI-Elemente, z. B. Dialogfelder und Fehlermeldungen verwendet wird. Das Attribut ist optional, es sei denn, das abhängige Paket von MSI-Datei installiert wird.  
  
    -   `Location` -Dieses optionale Attribut gibt an, entweder der relative Pfad innerhalb dieser VSIX zu einem geschachtelten VSIX-Paket oder eine URL auf den Downloadpfad für die Abhängigkeit. Dieses Attribut wird verwendet, zu der Benutzer, die das erforderliche Paket zu suchen.  
  
    -   `AnyAttribute*` – Der `Dependency` -Element akzeptiert einen offenen Satz von Attributen, die zur Laufzeit als ein Wörterbuch von Name / Wert-Paar verfügbar gemacht werden.  
  
### <a name="assets-element"></a>Anlagen-Element  
 Dieses Element enthält eine Liste der `<Asset>` Tags für jedes Element-Erweiterung oder den Inhalt von diesem Paket angefügt.  
  
-   `<Asset>` -Dieses Element enthält die folgenden Attribute und Elemente:  
  
    -   `Type` -Dies ist der Typ der Erweiterung oder des Inhalts von diesem Element dargestellt. Jede `<Asset>` Element benötigen einen einzigen `Type`, aber mehrere `<Asset>` möglicherweise Elemente verfügen über denselben `Type`. Dieses Attribut sollte ein vollqualifizierter Name gemäß Namespace Konventionen dargestellt werden. Die bekannten Typen sind:  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.VisualStudio.ProjectTemplate  
  
        6.  Microsoft.VisualStudio.ItemTemplate  
  
        7.  Microsoft.VisualStudio.Assembly  
  
         Sie können eigene erstellen und ihnen eindeutige Namen zuweisen. Zur Laufzeit innerhalb von Visual Studio kann Codes auflisten und Zugriff auf diese benutzerdefinierten Typen über die Erweiterungs-Manager-API.  
  
    -   Pfad - der relative Pfad auf die Datei oder einen Ordner innerhalb des Pakets, das das Medienobjekt enthält.  
  
    -   `AnyAttribute*` -Einen offenen Satz Attribute, die zur Laufzeit als Name / Wert-Paar Wörterbuch verfügbar gemacht werden müssen.  
  
         `<AnyElement>*` – Beliebige strukturierter Inhalt ist zulässig, zwischen einer `<Asset>` beginnen und enden Tag. Alle Elemente werden als eine Liste von Objekten XmlElement verfügbar gemacht. VSIX-Erweiterungen können strukturierte typspezifische Metadaten in der Manifestdatei definieren und zur Laufzeit aufzulisten.  
  
### <a name="sample-manifest"></a>Beispiel-Manifest  
  
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
 [Bereitstellen von Visual Studio-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)