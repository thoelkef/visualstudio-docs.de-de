---
title: VSIX-Language Pack 2.0 Schemareferenz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: dagriffe
author: dgriffen
manager: douge
ms.workload:
- dagriffe
ms.openlocfilehash: 3c1dfa0e3de06bcd6c61472a085ea3c4cdeeac27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780788"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Referenz zum VSIX Language Pack 2.0-schema

Das VSIX-Sprachpaket-Schema stellt lokalisierte Installationsinformationen für VSIX-Paketen bereit. Version 2.0 von diesem Schema unterstützt zusätzliche lokalisierungselemente.

## <a name="language-pack-schema"></a>Schema Language pack

Das Stammelement der Language Pack-Datei ist `<PackageLanguagePackManifest>`, mit dem Attribut `Version`, dies ist die Version des Language Pack-Formats. In diesem Artikel wird beschrieben, Version 2.0 des Language Pack Formats, der im Manifest, durch Festlegen angegeben ist der `Version` -Attributs auf den Wert `Version="2.0.0"`. Das Stammelement enthält genau ein untergeordneter `<Metadata>` Element.

### <a name="packagelanguagepackmanifest-element"></a>PackageLanguagePackManifest-element

In der `<PackageLanguagePackManifest>` Element mit dem folgende Element muss vorhanden sein:

|Titel|Beschreibung|
|-----------|-----------------|
|`<Metadata>`| Das enthaltende Element für alle Metadaten von lokalisierten Paketen

### <a name="metadata-element"></a>Metadata-element

In der `<Metadata>` Element können Sie die folgenden Elemente aufweisen:

|Titel|Beschreibung|
|-----------|-----------------|
|`<DisplayName>`|Der lokalisierte Name der Erweiterung installiert werden|
|`<Description>`|Die lokalisierte Beschreibung der Erweiterung installiert werden|
|`<License>`| Ein Pfad zu der eine lokalisierte Version der Erweiterung-Lizenz|
|`<MoreInfo>`| Ein Link zu lokalisierten Informationen über die Erweiterung|
|`<ReleaseNotes>`| Einen Pfad oder einen Link zu einer lokalisierten Version von den Anmerkungen zur Version|
|`<Icon>`| Ein Pfad zu einer lokalisierten Version von das Symbol "Erweiterungen"|

### <a name="sample-manifest"></a>Beispielmanifest

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
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
|[Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)|Veranschaulicht, wie lokalisierte Installations-Unterstützung für ein VSIX-Paket bereitzustellen.|
|[Referenz zum VSIX-Erweiterung Schema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)|Ein VSIX-Manifest beschreibt den Inhalt einer *VSIX* Bereitstellungsdatei. Die Bereitstellungsdatei können Sie zum Installieren von Visual Studio-Erweiterung mithilfe der **Erweiterungen und Updates** Dialogfeld.|
|[Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)|Zeigt, wie die **Erweiterungen und Updates** Dialogfeld installieren, entfernen, aktivieren und Deaktivieren von Erweiterungen.|