---
title: VSIX-Manifest-Designer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85b9d20dd67ff11f5bded7060440f2e768a205a9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722862"
---
# <a name="vsix-manifest-designer"></a>VSIX-Manifest-Designer
Ändert eine VSIX-Paket-manifest-Datei, die legt das Verhalten bei der Installation für Visual Studio-Erweiterung.

 Die **VSIX-Manifest-Designer** ordnet das zugrunde liegende VSIX-Schema. Jedes Element im Schema kann mithilfe eines entsprechenden Steuerelements im Designer festgelegt werden. Weitere Informationen zum Schema finden Sie unter [Referenz zum VSIX-Erweiterungsschema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).

 Zum Öffnen der **VSIX-Manifest-Designer**, Suchen einer *"Source.Extension.vsixmanifest"* Datei **Projektmappen-Explorer**, und öffnen Sie die Datei. Wenn die Datei keine gültigen XML-Code enthält, wird nicht im manifest-Designer öffnen.

> [!NOTE]
>  Die *"Source.Extension.vsixmanifest"* wird in die Ausgabedatei zu *"Extension.vsixmanifest"* Wenn das Paket erstellt wurde.

## <a name="uielement-list"></a>UIElement-Liste
 Die **VSIX-Manifest-Designer** enthält vier Abschnitte, die diese Elemente der obersten Ebene des Schemas entsprechen:

- Metadaten

- Installationsziele

- Objekte

- Abhängigkeiten

  Der Überschriftenbereich enthält die folgenden Steuerelemente.

  **Produktname** beschreibt den Erweiterungsnamen.

  **Produkt-ID** gibt die eindeutige Kennung dieses Pakets an.

  **Autor** gibt den Namen des Autors der Erweiterung.

  **Version** gibt die Versionsnummer der Erweiterung.

  Die **Metadaten** Registerkarte enthält die folgenden Steuerelemente.

  **Beschreibung** stellt eine textbeschreibung der Erweiterung anzuzeigenden **Erweiterungs-Manager**.

  **Sprache** gibt die Standardsprache für das Paket, die die Textdaten im Manifest entspricht. Die `Language` -Attribut den common Language Runtime (CLR) Gebietsschema Code Konvention folgt der Ressourcenassemblys, z. B. En-us, En, fr-fr. Standardmäßig ist der Wert neutral zurückgesetzt, was bedeutet, dass das Paket auf eine beliebige Sprachversion von Visual Studio ausgeführt wird.

  **Lizenz** die Textdatei, die die Benutzerlizenz enthält gibt an, wenn ein solcher vorhanden ist.

  **Symbol "** gibt an, die Grafikdatei (*PNG*, *BMP*, *JPEG*, *ICO*), enthält das Symbol, um die in angezeigt werden **Erweiterungs-Manager**, wenn ein Symbol vorhanden ist. Das Symbolbild muss 32 x 32 Pixel oder es ist Größe auf diese. Wenn kein Symbol angegeben wird, **Erweiterungs-Manager** ein Standardsymbol verwendet.

  **Vorschaubild** gibt an, die Grafikdatei (*PNG*, *BMP*, *JPEG*, *ICO*), enthält das Vorschaubild, angezeigt **Erweiterungs-Manager**, wenn ein Vorschaubild vorhanden ist. Das Vorschaubild muss sich auf 200 x 200 Pixel. Wenn kein Vorschaubild angegeben wird, **Erweiterungs-Manager** ein Standardbild verwendet.

  **Tags** fügt die für suchhinweise verwendet werden soll.

  **Anmerkungen zu dieser Version** gibt eine Datei (*.txt*, *RTF*), die Anmerkungen zu dieser Version enthält. Es kann sich dabei auch um die URL einer Website handeln, auf der die Anmerkungen zu diesem Release enthalten sind.

  **Leitfaden für erste Schritte** gibt eine Datei (*.txt*, *RTF*), die Informationen zur Verwendung der Erweiterung oder den Inhalt im VSIX-Paket enthält. Dieses Handbuch wird angezeigt, wenn die Erweiterungsinstallation abgeschlossen ist. Nimmt auch die URL einer Website, die im Handbuch anzeigt.

  **URL mit weiteren Informationen** gibt die URL einer Website, die zusätzliche Informationen über das Produkt enthält.

  Die **Ziele installieren** Registerkarte enthält die folgenden Steuerelemente.

  **Installationstyp** listet **Visual Studio-Erweiterung** und **Erweiterungs-SDK** als Installationstypen abzielen. Die Optionen unterscheiden sich je nach Typ, den Sie auswählen.

  **Visual Studio-Erweiterung** Listet die **"installationtarget"** Elemente, die beschreiben, wie das Paket kann installiert werden und kann diese Erweiterung in der Visual Studio-Produkte installiert werden. Jedes Produkt wird separat von Namen und eine Version oder die Version Bereich identifiziert. Produkte können der Liste hinzugefügt, geändert und gelöscht werden. Der Name und die Version eines Produkts entsprechen den **Id** und **Version** Attribute des zugeordneten **"installationtarget"** Element.

  **Versionsbereich** ist ["12.0", "14.0"] und die folgende Notation verwendet:

