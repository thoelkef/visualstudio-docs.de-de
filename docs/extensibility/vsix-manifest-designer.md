---
title: VSIX-Manifest-Designer | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eaf35854aede65b605b4578ca9ee71375ad7a479
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="vsix-manifest-designer"></a>VSIX-Manifest-Designer
Ändert eine VSIX-Paket-manifest-Datei, die das Installationsverhalten für eine Visual Studio-Erweiterung legt fest.  
  
 Die **VSIX-Manifest-Designer** ordnet das zugrunde liegende VSIX-Schema. Jedes Element im Schema kann mithilfe eines entsprechenden Steuerelements im Designer festgelegt werden. Weitere Informationen zum Schema finden Sie unter [VSIX-Erweiterung 2.0 Schemareferenz](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 So öffnen die **VSIX-Manifest-Designer**, suchen Sie eine Datei "Source.Extension.vsixmanifest" im **Projektmappen-Explorer**, und öffnen Sie die Datei. Wenn die Datei keine gültigen XML-Code enthält, wird der manifest-Designer nicht geöffnet werden.  
  
> [!NOTE]
>  "Source.Extension.vsixmanifest" ist die Ausgabe an "Extension.vsixmanifest", wenn das Paket erstellt wird.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 Die **VSIX-Manifest-Designer** enthält vier Abschnitte, die diese Elemente der obersten Ebene des Schemas entsprechen:  
  
-   Metadaten  
  
-   Installieren von Zielen  
  
-   Objekte  
  
-   Abhängigkeiten  
  
 Der Überschriftenbereich enthält die folgenden Steuerelemente.  
  
 **Produktname**  
 Beschreibt den Erweiterungsnamen an.  
  
 **Produkt-ID**  
 Gibt die eindeutige Kennung dieses Paket an.  
  
 **Autor**  
 Gibt den Namen des Autors der Erweiterung.  
  
 **Version**  
 Gibt die Versionsnummer der Erweiterung an.  
  
 Die **Metadaten** Registerkarte enthält die folgenden Steuerelemente.  
  
 **Beschreibung**  
 Bietet eine textbeschreibung der Erweiterung angezeigt werden **Erweiterungs-Manager**.  
  
 **Sprache**  
 Gibt die Standardsprache für das Paket, die die Textdaten in das Manifest entspricht. Die `Language` Attribut folgt die common Language Runtime (CLR) Gebietsschema Code Konvention für Ressourcenassemblys, z. B. de-de, En, fr-fr. Standardmäßig ist der Wert neutrale; Dies bedeutet, dass das Paket auf eine beliebige Sprachversion von Visual Studio ausgeführt wird.  
  
 **Lizenz**  
 Gibt die Textdatei, die die Benutzerlizenz enthält, sofern eins vorhanden ist.  
  
 **Symbol**  
 Gibt die Grafikdatei (PNG, BMP, JPEG, .ico) mit dem Symbol anzuzeigenden enthält **Erweiterungs-Manager**, wenn ein Symbol vorhanden ist. Das Symbolbild muss 32 x 32 Pixel oder wird für diese Dimensionen Größe geändert werden. Wenn kein Symbol angegeben wird, **Erweiterungs-Manager** ein Standardsymbol verwendet.  
  
 **Vorschaubild**  
 Gibt die Grafikdatei (PNG, BMP, JPEG, ICO), die das Vorschaubild anzuzeigenden enthält **Erweiterungs-Manager**, sofern ein Vorschaubild vorhanden ist. Das Vorschaubild muss 200 x 200 Pixel. Wenn kein Vorschaubild angegeben wird, **Erweiterungs-Manager** einem Standardbild verwendet.  
  
 **RFID-Transponder**  
 Fügt die für suchhinweise verwendet werden soll.  
  
 **Anmerkungen zu dieser Version**  
 Gibt eine Datei (".txt", RTF), die Anmerkungen zu dieser Version enthält. Es kann sich dabei auch um die URL einer Website handeln, auf der die Anmerkungen zu diesem Release enthalten sind.  
  
 **Handbuch mit ersten Schritten**  
 Gibt eine Datei (".txt", RTF), die Informationen zur Verwendung der Erweiterung oder des Inhalts im VSIX-Paket enthält. Diese Anleitung wird angezeigt, wenn die Erweiterungsinstallation abgeschlossen ist. Nimmt auch die URL einer Website, die im Handbuch anzeigt.  
  
 **URL mit weiteren Informationen**  
 Gibt die URL einer Website, die zusätzliche Informationen über das Produkt enthält.  
  
 Die **Ziele installieren** Registerkarte enthält die folgenden Steuerelemente.  
  
 **Installationstyp**  
 Listet **Visual Studio-Erweiterung** und **Erweiterungs-SDK** als Zielserver Installationstypen. Die Optionen unterscheiden sich je nach Typ, den Sie auswählen.  
  
 **Visual Studio-Erweiterung**  
 Listet die **InstallationTarget** Elemente, die beschreiben, wie das Paket kann installiert werden und kann diese Erweiterung in der Visual Studio-Produkte installiert werden. Jedes Produkt wird separat von Namen und eine Version oder die Version Bereich identifiziert.  Produkte können zur Liste hinzugefügt, geändert und gelöscht werden. Der Name und die Version eines Produkts entsprechen den **Id** und **Version** Attribute des zugeordneten **InstallationTarget** Element.  
  
 **Versionsbereich** ist [12.0, 14.0] und die folgende Notation verwendet:  
  
-   [-Mindestversion inklusive  
  
-   ]-Maximalversion inklusive  
  
-   (-Mindestversion exklusive  
  
-   ) – maximale Version exklusive  
  
-   Die Version mit einem # - nur die angegebene Version  
  
 **Erweiterungs-SDK**  
 Gibt eine globale Installation, die für ein bestimmtes Produkt und eine Version definiert ist nicht an. **Ziel Plattformbezeichner** ist die Plattform, z. B. "Windows", die Sie als Ziel bestimmen. **Version der Plattform als Ziel** ist die Version, z. B. 8.0, der Zielplattform. **SDK-Name** und **SDK-Version** sind die jeweils den Namen und die Versionsnummer des SDK.  
  
 **Diese VSIX ist installiert für alle Benutzer (erfordert erhöhte Rechte bei der Installation)** Kontrollkästchen  
 Wenn dieses Kontrollkästchen aktiviert ist, wird diese Erweiterung für alle Benutzer installiert. Andernfalls wird er nur für den aktuellen Benutzer installiert.  
  
 **Diese VSIX wurde mit Windows Installer installiert** Kontrollkästchen  
 Wenn dieses Kontrollkästchen aktiviert ist, wird diese Erweiterung von Windows Installer (MSI-Datei) installiert. Andernfalls wird er als typisches VSIX-Paket (VSIX-Datei) installiert.  
  
 Die **Bestand** Registerkarte enthält die folgenden Steuerelemente.  
  
 **Liste von Beständen**  
 Listet die Asset-Elemente, die die Erweiterung oder des Inhalts Elemente beschreiben, die von diesem Paket Oberflächen. Jede Erweiterung oder Content-Element wird von der Quelle, Typ und Pfad separat aufgeführt. Erweiterungen und Inhalt Elemente können zur Liste hinzugefügt, geändert und gelöscht werden. Entspricht der Typ und den Pfad eines Elements Erweiterung oder des Inhalts der `Type` und `Path` Attribute des zugeordneten `Asset` Element. Die folgenden Typen sind bekannt:  
  
-   Microsoft.VisualStudio.Package  
  
-   Microsoft.VisualStudio.MefComponent  
  
-   Microsoft.VisualStudio.ToolboxControl  
  
-   Microsoft.VisualStudio.Samples  
  
-   Microsoft.VisualStudio.ProjectTemplate  
  
-   Microsoft.VisualStudio.ItemTemplate  
  
-   Microsoft.VisualStudio.Assembly  
  
-   Microsoft.ExtensionSDK  
  
 Zum Hinzufügen oder Bearbeiten eines Medienobjekts, müssen Sie den Ressourcentyp angeben, ob die-Medienobjekt ein Projekt in der aktuellen Projektmappe oder eine Datei in das Dateisystem und den Namen des Projekts ist. Sie können auch den Namen des Ordners, in dem eingebettet werden angeben.  
  
 Sie können auch eigene erstellen und ihnen eindeutige Namen zuweisen.  
  
 Die **Abhängigkeiten** Registerkarte enthält die folgenden Steuerelemente.  
  
 **Namen, Quelle und Versionsbereich**  
 Listet die Abhängigkeitselemente für dieses Paket andere Pakete, denen dieses Paket abhängt. Eine abhängigkeitspakets angegeben wird, muss installiert sein, bevor dieses Paket installiert ist; Andernfalls müssen sie dieses Paket installieren.  
  
 Abhängigkeitspakete gemäß-ID, Name, Versionsbereich, Quelle und wie die Abhängigkeit ist, aufgelöst werden. Jedes Paket Abhängigkeit wird nach Name, Version und Quelle separat aufgeführt. Abhängigkeitspakete können zur Liste hinzugefügt, geändert und gelöscht werden.  
  
 Der Bezeichner muss übereinstimmen. die `ID` Attribut von der abhängigkeitsmetadaten für das Paket. Die Quelle kann es sich um ein Projekt in der aktuellen Projektmappe, die derzeit installierte Erweiterung oder eine Datei sein. Die **wie Abhängigkeit aufgelöst wird** Einstellung kann sein, den relativen Pfad eines geschachtelten Pakets oder die URL den Downloadpfad für die Abhängigkeit. Die ID, die Version und die Auflösung des abhängigkeitspakets entsprechen den `Id`, `Version`, und `Location` Attribute des zugeordneten `Dependency` Element.  
  
## <a name="see-also"></a>Siehe auch  
 [VSIX-Erweiterung Schemareferenz 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)