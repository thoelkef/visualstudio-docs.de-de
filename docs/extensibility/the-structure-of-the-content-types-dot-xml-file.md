---
title: Die Struktur der [Content_types] .xml-Datei | Microsoft-Dokumentation
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
ms.openlocfilehash: 49ba65f92143f47432cac874ebfd539f9b2da0f5
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495580"
---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Die Struktur der [Content_types].xml-Datei
Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die [Content_Types] .xml-Datei zum Installieren des Pakets, aber die Datei selbst werden nicht installiert.  
  
> [!NOTE]
>  Obwohl in diesem Thema nur für XML-Dateien [Content_Type], die in VSIX-Paketen verwendet werden gilt, wird der [Content_Types] .xml-Dateityp ist Teil der *Open Packaging Conventions (OPC)* standard. Weitere Informationen finden Sie unter [OPC: A New Standard für die Paketerstellung Your Data](http://go.microsoft.com/fwlink/?LinkID=148207) auf der MSDN-Website.  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten wird beschrieben, das Stammelement und seine Attribute und untergeordneten Elementen.  
  
### <a name="root-element"></a>Stammelement  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Types`|Enthält untergeordnete Elemente, die die Dateitypen im VSIX-Paket auflisten.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Xmlns`|(Erforderlich.) Der Speicherort des Schemas, die für diese [Content_Types] .xml-Datei verwendet.|  
  
### <a name="attribute-name-attribute"></a>{Attributname} Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|http://schemas.openformats.org/package/2006/content-types|Der Speicherort des Schemas, Inhaltstypen.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Die `Types` Element darf eine beliebige Anzahl von `Default` Elemente.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp in das Paket muss einen eigenen verfügen `Default` Element.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Extension`|Die Dateinamenerweiterung einer Datei in VSIX-Paket.|  
|`ContentType`|Beschreibt die Art von Inhalten, die mit der Dateinamenerweiterung verknüpft ist.|  
  
### <a name="attribute-name-attribute"></a>{Attributname} Attribut  
 Visual Studio erkennt die folgenden `ContentType` Werte für das zugeordnete `Extension` Typen.  
  
|Erweiterung|ContentType|  
|---------------|-----------------|  
|TXT|Text/plain|  
|PKGDEF|Text/plain|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm- oder HTML-|Text/html|  
|RTF|Anwendung/rtf|  
|PDF-Datei|Application/PDF-Datei|  
|GIF|Image/gif|  
|JPG oder JPEG-Format|Image/jpg|  
|TIFF|Image/tiff|  
|VSIX|Application/zip|  
|ZIP|Application/zip|  
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
 [Anatomie eines VSIX-Pakets](../extensibility/anatomy-of-a-vsix-package.md)   
 [Referenz zum VSIX-Erweiterung Schema 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Ein neuer Standard für das Verpacken Ihrer Daten](http://go.microsoft.com/fwlink/?LinkID=148207)