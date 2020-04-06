---
title: Die Struktur der Datei [Content_types].xml | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2761e012d32516265e61c8001491e3c605372ff5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699022"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Die Struktur der [Content_types].xml-Datei
Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die Datei [Content_Types].xml, um das Paket zu installieren, aber es installiert die Datei nicht selbst.

> [!NOTE]
> Obwohl dieses Thema nur für [Content_Type].xml-Dateien gilt, die in VSIX-Paketen verwendet werden, ist der Dateityp [Content_Types].xml Teil des *OPC-Standards (Open Packaging Conventions).* Weitere Informationen finden Sie unter [OPC: A New Standard For Packaging Your Data](https://msdn.microsoft.com/magazine/cc163372.aspx) auf der MSDN-Website.

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden das Stammelement und seine Attribute und untergeordneten Elemente beschrieben.

### <a name="root-element"></a>Root-Element

|Element|BESCHREIBUNG|
|-------------|-----------------|
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket aufzählen.|

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Xmlns`|(Erforderlich.) Der Speicherort des Schemas, das für diese [Content_Types].xml-Datei verwendet wird.|

### <a name="attribute-name-attribute"></a>"Attributname" Attribut

| Wert | BESCHREIBUNG |
| - | - |
| `http://schemas.openformats.org/package/2006/content-types` | Der Speicherort des Inhaltstypenschemas. |

### <a name="child-elements"></a>Untergeordnete Elemente
 Das `Types`-Element kann eine beliebige Anzahl von `Default`-Elementen enthalten.

|Element|BESCHREIBUNG|
|-------------|-----------------|
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket muss `Default` ein eigenes Element haben.|

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`Extension`|Die Dateinamenerweiterung einer Datei im VSIX-Paket.|
|`ContentType`|Beschreibt die Art des Inhalts, der der Dateinamenerweiterung zugeordnet ist.|

### <a name="attribute-name-attribute"></a>"Attributname" Attribut
 Visual Studio erkennt `ContentType` die folgenden `Extension` Werte für die zugeordneten Typen.

|Durchwahl|ContentType|
|---------------|-----------------|
|txt|text/plain|
|pkgdef|text/plain|
|Xml|text/xml|
|Extension.vsixmanifest|text/xml|
|htm oder html|text/html|
|Rtf|Anwendung/rtf|
|pdf|application/pdf|
|GIF|image/gif|
|jpg oder jpg|bild/jpg|
|tiff|image/tiff|
|VSIX|application/zip|
|zip|application/zip|
|DLL-Datei|application/octet-stream|
|alle anderen Dateitypen|application/octet-stream|

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG
 Die folgende Datei [Content_Types].xml beschreibt ein typisches VSIX-Paket.

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

## <a name="see-also"></a>Weitere Informationen
- [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)
- [VSIX-Erweiterungsschema 1.0-Referenz](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [OPC: Ein neuer Standard für die Verpackung Ihrer Daten](https://msdn.microsoft.com/magazine/cc163372.aspx)
