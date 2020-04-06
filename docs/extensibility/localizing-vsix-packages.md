---
title: Lokalisieren von VSIX-Paketen | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702898"
---
# <a name="localizing-vsix-packages"></a>Lokalisieren von VSIX-Paketen

Sie können ein VSIX-Paket lokalisieren, indem Sie eine *Extension.vsixlangpack-Datei* für jede Zielsprache erstellen und sie dann im richtigen Ordner speichern. Wenn ein lokalisiertes Paket installiert wird, wird der lokalisierte Name der Erweiterung zusammen mit einer lokalisierten Beschreibung angezeigt. Wenn Sie eine lokalisierte Lizenzdatei oder eine URL angeben, die auf lokalisierte Informationen verweist, werden diese ebenfalls angezeigt.

Wenn der Inhalt Ihres VSIX-Pakets ein VSPackage enthält, das Menübefehle oder eine andere Benutzeroberfläche hinzufügt, finden Sie unter Lokalisieren von [Menübefehlen](../extensibility/localizing-menu-commands.md) Informationen zum Lokalisieren der neuen UI-Elemente.

## <a name="directory-structure"></a>Verzeichnisstruktur

 Wenn ein Benutzer eine Erweiterung installiert, überprüft **Extensions and Updates** die oberste Ebene des VSIX-Pakets auf einen Ordner, dessen Name mit dem Visual Studio-Gebietsschema des Zielcomputers übereinstimmt. Wenn **Extensions and Updates** eine *.vsixlangpack-Datei* im Ordner findet, ersetzt sie die lokalisierten Werte in dieser Datei durch die entsprechenden Werte in der *.vsixmanifest-Datei.* Diese Werte werden angezeigt, wenn die Erweiterung installiert wird. Das folgende Beispiel zeigt die Verzeichnisstruktur für ein VSIX-Paket, das in Spanisch (es-ES) und Französisch (fr-FR) lokalisiert ist.

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Die VSIX-unterstützten Projektvorlagen [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] im Generieren eines VSIX-Manifests und dessen *Namen source.extension.vsixmanifest*. Wenn Visual Studio das Projekt erstellt, kopiert es den Inhalt dieser Datei in Extension.VsixManifest im VSIX-Paket.

## <a name="the-extensionvsixlangpack-file"></a>Die Datei Extension.vsixlangpack

Die *Datei Extension.vsixlangpack* folgt dem [VSIX Language Pack-Schema 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Dieses Schema `PackageLanguagePackManifest`hat eine , auf `Metadata` die unmittelbar ein untergeordnetes Element folgt. Das Metadata-Element kann bis zu `DisplayName` `Description`6 `MoreInfo` `License`untergeordnete `ReleaseNotes`Elemente, , , , , , und `Icon`. Diese untergeordneten Elemente `DisplayName` `Description`entsprechen `MoreInfo` `License`den `ReleaseNotes`, `Icon` , , `Metadata` , und untergeordneten Elementen des Elements der *Datei Extension.vsixmanifest.*

Wenn Sie eine vsixlangpack-Datei erstellen, müssen Sie die `Include in Vsix` Eigenschaft auf `true`festlegen. Andernfalls wird der lokalisierte Installationstext ignoriert.

### <a name="to-set-the-include-in-vsix-property"></a>So legen Sie die Include in Vsix-Eigenschaft fest

1. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf die Datei Extension.vsixlangpack, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie im **Eigenschaftenraster**auf **In Vsix einschließen,** und legen Sie den Wert auf fest. `true`

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Das folgende Beispiel zeigt relevante Teile einer *Datei Extension.vsixmanifest.* Die Datei enthält auch die entsprechende *Extension.vsixlangpack-Datei* für Spanisch. Die Werte aus dem Sprachpaket ersetzen die Werte aus dem Manifest, wenn das Visual Studio-Gebietsschema des Zielcomputers auf Spanisch festgelegt ist.

### <a name="code"></a>Code

- [*Erweiterung.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- [*Erweiterung.vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Weitere Informationen

|Titel|BESCHREIBUNG|
|-----------|-----------------|
|[VSIX Language Pack Schema 2.0-Referenz](vsix-language-pack-schema-2-0-reference.md)|Ein VSIX-Sprachpaket beschreibt die Lokalisierungsinformationen einer .vsix-Bereitstellungsdatei.|
|[Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Struktur und den Inhalt eines vsix-Pakets.|
|[Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md)|Zeigt, wie andere Textressourcen in einer Erweiterung lokalisiert werden.|
