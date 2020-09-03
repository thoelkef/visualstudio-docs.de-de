---
title: Die Struktur der Content_Types]. XML-Datei | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395356"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Die Struktur der Content_types].xml-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die Datei [Content_Types]. XML, um das Paket zu installieren, aber die Datei selbst wird nicht installiert.  
  
> [!NOTE]
> Obwohl sich dieses Thema nur auf [content_type]. XML-Dateien bezieht, die in VSIX-Paketen verwendet werden, ist der Dateityp [Content_Types]. XML Teil des OPC-Standards *(Open Packaging Conventions)* . Weitere Informationen finden Sie unter [OPC: ein neuer Standard zum Verpacken Ihrer Daten](https://msdn.microsoft.com/magazine/cc163372.aspx) auf der MSDN-Website.  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden das root-Element und seine Attribute und untergeordneten Elemente beschrieben.  
  
### <a name="root-element"></a>Root-Element  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket auflisten.|  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Xmlns`|(Erforderlich) Der Speicherort des Schemas, das für diese [Content_Types]. XML-Datei verwendet wird.|  
  
### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen  
  
|                           Wert                           |                Beschreibung                |
|-----------------------------------------------------------|-------------------------------------------|
| `http://schemas.openformats.org/package/2006/content-types` | Der Speicherort des Inhaltstypen Schemas. |
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Das `Types`-Element kann eine beliebige Anzahl von `Default`-Elementen enthalten.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket muss über ein eigenes- `Default` Element verfügen.|  
  
### <a name="attributes"></a>Attribute  
  
|attribute|Beschreibung|  
|---------------|-----------------|  
|`Extension`|Die Dateinamenerweiterung einer Datei im VSIX-Paket.|  
|`ContentType`|Beschreibt die Art des Inhalts, der der Dateinamenerweiterung zugeordnet ist.|  
  
### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen  
 In Visual Studio werden die folgenden `ContentType` Werte für die zugeordneten `Extension` Typen erkannt.  
  
|Erweiterung|ContentType|  
|---------------|-----------------|  
|txt|text/plain|  
|pkgdef|text/plain|  
|Xml|text/xml|  
|vsixmanifest|text/xml|  
|htm oder HTML|text/html|  
|RTF|Anwendung/RTF|  
|pdf|application/pdf|  
|GIF|image/gif|  
|JPG oder JPEG|Bild/jpg|  
|tiff|image/tiff|  
|VSIX|application/zip|  
|zip|application/zip|  
|DLL-Datei|application/octet-stream|  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX-Erweiterungs Schema 1,0-Referenz](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: ein neuer Standard zum Verpacken von Daten](https://msdn.microsoft.com/magazine/cc163372.aspx)