- [-Mindestversion inklusive

- ] – einschließlich-Maximalversion

- (-Mindestversion, die exklusive

- ) – maximale Version des exklusiven

- Einzelne Version # - nur die angegebene Version

  **Erweiterungs-SDK** eine globale Installation, die auf ein bestimmtes Produkt und eine Version begrenzt ist nicht angegeben. **Bezeichner der Zielplattform** ist eine Plattform, z. B. "Windows", die Sie abzielen. **Version der Zielplattform** ist die Version, z.B. 8.0, von der Zielplattform. **SDK-Name** und **SDK-Version** sind bzw. den Namen und die Versionsnummer des SDK.

  **Diese VSIX ist installiert, für alle Benutzer (erfordert rechteerweiterungen, bei der Installation)** , wenn Sie dieses Kontrollkästchen aktivieren, wird die Erweiterung für alle Benutzer installiert; andernfalls ist es nur für den aktuellen Benutzer installiert.

  **Diese VSIX ist installiert, mit Windows Installer** , wenn Sie dieses Kontrollkästchen aktivieren, wird die Erweiterung installiert, von der Windows Installer (*MSI* Datei) ist, andernfalls als typisches VSIX-Paket installiert (*VSIX*  Datei).

  Die **Assets** Registerkarte enthält die folgenden Steuerelemente.

  **Liste von Beständen** werden die Asset-Elemente, die beschreiben, die Erweiterung oder des Inhalts-Elemente aufgelistet, die dieses Paket Flächen. Jede Erweiterung oder Content-Element wird von der Quelle und Typ Pfad separat aufgeführt. Erweiterungen und Content-Elemente können zur Liste hinzugefügt, geändert und gelöscht werden. Den Typ und den Pfad eines Elements Erweiterung oder Inhalt entspricht der `Type` und `Path` Attribute des zugeordneten `Asset` Element. Die folgenden Typen werden unterstützt:

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

  **Namen, Quelle und Versionsbereich** enthält die Abhängigkeitselemente dieses Pakets, die andere Pakete sind, von denen dieses Paket abhängt. Wenn ein abhängigkeitspaket angegeben wird, muss es vor der Installation dieses Pakets installiert werden. Andernfalls müssen sie dieses Paket installieren.

  Abhängigkeitspakete werden angegeben ID, Name, Versionsbereich, Quelle und wie die Abhängigkeit ist, aufgelöst werden sollen. Jedes abhängigkeitspaket wird nach Name, Version und die Datenquelle separat aufgeführt. Abhängigkeitspakete können der Liste hinzugefügt, geändert und gelöscht werden.

  Der Bezeichner muss übereinstimmen. die `ID` Attribut die Metadaten-Paket. Die Quelle kann es sich um ein Projekt in der aktuellen Projektmappe, die eine installierte Erweiterung oder eine Datei sein. Die **wie Abhängigkeit aufgelöst wird** Einstellung kann der relative Pfad eines verschachtelten Pakets oder die URL der Speicherort des Downloads für die Abhängigkeit sein. Die ID, die Version und die Auflösung des abhängigkeitspakets entsprechen den `Id`, `Version`, und `Location` Attribute des zugeordneten `Dependency` Element.

## <a name="see-also"></a>Siehe auch
- [Referenz zum VSIX-Erweiterung Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)