---
title: "VSIX-Erweiterung Schemareferenz 2.0 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSIX"
  - "Erweiterungsschema"
ms.assetid: 0da81b98-f5e3-40d3-ba9a-94551378d0b4
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# VSIX-Erweiterung Schemareferenz 2.0
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Eine VSIX\-Bereitstellung\-Manifestdatei beschreibt den Inhalt eines VSIX\-Pakets. Das Format wird durch ein Schema bestimmt. Version 2.0 von diesem Schema unterstützt das Hinzufügen von benutzerdefinierten Typen und Attribute.  Das Schema des Manifests ist erweiterbar. Das Manifeste Ladeprogramm ignoriert XML\-Elementen und Attributen, die nicht verstanden.  
  
> [!IMPORTANT]
>  Visual Studio 2015 können VSIX\-Dateien in den Visual Studio 2010, Visual Studio 2012 oder Visual Studio 2013 laden.  
  
## Paket\-Manifestschema  
 Ist das Stammelement des XML\-Manifestdatei `<PackageManifest>`, mit einem einzelnen Attribut `Version`, dies ist die Version der manifest\-Format. Wenn wesentliche Änderungen in das Format vorgenommen werden, wird das Versionsformat geändert. In diesem Thema wird beschrieben, Manifestformat Version 2.0, die im Manifest, durch Festlegen angegeben wird der `Version` \-Attribut auf den Wert Version \= "2.0".  
  
### PackageManifest\-Element  
 Innerhalb der `<PackageManifest>` Root\-Element können Sie die folgenden Elemente:  
  
-   `<Metadata>` \-Metadaten und Werbung Informationen über das Paket selbst. Nur ein `Metadata` Element ist im Manifest zulässig.  
  
-   `<Installation>` \-Dieser Abschnitt definiert, wie dieses Erweiterungspaket installiert werden kann, einschließlich der Anwendung\-SKUs, die sie installieren kann. Nur eine einzige `Installation` Element ist im Manifest zulässig. Ein Manifest benötigen Sie ein `Installation` Element oder das Paket kann nicht in einer beliebigen SKU installiert.  
  
-   `<Dependencies>` – Eine optionale Liste von Abhängigkeiten für dieses Paket werden hier definiert.  
  
-   `<Assets>` \-Dieser Abschnitt enthält alle in diesem Paket enthaltenen Objekte. Dieses Paket wird keine Inhalte Fläche, ohne in diesem Abschnitt.  
  
-   `<AnyElement>*` \-Die Manifestschema ist flexibel genug, um andere Elemente zu ermöglichen. Alle untergeordneten Elemente, die nicht vom Ladeprogramm Bereitstellungsmanifests erkannt werden als zusätzliche XmlElement\-Objekte in der Erweiterungs\-Manager\-API verfügbar gemacht. Mit dieser untergeordneten Elemente können VSIX\-Erweiterungen, zusätzliche Daten in der Manifestdatei definieren, die in Visual Studio ausgeführte Code zur Laufzeit zugreifen können. Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.AdditionalElements%2A> und <xref:Microsoft.VisualStudio.ExtensionManager.IExtension.LocalizedAdditionalElements%2A>.  
  
### Metadaten\-Element  
 In diesem Abschnitt werden die Metadaten über das Paket, dessen Identität und Werbung Informationen.`<Metadata>` enthält die folgenden Elemente:  
  
-   `<Identity>` \-ID\-Informationen für dieses Paket definiert und enthält die folgenden Attribute:  
  
    -   `Id` – Mit diesem Attribut muss eine eindeutige ID für das Paket vom Autor ausgewählt sein. Der Name sollte die gleiche Weise, die CLR\-Typen Namespaces sind qualifiziert werden: Company.Product.Feature.Name. Das `Id` \-Attribut ist auf 100 Zeichen beschränkt.  
  
    -   `Version` – Definiert die Version von diesem Paket und seinen Inhalt. Dieses Attribut entspricht dem CLR\-Assembly Versioning\-Format: "Hauptversion.Nebenversion.Build.Revision" \(1.2.40308.00\). Ein Paket mit einer höheren Versionsnummer Aktualisierungen des Pakets gilt, und über die vorhandene installierte Version installiert werden kann.  
  
    -   `Language` – Mit diesem Attribut wird die Standardsprache für das Paket und die Textdaten in diesem Manifest entspricht. Dieses Attribut folgt der CLR Gebietsschema Code\-Konvention für Ressourcenassemblys, zum Beispiel: En\-us, En, fr\-fr. Sie können angeben, `neutral` Erweiterung sprachneutrale deklarieren, die auf einer beliebigen Version von Visual Studio ausgeführt wird. Der Standardwert ist `neutral`.  
  
    -   `Publisher` – Dieses Attribut identifiziert den Herausgeber des Pakets, ein Unternehmen oder eine einzelne Name. Das `Publisher` \-Attribut ist auf 100 Zeichen beschränkt.  
  
