---
title: "VSIX-Manifest-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.Sdk.VsixManifestEditor"
helpviewer_keywords: 
  - "vsixmanifest"
  - "VSIX-manifest"
  - "Manifest-designer"
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# VSIX-Manifest-Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ändert eine VSIX\-Manifestdatei, die das Installationsverhalten für Visual Studio\-Erweiterung festlegt.  
  
 Die **VSIX\-Manifest\-Designer** ordnet das zugrunde liegende VSIX\-Schema. Jedes Element im Schema kann mithilfe eines entsprechenden Steuerelements im Designer festgelegt werden. Weitere Informationen zum Schema finden Sie unter [VSIX\-Erweiterung Schemareferenz 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Zum Öffnen der **VSIX\-Manifest\-Designer**, suchen Sie eine Datei "source.extension.vsixmanifest" im **Projektmappen\-Explorer**, und öffnen Sie die Datei. Wenn die Datei keine gültigen XML\-Code enthält, wird im manifest\-Designer nicht geöffnet werden.  
  
> [!NOTE]
>  "Source.Extension.vsixmanifest" wird in "Extension.vsixmanifest" ausgegeben, wenn das Paket erstellt wird.  
  
## UIElement-Liste  
 Die **VSIX\-Manifest\-Designer** enthält vier Abschnitte, die diese Elemente der obersten Ebene des Schemas entsprechen:  
  
-   Metadaten  
  
-   Installieren von Zielen  
  
-   Anlagen  
  
-   Abhängigkeiten  
  
 Der Überschriftenbereich enthält die folgenden Steuerelemente.  
  
 **Produktname**  
 Beschreibt den Erweiterungsnamen.  
  
 **Produkt\-ID**  
 Gibt die eindeutige ID\-Informationen für dieses Paket.  
  
 **Autor**  
 Gibt den Namen des Autors der Erweiterung.  
  
 **Version**  
 Gibt die Versionsnummer der Erweiterung.  
  
 Die **Metadaten** Registerkarte enthält die folgenden Steuerelemente.  
  
 **Beschreibung**  
 Enthält eine Beschreibung der Erweiterung anzuzeigenden **Extension Manager**.  
  
 **Sprache**  
 Gibt die Standardsprache für das Paket, das die Textdaten im Manifest entspricht. Die `Language` Attribut folgt den common Language Runtime \(CLR\) Gebietsschema Code Konvention für Ressourcenassemblys, z. B. En\-us, En, fr\-fr. Standardmäßig ist der Wert neutral. Dies bedeutet, dass das Paket auf eine beliebige Sprachversion von Visual Studio ausgeführt wird.  
  
 **Lizenz**  
 Gibt die Textdatei, die die Benutzer\-Lizenz enthält, sofern vorhanden.  
  
 **Symbol**  
 Gibt die Grafikdatei \(PNG, BMP, JPEG, ICO\) mit den anzuzeigenden **Extension Manager**, wenn ein Symbol vorhanden ist. Das Symbolbild muss 32 x 32 Pixel oder wird auf diese Größe geändert werden. Wenn kein Symbol angegeben wird, **Extension Manager** ein Standardsymbol verwendet.  
  
 **Vorschaubild**  
 Gibt die Grafikdatei \(PNG, BMP, JPEG, ICO\), die das Vorschaubild anzuzeigenden enthält **Extension Manager**, wenn ein Vorschaubild vorhanden ist. Das Vorschaubild muss 200 x 200 Pixel groß sein. Wenn kein Vorschaubild angegeben ist, **Extension Manager** ein Standardbild verwendet.  
  
 **Tags**  
 Fügt die für suchhinweise verwendet werden soll.  
  
 **Anmerkungen zu dieser Version**  
 Gibt eine Datei \(txt, RTF\), die Versionsinformationen enthält. Es kann sich dabei auch um die URL einer Website handeln, auf der die Anmerkungen zu diesem Release enthalten sind.  
  
 **Erste Schritte**  
 Gibt eine Datei \(txt, RTF\), die Informationen zur Verwendung der Erweiterung oder des Inhalts im VSIX\-Paket enthält. Dieses Handbuch wird angezeigt, wenn die Installation der Erweiterung abgeschlossen ist. Außerdem wird die URL einer Website, die im Handbuch zeigt.  
  
 **URL mit weiteren Informationen**  
 Gibt die URL einer Website, die zusätzliche Informationen über das Produkt enthält.  
  
 Die **Ziele installieren** Registerkarte enthält die folgenden Steuerelemente.  
  
 **Installationstyp**  
 Listet **Visual Studio\-Erweiterung** und **Erweiterung\-SDK** als Zielserver Installationstypen. Die Optionen unterscheiden sich je nach Typ, den Sie auswählen.  
  
 **Visual Studio\-Erweiterung**  
 Listet die **InstallationTarget** Elemente, die beschreiben, wie das Paket installiert werden kann, und kann diese Erweiterung in der Visual Studio\-Produkte installiert werden. Jedes Produkt wird separat durch Namen und eine Version oder die Version Bereich identifiziert.  Produkte können der Liste hinzugefügt, geändert und gelöscht werden. Der Name und die Version eines Produkts entsprechen den **Id** und **Version** Attribute des zugeordneten **InstallationTarget** Element.  
  
 **Versionsbereich** ist \[12.0, 14.0\] und die folgende Notation verwendet:  
  
-   \[– einschließlich Mindestversion  
  
-   \] – einschließlich maximale Version  
  
-   \(\-Mindestversion exklusive  
  
-   \) – maximale Version exklusive  
  
-   Die Version mit einem \# \- nur die angegebene Version  
  
 **SDK\-Erweiterung**  
 Gibt eine globale Installation, die für ein bestimmtes Produkt und eine Version definiert wird nicht an.**Ziel Plattformbezeichner** ist die Plattform, z. B. "Windows", die Sie entwickeln.**Version der Zielplattform** ist die Version, z. B. 8.0 der Zielplattform.**SDK Name** und **SDK\-Version** jeweils den Namen und die Versionsnummer des SDK.  
  
 **Diese VSIX ist installiert für alle Benutzer \(erfordert erhöhte Rechte bei der Installation\)** Kontrollkästchen  
 Wenn dieses Kontrollkästchen aktiviert ist, wird diese Erweiterung für alle Benutzer installiert. Andernfalls wird er nur für den aktuellen Benutzer installiert.  
  
 **Diese VSIX wurde mit Windows Installer installiert** Kontrollkästchen  
 Wenn dieses Kontrollkästchen aktiviert ist, wird diese Erweiterung von Windows Installer \(MSI\-Datei\) installiert. Andernfalls wird sie als typisches VSIX\-Paket \(VSIX\-Datei\) installiert.  
  
 Die **Elemente** Registerkarte enthält die folgenden Steuerelemente.  
  
 **Liste von Beständen**  
 Listet die Asset\-Elemente, die die Erweiterung oder des Inhalts Elemente beschreiben, die von diesem Paket Flächen. Jede Erweiterung oder Content\-Element wird von Quelle und Typ Pfad separat aufgeführt. Erweiterungen und Content\-Elemente können der Liste hinzugefügt, geändert und gelöscht werden. Entspricht den Typ und den Pfad eines Elements Erweiterung oder des Inhalts der `Type` und `Path` Attribute des zugeordneten `Asset` Element. Die folgenden Typen sind bekannt:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Zum Hinzufügen oder Bearbeiten eines Medienobjekts, müssen Sie den Asset\-Typ angeben, ob das Medienobjekt ein Projekt in der aktuellen Projektmappe oder eine Datei in das Dateisystem und den Namen des Projekts ist. Sie können auch den Namen des Ordners, in dem eingebettet werden angeben.  
  
 Sie können eigene Typen erstellen und ihnen eindeutige Namen zuweisen.  
  
 Die **Abhängigkeiten** Registerkarte enthält die folgenden Steuerelemente.  
  
 **Namen, Quelle und Version\-Bereich**  
 Gibt die Abhängigkeitselemente von diesem Paket andere Pakete, denen von diesem Paket abhängig ist. Wenn ein Paket Abhängigkeit angegeben wird, muss es vor der Installation dieses Pakets installiert werden. Andernfalls müssen sie dieses Paket installieren.  
  
 Abhängigkeitspakete werden angegeben ID, Name, Versionsbereich, Quelle und wie die Abhängigkeit vorhanden ist, nicht aufgelöst werden. Jedes Paket Abhängigkeit wird nach Name, Version und Quelle separat aufgeführt. Abhängigkeitspakete können der Liste hinzugefügt, geändert und gelöscht werden.  
  
 Der Bezeichner muss entsprechen der `ID` \-Attribut des Pakets die Metadaten. Die Quelle kann es sich um ein Projekt in der aktuellen Projektmappe, eine aktuell installierte Erweiterung oder eine Datei sein. Die **wie Abhängigkeit aufgelöst wird** Einstellung kann den relativen Pfad eines verschachtelten Pakets oder die URL den Downloadpfad für die Abhängigkeit sein. Die ID, die Version und die Auflösung des abhängigkeitspakets entsprechen den `Id`, `Version`, und `Location` Attribute des zugeordneten `Dependency` Element.  
  
## Siehe auch  
 [VSIX\-Erweiterung Schemareferenz 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomie eines VSIX\-Pakets](../extensibility/anatomy-of-a-vsix-package.md)