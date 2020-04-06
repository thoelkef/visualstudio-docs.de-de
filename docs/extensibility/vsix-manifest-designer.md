---
title: VSIX-Manifest-Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697898"
---
# <a name="vsix-manifest-designer"></a>VSIX-Manifest-Designer
Ändert eine VSIX-Paketmanifestdatei, die das Installationsverhalten für eine Visual Studio-Erweiterung festlegt.

 Der **VSIX-Manifest-Designer** ordnet dem zugrunde liegenden VSIX-Schema zu. Jedes Element im Schema kann mithilfe eines entsprechenden Steuerelements im Designer festgelegt werden. Weitere Informationen zum Schema finden Sie unter [VSIX Extension Schema 2.0 Reference](../extensibility/vsix-extension-schema-2-0-reference.md).

 Um den **VSIX-Manifest-Designer zu**öffnen, suchen Sie eine *source.extension.vsixmanifest-Datei* im **Projektmappen-Explorer**, und öffnen Sie die Datei. Wenn die Datei keinen gültigen XML-Code enthält, wird der Manifest-Designer nicht geöffnet.

> [!NOTE]
> Die Datei *source.extension.vsixmanifest* wird an *extension.vsixmanifest* ausgegeben, wenn das Paket erstellt wird.

## <a name="uielement-list"></a>UIElement-Liste
 Der **VSIX-Manifest-Designer** enthält vier Abschnitte, die diesen Elementen der obersten Ebene des Schemas entsprechen:

- Metadaten

- Installationsziele

- Objekte

- Abhängigkeiten

  Der Überschriftenbereich enthält die folgenden Steuerelemente.

  **Produktname** Beschreibt den Erweiterungsnamen.

  **Produkt-ID** Gibt die eindeutigen Identifikationsinformationen für dieses Paket an.

  **Autor** Gibt den Namen des Autors der Erweiterung an.

  **Version** Gibt die Versionsnummer der Erweiterung an.

  Die Registerkarte **Metadaten** enthält die folgenden Steuerelemente.

  **Beschreibung** Enthält eine Textbeschreibung der Erweiterung, die im **Erweiterungs-Manager**angezeigt werden soll.

  **Sprache** Gibt die Standardsprache für das Paket an, die den Textdaten im Manifest entspricht. Das `Language` Attribut folgt der COMMON Language Runtime (CLR)-Gebietsschemacodekonvention für Ressourcenassemblys, z. B. en-us, en, fr-fr. Standardmäßig ist der Wert neutral, d. h., das Paket wird auf jeder Sprachversion von Visual Studio ausgeführt.

  **Lizenz** Gibt die Textdatei an, die die Benutzerlizenz enthält, sofern vorhanden.

  **Icon** Gibt die Grafikdatei (*.png*, *.bmp*, *.jpg*, *.ico*) an, die das Symbol enthält, das im **Erweiterungs-Manager**angezeigt werden soll, wenn ein Symbol vorhanden ist. Das Symbolbild muss 32x32 Pixel groß sein, oder es wird die Größe auf diese Dimensionen geändert. Wenn kein Symbol angegeben ist, verwendet **Extension Manager** ein Standardsymbol.

  **Vorschaubild** Gibt die Grafikdatei (*.png*, *.bmp*, *.jpg*, *.ico*) an, die das Vorschaubild enthält, das im **Erweiterungs-Manager**angezeigt werden soll, wenn ein Vorschaubild vorhanden ist. Das Vorschaubild muss 200x200 Pixel groß sein. Wenn kein Vorschaubild angegeben ist, verwendet **Extension Manager** ein Standardbild.

  **Tags** Fügt Text-Tags hinzu, die für Suchhinweise verwendet werden sollen.

  **Versionshinweise** Gibt eine Datei an (*.txt*, *.rtf*), die Versionshinweise enthält. Es kann sich dabei auch um die URL einer Website handeln, auf der die Anmerkungen zu diesem Release enthalten sind.

  **Leitfaden für erste Schritte** Gibt eine Datei an (*.txt*, *.rtf*), die Informationen zur Verwendung der Erweiterung oder des Inhalts im VSIX-Paket enthält. Dieses Handbuch wird angezeigt, wenn die Erweiterungsinstallation abgeschlossen ist. Nimmt auch die URL einer Website, die das Handbuch anzeigt.

  **Weitere Info-URL** Gibt die URL einer Website an, die zusätzliche Informationen zum Produkt enthält.

  Die Registerkarte **Ziele installieren** enthält die folgenden Steuerelemente.

  **Installationstyp** Listet **Visual Studio Extension** und Extension **SDK** als Zielinstallationstypen auf. Die Optionen unterscheiden sich je nach gewähltem Typ.

  **Visual Studio-Erweiterung** Listet die **InstallationTarget-Elemente** auf, die beschreiben, wie das Paket installiert werden kann und in welchen Visual Studio-Produkten diese Erweiterung installiert werden kann. Jedes Produkt wird separat durch DenNamen und eine Version oder einen Versionsbereich identifiziert. Produkte können der Liste hinzugefügt, geändert und gelöscht werden. Der Name und die Version eines Produkts entsprechen den **Attributen ID** und **Version** des zugeordneten **InstallationTarget-Elements.**

  **Der Versionsbereich** ist [12.0, 14.0] und verwendet die folgende Notation:

