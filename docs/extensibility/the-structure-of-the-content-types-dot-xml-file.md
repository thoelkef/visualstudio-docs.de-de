---
title: Die Struktur der [Content_Types]. XML-Datei | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac250053f90d99e7db27a9862d2dc1b33fadbfb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2019
ms.locfileid: "72983042"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Die Struktur der [Content_types].xml-Datei
Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die Datei [Content_Types]. XML, um das Paket zu installieren, aber die Datei selbst wird nicht installiert.

> [!NOTE]
> Obwohl sich dieses Thema nur auf [content_type]. XML-Dateien bezieht, die in VSIX-Paketen verwendet werden, ist der Dateityp [Content_Types]. XML Teil des OPC-Standards *(Open Packaging Conventions)* . Weitere Informationen finden Sie unter [OPC: ein neuer Standard zum Verpacken Ihrer Daten](https://msdn.microsoft.com/magazine/cc163372.aspx) auf der MSDN-Website.

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden das root-Element und seine Attribute und untergeordneten Elemente beschrieben.

### <a name="root-element"></a>Stammelement

|Element|Beschreibung|
|-------------|-----------------|
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket auflisten.|

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Xmlns`|(Erforderlich) Der Speicherort des Schemas, das für diese [Content_Types]. XML-Datei verwendet wird.|

### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen

| Wert | Beschreibung |
| - | - |
| http://schemas.openformats.org/package/2006/content-types | Der Speicherort des Inhaltstypen Schemas. |

### <a name="child-elements"></a>Untergeordnete Elemente
 Das `Types`-Element kann beliebig viele `Default` Elemente enthalten.

|Element|Beschreibung|
|-------------|-----------------|
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket muss über ein eigenes `Default`-Element verfügen.|

### <a name="attributes"></a>Attribute

|Attribut|Beschreibung|
|---------------|-----------------|
|`Extension`|Die Dateinamenerweiterung einer Datei im VSIX-Paket.|
|`ContentType`|Beschreibt die Art des Inhalts, der der Dateinamenerweiterung zugeordnet ist.|

### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen
 Visual Studio erkennt die folgenden `ContentType` Werte für die zugeordneten `Extension` Typen.

|Erweiterung|ContentType|
|---------------|-----------------|
|txt|Text/Plain|
|pkgdef|Text/Plain|
|xml|text/xml|
|vsixmanifest|text/xml|
|htm oder HTML|Text/HTML|
|RTF|Anwendung/RTF|
|PDF|Anwendung/PDF|
|GIF|Bild/GIF|
|JPG oder JPEG|Bild/jpg|
|PPE|Bild/TIFF|
|VSIX|Anwendung/zip|
|zip|Anwendung/zip|
|dll|application/octet-stream|
|alle anderen Dateitypen|application/octet-stream|

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung
 In der folgenden [Content_Types]. XML-Datei wird ein typisches VSIX-Paket beschrieben.

### <a name="code"></a>Code

```
<?xml version="1.0" encoding="utf-8" ?>
<Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
    <Default Extension="vsixmanifest" ContentType="text/xml" />
    <Default Extension="dll" ContentType="application/octet-stream" />
    <Default Extension="png" ContentType="application/octet-stream" />
    <Default Extension="txt" ContentType="text/plain" />
    <Default Extension="pkgdef" ContentType="text/plain" />
</Types>
```

## <a name="see-also"></a>Siehe auch
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
- [VSIX-Erweiterungs Schema 1,0-Referenz](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: ein neuer Standard zum Verpacken von Daten](https://msdn.microsoft.com/magazine/cc163372.aspx)