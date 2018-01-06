---
title: VSIX-Language Pack 2.0 Schemareferenz | Microsoft Docs
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
caps.latest.revision: "8"
ms.author: dagriffe
author: dgriffen
manager: ghogen
ms.workload: dagriffe
ms.openlocfilehash: b601653e4b2d309d41f32ff71666567ab860e698
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-language-pack-schema-20-reference"></a>VSIX-Language Pack 2.0 Schemareferenz

Das Sprachpaket für die VSIX-Schema enthält lokalisierte Installationsinformationen für VSIX-Pakete. Version 2.0 von diesem Schema unterstützt zusätzliche lokalisierungselemente.

## <a name="language-pack-schema"></a>Language Pack-Schemas

Das Stammelement der Language Pack-Datei ist `<PackageLanguagePackManifest>`, mit der ein Attribut des `Version`, also die Language Pack-Formatversion. In diesem Thema wird beschrieben, Version 2.0 von der Language-Pack-Format, das im Manifest, durch Festlegen angegeben wird der `Version` -Attributs auf den Wert `Version="2.0.0"`. Das Stammelement enthält genau ein untergeordneter `<Metadata>` Element.

### <a name="packagelangaugepackmanifest-element"></a>PackageLangaugePackManifest-Element

Innerhalb der `<PackageLanguagePackManifest>` Element mit dem folgende Element muss vorhanden sein:
|Titel|Beschreibung|
|-----------|-----------------|
|`<Metadata>`| Das enthaltende Element für alle lokalisierten Paketmetadaten

### <a name="metadata-element"></a>Metadaten-Element

Innerhalb der `<Metadata>` Element können Sie die folgenden Elemente:
|Titel|Beschreibung|
|-----------|-----------------|
|`<DisplayName>`|Der lokalisierte Name der Erweiterung zu installierenden|
|`<Description>`|Die lokalisierte Beschreibung der Erweiterung zu installierenden|
|`<License>`| Ein Pfad zu einer lokalisierten Version der Erweiterung Lizenz|
|`<MoreInfo>`| Ein Link zu lokalisierten Informationen über die Erweiterung|
|`<ReleaseNotes>`| Einen Pfad oder einen Link, um eine lokalisierte Version der Versionshinweise|
|`<Icon>`| Ein Pfad zu einer lokalisierten Version von das Symbol "Erweiterungen"|

### <a name="sample-manifest"></a>Beispiel-Manifest

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
|[Lokalisieren von VSIX-Paketen](../extensibility/localizing-vsix-packages.md)|Zeigt, wie lokalisierte Installations-Unterstützung für ein VSIX-Paket bereitzustellen.|
|[Referenz zum VSIX-Erweiterungsschema 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)|Ein VSIX-Manifest beschreibt den Inhalt einer VSIX-Bereitstellungsdatei, dadurch kann eine Visual Studio-Erweiterung zu installierenden mithilfe der **Erweiterungen und Updates** (Dialogfeld).|
|[Suchen und Verwenden von Visual Studio-Erweiterungen](../ide/finding-and-using-visual-studio-extensions.md)|Zeigt, wie die **Erweiterungen und Updates** (Dialogfeld), installieren, entfernen, aktivieren und Deaktivieren von Erweiterungen.|