-   `<DisplayName>` – Dieses Element gibt den benutzerfreundlichen Paketnamen, der in der UI Extension Manager angezeigt wird. Die `DisplayName` Inhalt ist auf 100 Zeichen beschränkt.  
  
-   `<Description>` \-Dieses optionale Element ist eine kurze Beschreibung des Pakets und dessen Inhalt, die im Extension Manager UI angezeigt wird. Die `Description` Inhalten Text, den Sie, aber es wurde auf 1000 Zeichen beschränkt.  
  
-   `<MoreInfo>` \-Dieses optionale Element ist eine URL zu einer Seite online, die eine vollständige Beschreibung des Pakets enthält. Das Protokoll muss als http angegeben werden.  
  
-   `<License>` \-Dieses optionale Element ist ein relativer Pfad in eine Lizenzdatei \(.txt, RTF\), die im Paket enthaltenen.  
  
-   `<ReleaseNotes>` \-Dieses optionale Element ist entweder einen relativen Pfad zu einer Release Notes\-Datei, die Bestandteil des Pakets \(.txt, RTF\), da sonst eine URL zu einer Website, die die Versionsinformationen anzeigt.  
  
-   `<Icon>` \-Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei \(Png, Bmp, Jpeg, Ico\), der im Paket enthaltenen. Das Symbolbild sollte 32 x 32 Pixel \(oder es wird auf diese Größe verkleinert werden\) und in "ListView"\-Benutzeroberfläche angezeigt wird. Wenn kein `Icon` Element angegeben ist, die Benutzeroberfläche ist der Standardwert.  
  
-   `<PreviewImage>` \-Dieses optionale Element ist ein relativer Pfad zu einer Bilddatei \(Png, Bmp, Jpeg\), der im Paket enthaltenen. Das Vorschaubild sollte 200 x 200 Pixel groß sein, und die Details\-Benutzeroberfläche angezeigt. Wenn kein `PreviewImage` Element angegeben ist, die Benutzeroberfläche ist der Standardwert.  
  
-   `<Tags>` \-Dieses optionale Element listet zusätzlichen durch Semikolons getrennten Text\-Tags, die für suchhinweise verwendet werden. Die `Tags` \-Elements ist auf 100 Zeichen beschränkt.  
  
-   `<GettingStartedGuide>` \-Dieses optionale Element ist entweder einen relativen Pfad zu einer HTML\-Datei oder eine URL zu einer Website, die Informationen zur Verwendung der Erweiterung oder des Inhalts dieses Pakets enthält. Dieses Handbuch ist als Teil einer Installation gestartet.  
  
-   `<AnyElement>*` \-Die Manifestschema ist flexibel genug, um andere Elemente zu ermöglichen. Keine untergeordneten Elemente, die vom Ladeprogramm Bereitstellungsmanifests erkannt werden, werden als Liste von XmlElement\-Objekte verfügbar gemacht. Verwenden diese untergeordneten Elemente, VSIX\-Erweiterungen zusätzliche Daten in der Manifestdatei zu definieren und zur Laufzeit aufzulisten.  
  
### Installation\-Element  
 Dieser Abschnitt definiert die Möglichkeit, die dieses Paket installiert werden kann und die Anwendung SKUs, die sie installieren kann. Dieser Abschnitt enthält die folgenden Attribute:  
  
-   `Experimental` – Legen Sie dieses Attribut auf true, wenn Sie eine Erweiterung, die derzeit für alle Benutzer installiert wird, aber Sie eine aktualisierte Version auf demselben Computer entwickeln. Zum Beispiel, wenn Sie Distance 1.0 für alle Benutzer installiert, aber möchten Distance 2.0 auf dem gleichen Computer zu debuggen, legen Sie die experimentelle \= "true". Dieses Attribut ist in Visual Studio 2015 Update 1 und höher verfügbar.  
  
-   `Scope` – Dieses Attribut kann den Wert "Global" oder "ProductExtension" nutzen:  
  
    -   "Global" gibt an, dass die Installation nicht auf eine bestimmte SKU begrenzt ist. Beispielsweise wird dieser Wert verwendet, wenn eine Erweiterung\-SDK installiert ist.  
  
    -   "ProductExtension" gibt an, dass eine einzelne Visual Studio\-SKUs Gültigkeitsbereich herkömmliche VSIX\-Erweiterung \(Version 1.0\) installiert ist. Dies ist der Standardwert.  
  
