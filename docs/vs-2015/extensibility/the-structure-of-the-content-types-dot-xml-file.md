---
title: Die Struktur der datei Content_types].xml | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d6eca44c08cf35e7b2075965c1b6139e7fb95bc
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395356"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Die Struktur der Content_types].xml-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die Datei [Content_Types].xml, um das Paket zu installieren, aber es installiert die Datei nicht selbst.  
  
> [!NOTE]
> Obwohl dieses Thema nur für [Content_Type].xml-Dateien gilt, die in VSIX-Paketen verwendet werden, ist der Dateityp [Content_Types].xml Teil des *OPC-Standards (Open Packaging Conventions).* Weitere Informationen finden Sie unter [OPC: A New Standard For Packaging Your Data](https://msdn.microsoft.com/magazine/cc163372.aspx) auf der MSDN-Website.  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden das Stammelement und seine Attribute und untergeordneten Elemente beschrieben.  
  
### <a name="root-element"></a>Root-Element  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket aufzählen.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Xmlns`|(Erforderlich.) Der Speicherort des Schemas, das für diese [Content_Types].xml-Datei verwendet wird.|  
  
### <a name="attribute-name-attribute"></a>"Attributname" Attribut  
  
|                           Wert                           |                Beschreibung                |
|-----------------------------------------------------------|-------------------------------------------|
| `http://schemas.openformats.org/package/2006/content-types` | Der Speicherort des Inhaltstypenschemas. |
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Das `Types`-Element kann eine beliebige Anzahl von `Default`-Elementen enthalten.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket muss `Default` ein eigenes Element haben.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
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
  
### <a name="description"></a>Beschreibung  
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
  
## <a name="see-also"></a>Siehe auch  
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX-Erweiterungsschema 1.0-Referenz](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Ein neuer Standard für die Verpackung Ihrer Daten](https://msdn.microsoft.com/magazine/cc163372.aspx)
