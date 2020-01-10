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
ms.openlocfilehash: 3185b70f74478a9a55c4fb918c1535c86d154c76
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846369"
---
# <a name="the-structure-of-the-content_typesxml-file"></a>Die Struktur der Content_types].xml-Datei
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
|Attribute|Beschreibung|  
|---------------|-----------------|  
|`Xmlns`|(Erforderlich) Der Speicherort des Schemas, das für diese [Content_Types]. XML-Datei verwendet wird.|  
  
### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen  
  
|                           {2&gt;Wert&lt;2}                           |                Beschreibung                |
|-----------------------------------------------------------|-------------------------------------------|
| http://schemas.openformats.org/package/2006/content-types | Der Speicherort des Inhaltstypen Schemas. |
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Das `Types`-Element kann eine beliebige Anzahl von `Default`-Elementen enthalten.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket muss über ein eigenes `Default`-Element verfügen.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribute|Beschreibung|  
|---------------|-----------------|  
|`Extension`|Die Dateinamenerweiterung einer Datei im VSIX-Paket.|  
|`ContentType`|Beschreibt die Art des Inhalts, der der Dateinamenerweiterung zugeordnet ist.|  
  
### <a name="attribute-name-attribute"></a>{Attribut Name} Versehen  
 Visual Studio erkennt die folgenden `ContentType` Werte für die zugeordneten `Extension` Typen.  
  
|Erweiterung|ContentType|  
|---------------|-----------------|  
|txt|text/plain|  
|pkgdef|text/plain|  
|xml|Text/XML|  
|vsixmanifest|Text/XML|  
|htm oder HTML|text/html|  
|rtf|Anwendung/RTF|  
|pdf|application/pdf|  
|gif|image/gif|  
|JPG oder JPEG|Bild/jpg|  
|tiff|image/tiff|  
|VSIX|application/zip|  
|zip|application/zip|  
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
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX-Erweiterungs Schema 1,0 Verweis](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: ein neuer Standard zum Verpacken von Daten](https://msdn.microsoft.com/magazine/cc163372.aspx)
