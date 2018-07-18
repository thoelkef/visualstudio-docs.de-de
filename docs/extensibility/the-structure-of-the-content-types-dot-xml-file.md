---
title: Die Struktur der XML-Datei [Content_types] | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 38e65f484411abcfb2acd78b124b77ff3f2c49cd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31144566"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Die Struktur der [Content_types] .XML-Datei
Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio [Content_Types] .xml-Datei zum Installieren des Pakets verwendet, aber die Datei selbst wird nicht installiert.  
  
> [!NOTE]
>  Bezieht sich in diesem Thema nur auf [Content_Type] XML-Dateien, die in VSIX-Pakete verwendet werden, wird der [Content_Types] .xml-Dateityp ist Teil der *(Open Packaging Conventions, OPC)* standard. Weitere Informationen finden Sie unter [OPC: A New Standard für Verpackung Your Data](http://go.microsoft.com/fwlink/?LinkID=148207) auf der MSDN-Website.  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten wird beschrieben, die Root-Element und seine Attribute und untergeordneten Elemente.  
  
### <a name="root-element"></a>Stammelement  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket auflisten.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Xmlns`|(Erforderlich.) Der Speicherort des Schemas, die für diese [Content_Types] .xml-Datei verwendet.|  
  
### <a name="attribute-name-attribute"></a>{Attributnamen} Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|Der Speicherort des Schemas Inhaltstypen.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Die `Types` Element darf eine beliebige Anzahl von `Default` Elemente.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket benötigt einen eigenen `Default` Element.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Extension`|Die Dateinamenerweiterung einer Datei im VSIX-Paket.|  
|`ContentType`|Beschreibt die Art des Inhalts, der mit der Dateinamenerweiterung verknüpft ist.|  
  
### <a name="attribute-name-attribute"></a>{Attributnamen} Attribut  
 Visual Studio erkennt die folgenden `ContentType` Werte für den zugeordneten `Extension` Typen.  
  
|Erweiterung|ContentType|  
|---------------|-----------------|  
|TXT|Text/plain|  
|PKGDEF|Text/plain|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm- oder HTML-|Text/html|  
|RTF-Datei|Anwendung/rtf|  
|PDF-Datei|Application/pdf|  
|GIF|Image/gif|  
|JPEG- Dateien|Image/jpg|  
|TIFF|Image/tiff|  
|VSIX|Anwendung/zip|  
|PLZ|Anwendung/zip|  
|dll|application/octet-stream|  
|Alle anderen Dateitypen|application/octet-stream|  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Die folgende [Content_Types] .xml-Datei beschreibt ein typisches VSIX-Paket.  
  
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
 [Aufbau eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Einen neuen Standard für das Verpacken Ihrer Daten](http://go.microsoft.com/fwlink/?LinkID=148207)