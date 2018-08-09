---
title: Lokalisieren von VSIX-Paketen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54de0b219eb1c86a413b7a95e87a48e7f65ac9ec
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636973"
---
# <a name="localizing-vsix-packages"></a>Lokalisieren von VSIX-Paketen

Sie können ein VSIX-Paket auch lokalisieren, durch das Erstellen einer *Extension.vsixlangpack* -Datei für jede Sprache Ziel und die anschließende im richtigen Ordner. Wenn ein lokalisiertes Paket installiert ist, wird der lokalisierte Name der Erweiterung zusammen mit einer lokalisierten Beschreibung angezeigt. Wenn Sie angeben, eine lokalisierte Lizenzdatei oder eine URL, die auf lokalisierte Informationen verweist, werden sie ebenfalls angezeigt.

Wenn der Inhalt des VSIX-Pakets eine VSPackage enthält, die fügt Menübefehle oder eine andere Benutzeroberfläche, finden Sie unter [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md) Informationen zum Lokalisieren die neue UI-Elemente.

## <a name="directory-structure"></a>Verzeichnisstruktur

 Wenn ein Benutzer eine Erweiterung installiert **Erweiterungen und Updates** überprüft die oberste Ebene der VSIX-Paket für einen Ordner, deren Name mit der Visual Studio-Gebietsschema des Zielcomputers übereinstimmt. Wenn **Erweiterungen und Updates** sucht nach einem *.vsixlangpack* Datei im Ordner "", ersetzt er die lokalisierte Werte in dieser Datei für die entsprechenden Werte in der *vsixmanifest*Datei. Diese Werte werden angezeigt, wenn die Erweiterung installiert wird. Das folgende Beispiel zeigt die Verzeichnisstruktur für ein VSIX-Paket, das in Spanisch (es-ES) und Französisch (fr-FR) lokalisiert ist.  

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
> Die VSIX-unterstützt-Projektvorlagen in der [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generieren Sie ein VSIX-Manifest, und nennen Sie sie *"Source.Extension.vsixmanifest"*. Wenn Visual Studio das Projekt erstellt wurde, kopiert er den Inhalt der Datei in "Extension.vsixmanifest" im VSIX-Paket.

## <a name="the-extensionvsixlangpack-file"></a>Die Extension.vsixlangpack-Datei

Die *Extension.vsixlangpack* Datei folgt die [Schema der VSIX-Sprachpaket 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Dieses Schema verfügt über eine `PackageLanguagePackManifest`, die unmittelbar folgt eine `Metadata` untergeordnetes Element. Das Metadatenelement kann bis zu 6 untergeordnete Elemente enthalten, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, und `Icon`. Diese untergeordneten Elemente entsprechen den `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, und `Icon` untergeordnete Elemente des der `Metadata` Element der *"Extension.vsixmanifest"* Datei.

Wenn Sie eine Vsixlangpack-Datei erstellen, müssen Sie festlegen der `Include in Vsix` Eigenschaft `true`. Andernfalls wird der Text für die lokalisierte Installations-ignoriert.

### <a name="to-set-the-include-in-vsix-property"></a>Die Include in VSIX-Eigenschaft festlegen

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf die Extension.vsixlangpack-Datei, und klicken Sie dann auf **Eigenschaften**.

2.  In der **Eigenschaftenraster**, klicken Sie auf **Include in VSIX-Datei**, und legen Sie dessen Wert auf `true`.

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung

Das folgende Beispiel zeigt die relevanten Teile einer *"Extension.vsixmanifest"* Datei. Die Datei enthält auch die entsprechenden *Extension.vsixlangpack* -Datei für Spanisch. Die Werte aus dem Sprachpaket ersetzen die Werte aus dem Manifest auf, wenn das Visual Studio-Gebietsschema des Zielcomputers auf Spanisch festgelegt ist.

### <a name="code"></a>Code

 [*"Extension.vsixmanifest"*]

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

 [*Extension.vsixlangpack*]

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

## <a name="see-also"></a>Siehe auch

|Titel|Beschreibung|
|-----------|-----------------|
|[Schemareferenz für VSIX-Sprachpaket 2.0](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Ein VSIX-Sprachpaket wird beschrieben, die Informationen zur Lokalisierung von einem VSIX-Bereitstellungsdatei.|
|[Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Struktur und Inhalt einer Vsix-Pakets.|
|[Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md)|Zeigt, wie andere Textressourcen in einer Erweiterung zu lokalisieren.|