- [ - Mindestversion inklusive

- ] - maximale Version inklusive

- ( - Mindestversion exklusiv

- ) - maximale Version exklusiv

- Einzelversion - nur die angegebene Version

  **Erweiterungs-SDK** Gibt eine globale Installation an, die nicht auf ein bestimmtes Produkt und eine bestimmte Version beschränkt ist. **Target Platform Identifier** ist die Plattform, z. B. "Windows", auf die Sie abzielen. **Die Zielplattformversion** ist die Version Ihrer Zielplattform, z. B. 8.0. **SDK-Name** und **SDK-Version** sind der Name bzw. die Versionsnummer des SDK.

  **Diese VSIX ist für alle Benutzer installiert (erfordert Eine Erhöhung bei der Installation)** Wenn Sie dieses Kontrollkästchen aktivieren, wird die Erweiterung für alle Benutzer installiert. Andernfalls wird es nur für den aktuellen Benutzer installiert.

  **Diese VSIX wird von Windows Installer installiert** Wenn Sie dieses Kontrollkästchen aktivieren, wird die Erweiterung vom Windows Installer (*.msi-Datei)* installiert. Andernfalls wird es als typisches VSIX-Paket (*.vsix-Datei)* installiert.

  Die Registerkarte **"Assets"** enthält die folgenden Steuerelemente.

  **Liste der Vermögenswerte** Listet die Asset-Elemente auf, die die Erweiterungs- oder Inhaltselemente beschreiben, die dieses Paket aufzeigt. Jedes Erweiterungs- oder Inhaltselement wird separat nach Quelle, Typ und Pfad aufgelistet. Erweiterungen und Inhaltselemente können der Liste hinzugefügt, geändert und gelöscht werden. Der Typ und Pfad eines Erweiterungs- `Type` `Path` oder Inhaltselements `Asset` entspricht den Attributen und Attributen des zugeordneten Elements. Die folgenden Typen werden unterstützt:

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Um ein Asset hinzuzufügen oder zu bearbeiten, müssen Sie den Anlagentyp angeben, ob es sich bei dem Asset um ein Projekt in der aktuellen Projektmappe oder eine Datei im Dateisystem handelt, sowie den Namen des Projekts. Sie können auch den Namen des Ordners angeben, in den eingebettet werden soll.

  Sie können auch eigene Typen erstellen und ihnen eindeutige Namen geben.

  Die Registerkarte **Abhängigkeiten** enthält die folgenden Steuerelemente.

  **Name, Quelle und Versionsbereich** Listet die Dependency-Elemente dieses Pakets auf, bei denen es sich um andere Pakete handelt, von denen dieses Paket abhängt. Wenn ein Abhängigkeitspaket angegeben ist, muss es installiert werden, bevor dieses Paket installiert wird. Andernfalls muss dieses Paket es installieren.

  Abhängigkeitspakete werden durch Bezeichner, Name, Versionsbereich, Quelle und wie die Abhängigkeit aufgelöst werden soll, angegeben. Jedes Abhängigkeitspaket wird separat nach Name, Version und Quelle aufgeführt. Abhängigkeitspakete können der Liste hinzugefügt, geändert und gelöscht werden.

  Der Bezeichner `ID` muss mit dem Attribut der Metadaten des Abhängigkeitspakets übereinstimmen. Die Quelle kann ein Projekt in der aktuellen Projektmappe, eine aktuell installierte Erweiterung oder eine Datei sein. Die Einstellung **Wie wird die Abhängigkeit aufgelöst,** kann der relative Pfad eines geschachtelten Pakets oder die URL des Downloadspeicherorts für die Abhängigkeit sein. Die ID, die Version und die Auflösung des `Id` `Version`Abhängigkeitspakets entsprechen den , und `Location` attributen des zugeordneten `Dependency` Elements.

## <a name="see-also"></a>Weitere Informationen
- [VSIX-Erweiterungsschema 2.0-Referenz](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
