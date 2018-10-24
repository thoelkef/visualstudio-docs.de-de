---
title: VSIX-Manifest-Designer | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c2648b237cbe2dd2cbaab28b94de68752bb596f0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49843781"
---
# <a name="vsix-manifest-designer"></a>VSIX-Manifest-Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ändert eine VSIX-Paket-manifest-Datei, die legt das Verhalten bei der Installation für Visual Studio-Erweiterung.  
  
 Die **VSIX-Manifest-Designer** ordnet das zugrunde liegende VSIX-Schema. Jedes Element im Schema kann mithilfe eines entsprechenden Steuerelements im Designer festgelegt werden. Weitere Informationen zum Schema finden Sie unter [Referenz zum VSIX-Erweiterungsschema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Zum Öffnen der **VSIX-Manifest-Designer**, suchen Sie eine Datei "Source.Extension.vsixmanifest" in **Projektmappen-Explorer**, und öffnen Sie die Datei. Wenn die Datei keine gültigen XML-Code enthält, wird der manifest-Designer nicht geöffnet werden.  
  
> [!NOTE]
>  "Source.Extension.vsixmanifest" wird an "Extension.vsixmanifest" ausgegeben, wenn das Paket erstellt wird.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 Die **VSIX-Manifest-Designer** enthält vier Abschnitte, die diese Elemente der obersten Ebene des Schemas entsprechen:  
  
- Metadaten  
  
- Installationsziele  
  
- Objekte  
  
- Abhängigkeiten  
  
  Der Überschriftenbereich enthält die folgenden Steuerelemente.  
  
  **Produktname**  
  Beschreibt, der Name der Erweiterung.  
  
  **Produkt-ID**  
  Gibt die eindeutige ID-Informationen für dieses Paket.  
  
  **Autor**  
  Gibt den Namen des Autors der Erweiterung.  
  
  **Version**  
  Gibt die Versionsnummer der Erweiterung an.  
  
  Die **Metadaten** Registerkarte enthält die folgenden Steuerelemente.  
  
  **Beschreibung**  
  Stellt eine textbeschreibung der Erweiterung anzuzeigenden **Erweiterungs-Manager**.  
  
  **Sprache**  
  Gibt die Standardsprache für das Paket, das Textdaten im Manifest entspricht. Die `Language` -Attribut den common Language Runtime (CLR) Gebietsschema Code Konvention folgt der Ressourcenassemblys, z. B. En-us, En, fr-fr. Standardmäßig ist der Wert neutral. Dies bedeutet, dass das Paket auf eine beliebige Sprachversion von Visual Studio ausgeführt wird.  
  
  **Lizenz**  
  Gibt die Textdatei, die die Benutzerlizenz enthält, sofern vorhanden.  
  
  **Symbol**  
  Gibt an, die Grafikdatei (PNG, BMP, JPEG, .ico) mit dem Symbol anzuzeigenden enthält **Erweiterungs-Manager**, wenn ein Symbol vorhanden ist. Das Symbolbild muss 32 x 32 Pixel oder es wird auf diese Größe geändert werden. Wenn kein Symbol angegeben wird, **Erweiterungs-Manager** ein Standardsymbol verwendet.  
  
  **Vorschaubild**  
  Gibt die Grafikdatei (PNG, BMP, JPEG, .ico) an, die das Vorschaubild anzuzeigenden enthält **Erweiterungs-Manager**, wenn ein Vorschaubild vorhanden ist. Das Vorschaubild muss sich auf 200 x 200 Pixel. Wenn kein Vorschaubild angegeben wird, **Erweiterungs-Manager** ein Standardbild verwendet.  
  
  **Tags**  
  Fügt die für suchhinweise verwendet werden soll.  
  
  **Anmerkungen zu dieser Version**  
  Gibt eine Datei (".txt", "RTF"), die Anmerkungen zu dieser Version enthält. Es kann sich dabei auch um die URL einer Website handeln, auf der die Anmerkungen zu diesem Release enthalten sind.  
  
  **Handbuch mit ersten Schritten**  
  Gibt eine Datei (".txt", "RTF"), die Informationen zur Verwendung der Erweiterung oder den Inhalt im VSIX-Paket enthält. Dieses Handbuch wird angezeigt, wenn die Erweiterungsinstallation abgeschlossen ist. Nimmt auch die URL einer Website, die im Handbuch anzeigt.  
  
  **URL mit weiteren Informationen**  
  Gibt die URL einer Website, die zusätzliche Informationen über das Produkt enthält.  
  
  Die **Ziele installieren** Registerkarte enthält die folgenden Steuerelemente.  
  
  **Installationstyp**  
  Listet **Visual Studio-Erweiterung** und **Erweiterungs-SDK** als Installationstypen abzielen. Die Optionen unterscheiden sich je nach Typ, den Sie auswählen.  
  
  **Visual Studio-Erweiterung**  
  Listet die **"installationtarget"** Elemente, die beschreiben, wie das Paket kann installiert werden und kann diese Erweiterung in der Visual Studio-Produkte installiert werden. Jedes Produkt wird separat von Namen und eine Version oder die Version Bereich identifiziert.  Produkte können der Liste hinzugefügt, geändert und gelöscht werden. Der Name und die Version eines Produkts entsprechen den **Id** und **Version** Attribute des zugeordneten **"installationtarget"** Element.  
  
  **Versionsbereich** ist ["12.0", "14.0"] und die folgende Notation verwendet:  
  
- [– einschließlich-Mindestversion  
  
- ] – einschließlich-Maximalversion  
  
- (-Mindestversion, die exklusive  
  
- ) – maximale Version des exklusiven  
  
- Einzelne Version # - nur die angegebene Version  
  
  **Erweiterungs-SDK**  
  Gibt eine globale Installation, die auf ein bestimmtes Produkt und eine Version begrenzt ist nicht an. **Bezeichner der Zielplattform** ist eine Plattform, z. B. "Windows", die Sie abzielen. **Version der Zielplattform** ist die Version, z.B. 8.0, von der Zielplattform. **SDK-Name** und **SDK-Version** sind bzw. den Namen und die Versionsnummer des SDK.  
  
  **Diese VSIX ist installiert, für alle Benutzer (erfordert rechteerweiterungen, bei der Installation)** Kontrollkästchen  
  Wenn dieses Kontrollkästchen ausgewählt ist, wird diese Erweiterung für alle Benutzer installiert. Andernfalls wird es nur für den aktuellen Benutzer installiert.  
  
  **Diese VSIX ist installiert, mit Windows Installer** Kontrollkästchen  
  Wenn dieses Kontrollkästchen ausgewählt ist, wird diese Erweiterung durch die Windows Installer (MSI-Datei) installiert. Andernfalls wird es als typisches VSIX-Paket (VSIX-Datei) installiert.  
  
  Die **Assets** Registerkarte enthält die folgenden Steuerelemente.  
  
  **Liste von Beständen**  
  Werden die Asset-Elemente, die beschreiben, die Erweiterung oder des Inhalts-Elemente aufgelistet, die dieses Paket Flächen. Jede Erweiterung oder Content-Element wird von der Quelle und Typ Pfad separat aufgeführt. Erweiterungen und Content-Elemente können zur Liste hinzugefügt, geändert und gelöscht werden. Den Typ und den Pfad eines Elements Erweiterung oder Inhalt entspricht der `Type` und `Path` Attribute des zugeordneten `Asset` Element. Die folgenden Typen werden unterstützt:  
  
- Microsoft.VisualStudio.Package  
  
- Microsoft.VisualStudio.MefComponent  
  
- Microsoft.VisualStudio.ToolboxControl  
  
- Microsoft.VisualStudio.Samples  
  
- Microsoft.VisualStudio.ProjectTemplate  
  
- Microsoft.VisualStudio.ItemTemplate  
  
- Microsoft.VisualStudio.Assembly  
  
- Microsoft.ExtensionSDK  
  
  Zum Hinzufügen oder bearbeiten ein Medienobjekt, müssen Sie die Objekttyp, angeben, ob das Objekt ein Projekt in der aktuellen Projektmappe oder eine Datei in das Dateisystem und den Namen des Projekts ist. Sie können auch den Namen des Ordners, in dem eingebettet werden angeben.  
  
  Sie können auch eigene Typen erstellen, und geben sie eindeutige Namen.  
  
  Die **Abhängigkeiten** Registerkarte enthält die folgenden Steuerelemente.  
  
  **Namen, Quelle und Versionsbereich**  
  Listet die Abhängigkeitselemente dieses Pakets, die andere Pakete sind, von denen dieses Paket abhängt. Wenn ein abhängigkeitspaket angegeben wird, muss es vor der Installation dieses Pakets installiert werden. Andernfalls müssen sie dieses Paket installieren.  
  
  Abhängigkeitspakete werden angegeben ID, Name, Versionsbereich, Quelle und wie die Abhängigkeit ist, aufgelöst werden sollen. Jedes abhängigkeitspaket wird nach Name, Version und die Datenquelle separat aufgeführt. Abhängigkeitspakete können der Liste hinzugefügt, geändert und gelöscht werden.  
  
  Der Bezeichner muss übereinstimmen. die `ID` Attribut die Metadaten-Paket. Die Quelle kann es sich um ein Projekt in der aktuellen Projektmappe, die eine installierte Erweiterung oder eine Datei sein. Die **wie Abhängigkeit aufgelöst wird** Einstellung kann der relative Pfad eines verschachtelten Pakets oder die URL der Speicherort des Downloads für die Abhängigkeit sein. Die ID, die Version und die Auflösung des abhängigkeitspakets entsprechen den `Id`, `Version`, und `Location` Attribute des zugeordneten `Dependency` Element.  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum VSIX-Erweiterung Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)

