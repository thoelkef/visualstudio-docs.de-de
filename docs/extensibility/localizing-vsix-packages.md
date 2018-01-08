---
title: Lokalisieren von VSIX-Pakete | Microsoft Docs
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6b95047348f549073a05060b81874f65d7781918
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="localizing-vsix-packages"></a>Lokalisieren von VSIX-Pakete

Sie können ein VSIX-Paket lokalisieren, indem eine Extension.vsixlangpack-Datei für jede Zielsprache erstellen und sie dann in den richtigen Ordner zu speichern. Wenn ein lokalisiertes Paket installiert ist, wird der lokalisierte Name der Erweiterung zusammen mit einer lokalisierten Beschreibung angezeigt. Wenn Sie angeben, eine lokalisierte Lizenzdatei oder eine URL, die auf den lokalisierten Informationen verweist, werden sie ebenfalls angezeigt.

Wenn der Inhalt des VSIX-Pakets eine VSPackage enthält, die fügt Menübefehle oder eine andere Benutzeroberfläche finden Sie unter [Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md) Informationen zum Lokalisieren von der neuen Elemente der Benutzeroberfläche.

## <a name="directory-structure"></a>Verzeichnisstruktur

 Wenn ein Benutzer eine Erweiterung installiert **Erweiterungen und Updates** überprüft die oberste Ebene des VSIX-Pakets für einen Ordner, deren Name mit der Visual Studio-Gebietsschema des Zielcomputers übereinstimmt. Wenn **Erweiterungen und Updates** eine .vsixlangpack findet Datei im Ordner "", er ersetzt die lokalisierten Werte in dieser Datei für die entsprechenden Werte in die vsixmanifest-Datei. Diese Werte werden angezeigt, wenn die Erweiterung installiert wird. Das folgende Beispiel zeigt die Verzeichnisstruktur für ein VSIX-Paket, das in Spanisch (es-ES) und Französisch (fr-FR) lokalisiert wird.  

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
> Die VSIX-unterstützt-Projektvorlagen in den [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generieren Sie ein VSIX-Manifest, und nennen sie die Datei "Source.Extension.vsixmanifest". Wenn Visual Studio das Projekt erstellt wurde, kopiert er den Inhalt dieser Datei in "Extension.vsixmanifest" im VSIX-Paket.

## <a name="the-extensionvsixlangpack-file"></a>Die Extension.vsixlangpack-Datei

Die Extension.vsixlangpack-Datei der [VSIX-Language Pack Schema 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Dieses Schema verfügt über eine `PackageLanguagePackManifest`, ist der unmittelbar gefolgt von einem `Metadata` untergeordnetes Element. Das Metadatenelement kann bis zu 6 untergeordnete Elemente enthalten `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, und `Icon`. Diese untergeordneten Elemente entsprechen den `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, und `Icon` untergeordneten Elemente des der `Metadata` -Element der Datei "Extension.vsixmanifest".

Wenn Sie eine Vsixlangpack-Datei erstellen, müssen Sie festlegen der `Include in Vsix` Eigenschaft `true`. Andernfalls wird der Text lokalisierte Installations-ignoriert.

### <a name="to-set-the-include-in-vsix-property"></a>Die Include in VSIX-Eigenschaft festlegen

1. In **Projektmappen-Explorer**mit der rechten Maustaste auf die Extension.vsixlangpack-Datei, und klicken Sie dann auf **Eigenschaften**.

2.  Klicken Sie im Eigenschaftenraster auf **Include in Vsix**, und legen Sie dessen Wert auf `true`.

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung

Das folgende Beispiel zeigt die relevanten Teile einer Datei "Extension.vsixmanifest" zusammen mit der entsprechenden Extension.vsixlangpack-Datei für Spanisch. Die Werte aus dem Language Pack ersetzen die Werte aus dem Manifest an, wenn das Visual Studio-Gebietsschema des Zielcomputers auf Spanisch festgelegt ist.

### <a name="code"></a>Code

 ["Extension.vsixmanifest"]

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

 [Extension.vsixlangpack]

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
|[VSIX LanguagePack 2.0 Schemareferenz](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Ein VSIX-Language Pack werden die Informationen zur Lokalisierung in einer VSIX-Bereitstellungsdatei beschrieben.|
|[Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)|Beschreibt die Struktur und Inhalt eines Vsix-Pakets.|
|[Lokalisieren von Menübefehlen](../extensibility/localizing-menu-commands.md)|Zeigt Informationen zum Lokalisieren von anderen Textressourcen in einer Erweiterung.|