-   `AllUsers` – Dieses optionale Attribut gibt an, ob dieses Paket für alle Benutzer installiert werden soll. Standardmäßig ist dieses Attribut false gibt an, dass das Paket pro Benutzer. \(Wenn Sie diesen Wert auf "true" festlegen, muss der installierende Benutzer Administratorrechte auf die resultierende VSIX installiert erhöhen.  
  
-   `InstalledByMsi` – Dieses optionale Attribut gibt an, ob dieses Paket von einem MSI installiert wird. Pakete installiert, indem Sie eine MSI\-Datei installiert und von MSI \(Programme und Funktionen\) und nicht von der Visual Studio Extension Manager verwaltet werden.  Standardmäßig ist dieses Attribut false gibt an, dass das Paket durch eine MSI\-Datei nicht installiert ist.  
  
-   `SystemComponent` – Dieser optionale Attribut gibt an, ob dieses Paket eine Systemkomponente berücksichtigt werden soll. Systemkomponenten nicht in der UI Extension Manager anzeigen und können nicht aktualisiert werden. Standardmäßig ist dieses Attribut false gibt an, dass das Paket eine Systemkomponente ist.  
  
-   `AnyAttribute*` – Das `Installation` \-Element akzeptiert einen offenen Satz von Attributen, die zur Laufzeit als ein Wörterbuch mit Name\-Wert\-Paaren verfügbar gemacht werden.  
  
-   `<InstallationTarget>` – Dieses Element steuert den Speicherort, in dem das VSIX\-Installationsprogramm für das Paket installiert. Wenn der Wert der `Scope` Attribut ist "ProductExtension" das Paket muss als Ziel eine SKU, die eine Manifestdatei als Teil des Inhalts in seine Verfügbarkeit Erweiterungen ankündigen installiert wurde. Die `<InstallationTarget>` Element hat die folgenden Attribute, wenn die `Scope` Attribut hat den expliziten oder Standardwert "ProductExtension":  
  
    -   `Id` – Dieses Attribut identifiziert das Paket.  Das Attribut die Namespace\-Konvention folgt: Company.Product.Feature.Name. Das `Id` \-Attribut darf nur alphanumerische Zeichen enthalten und ist auf 100 Zeichen beschränkt. Erwartete Werte:  
  
        -   Microsoft.VisualStudio.IntegratedShell  
  
        -   Microsoft.VisualStudio.Pro  
  
        -   Microsoft.VisualStudio.Premium  
  
        -   Microsoft.VisualStudio.Ultimate  
  
        -   Microsoft.VisualStudio.VWDExpress  
  
        -   Microsoft.VisualStudio.VPDExpress  
  
        -   Microsoft.VisualStudio.VSWinExpress  
  
        -   Microsoft.VisualStudio.VSLS  
  
        -   My.Shell.App  
  
    -   `Version` – Dieses Attribut gibt einen Versionsbereich mit den minimalen und maximalen unterstützten Versionen dieser SKU. Ein Paket kann die Versionen der SKUs ausführlich beschrieben, die es unterstützt. Die Bereichsangabe Version ist \[10.0 – 11.0\], wo  
  
        -   \[– einschließlich Mindestversion.  
  
        -   \] – maximale Version liegen.  
  
        -   \(\-Mindestversion exklusiv.  
  
        -   \) – maximale Version exklusiv.  
  
        -   Die Version mit einem \# \- nur die angegebene Version.  
  
        > [!IMPORTANT]
        >  Version 2.0 des VSIX\-Schema wurde in Visual Studio 2012 eingeführt. Dieses Schema verwenden Sie benötigen Visual Studio 2012 oder höher auf dem Computer installiert und die VSIXInstaller.exe, die Teil des Produkts verwenden. Sie können frühere Versionen von Visual Studio mit einem Visual Studio 2012 oder höher VSIXInstaller, aber nur mit den neueren Versionen des Installationsprogramms.  
  
    -   `AnyAttribute*` – Das `<InstallationTarget>` \-Element können Sie einen offenen Satz von Attributen, die zur Laufzeit als ein Wörterbuch mit Name\-Wert\-Paaren verfügbar gemacht werden müssen.  
  
### Abhängigkeitselement  
 Dieses Element enthält eine Liste der Abhängigkeiten, die dieses Paket deklariert. Wenn Abhängigkeiten angegeben werden, diese Pakete \(anhand ihrer `Id`\) muss installiert wurde, bevor Sie.  
  
-   `<Dependency>` Element – dieses untergeordnete Element verfügt über die folgenden Attribute:  
  
    -   `Id` – Mit diesem Attribut muss eine eindeutige ID für das abhängige Paket sein. Dieser Identitätswert übereinstimmen der `<Metadata><Identity>Id` eines Pakets, das diesem Paket abhängig ist. Das `Id` \-Attribut die Namespace\-Konvention folgt: Company.Product.Feature.Name. Das Attribut darf nur alphanumerische Zeichen enthalten und ist auf 100 Zeichen beschränkt.  
  
    -   `Version` – Dieses Attribut gibt einen Versionsbereich mit den minimalen und maximalen unterstützten Versionen dieser SKU. Ein Paket kann die Versionen der SKUs ausführlich beschrieben, die es unterstützt. Die Version Bereich Notation ist \[12.0, 13,0\], wobei:  
  
        -   \[– einschließlich Mindestversion.  
  
        -   \] – maximale Version liegen.  
  
        -   \(\-Mindestversion exklusiv.  
  
        -   \) – maximale Version exklusiv.  
  
        -   Die Version mit einem \# \- nur die angegebene Version.  
  
    -   `DisplayName` – Dieses Attribut ist der Anzeigename des abhängigen Pakets die im UI\-Elemente wie z. B. Dialogfelder und Fehlermeldungen verwendet wird. Das Attribut ist optional, es sei denn, das abhängige Paket von MSI\-Datei installiert wird.  
  
    -   `Location` – Dieses optionale Attribut gibt den relativen Pfad innerhalb dieser VSIX einem geschachtelten VSIX\-Paket oder eine URL auf den Downloadspeicherort für die Abhängigkeit. Dieses Attribut wird verwendet, damit der Benutzer das erforderliche Paket nicht finden kann.  
  
    -   `AnyAttribute*` – Das `Dependency` \-Element akzeptiert einen offenen Satz von Attributen, die zur Laufzeit als ein Wörterbuch mit Name\-Wert\-Paaren verfügbar gemacht werden.  
  
### Anlagen\-Element  
 Dieses Element enthält eine Liste der `<Asset>` Tags für jedes Element Erweiterung oder des Inhalts von diesem Paket verfügbar gemacht.  
  
-   `<Asset>` – Dieses Element enthält die folgenden Attribute und Elemente:  
  
    -   `Type` – Dies ist der Typ der Erweiterung oder des Inhalts von diesem Element dargestellt. Jede `<Asset>` Element benötigen einen einzigen `Type`, aber mehrere `<Asset>` Elemente müssen die gleiche `Type`. Dieses Attribut sollte ein vollqualifizierter Name, gemäß Namespace Konventionen dargestellt werden. Die bekannten Typen sind:  
  
        1.  Microsoft.VisualStudio.VsPackage  
  
        2.  Microsoft.VisualStudio.MefComponent  
  
        3.  Microsoft.VisualStudio.ToolboxControl  
  
        4.  Microsoft.VisualStudio.Samples  
  
        5.  Microsoft.VisualStudio.ProjectTemplate  
  
        6.  Microsoft.VisualStudio.ItemTemplate  
  
        7.  Microsoft.VisualStudio.Assembly  
  
         Sie können eigene Typen erstellen und ihnen eindeutige Namen zuweisen. Zur Laufzeit in Visual Studio kann Code auflisten und Zugriff auf diese benutzerdefinierten Typen über die Extension Manager\-API.  
  
    -   Pfad – den relativen Pfad zur Datei oder eines Ordners innerhalb des Pakets, das die Anlage enthält.  
  
    -   `AnyAttribute*` – Ein offenen Satz von Attributen, die zur Laufzeit als ein Wörterbuch mit Name\-Wert\-Paaren verfügbar gemacht werden müssen.  
  
         `<AnyElement>*` – Alle strukturierten Inhalten kann zwischen einem `<Asset>` Begin\- und end\-Tag. Alle Elemente werden als eine Liste der XmlElement\-Objekte verfügbar gemacht. VSIX\-Erweiterungen können strukturierte typspezifische Metadaten in der Manifestdatei definieren und zur Laufzeit aufzulisten.  
  
### Beispiel\-Manifest  
  
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
  
## Siehe auch  
 [Lieferung von Visual Studio\-Erweiterungen](../extensibility/shipping-visual-studio-extensions.md)