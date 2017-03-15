---
title: Die Struktur der XML-Datei [Content_types] | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- content_types
- content types
- opc
- vsix
ms.assetid: 9c399598-b9fa-4da7-84b5-defbf82e9335
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 7278fb37984b92a6a07823c552db5c59a446d0d2
ms.openlocfilehash: 6f45707a88a27fa54840825d9562f859385ce4b7
ms.lasthandoff: 02/22/2017

---
# <a name="the-structure-of-the-contenttypesxml-file"></a>Die Struktur der [Content_types] .xml-Datei
Enthält Informationen zu den Arten von Inhalten in einem VSIX-Paket. Visual Studio verwendet die [Content_Types] .xml-Datei, um das Paket zu installieren, aber die Datei selbst wird nicht installiert.  
  
> [!NOTE]
>  Obwohl dieses Thema nur für [Content_Type] .XML-Dateien, die in VSIX-Paketen verwendet werden gilt, ist der [Content_Types] .xml-Dateityp Teil der *Open Packaging-Konventionen (OPC)* standard. Weitere Informationen finden Sie unter [OPC: A New Standard für Verpackung Your Data](http://go.microsoft.com/fwlink/?LinkID=148207) auf der MSDN-Website.  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden das Stammelement und seine Attribute und untergeordneten Elemente beschrieben.  
  
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
|http://Schemas.OpenFormats.org/Package/2006/Content-Types|Der Speicherort des Schemas, Inhaltstypen.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Die `Types` Element kann eine beliebige Anzahl von enthalten `Default` Elemente.  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`Default`|Beschreibt einen Inhaltstyp im VSIX-Paket. Jeder Dateityp im Paket muss einen eigenen haben `Default` Element.|  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Extension`|Die Erweiterung einer Datei im VSIX-Paket.|  
|`ContentType`|Beschreibt die Art des Inhalts, der die Erweiterung zugeordnet ist.|  
  
### <a name="attribute-name-attribute"></a>{Attributname} Attribut  
 Visual Studio erkennt die folgenden `ContentType` Werte für den zugeordneten `Extension` Typen.  
  
|Erweiterung|ContentType|  
|---------------|-----------------|  
|TXT|Text/plain|  
|PKGDEF|Text/plain|  
|xml|text/xml|  
|vsixmanifest|text/xml|  
|htm- oder HTML-|Text/html|  
|RTF|Anwendung/rtf|  
|PDF-Datei|Application/pdf|  
|GIF|Image/gif|  
|JPEG- Dateien|Image/jpg|  
|TIFF|Image/tiff|  
|VSIX|Anwendung/zip|  
|ZIP|Anwendung/zip|  
|dll|Application/Octet-stream|  
|Alle anderen Dateitypen|Application/Octet-stream|  
  
## <a name="example"></a>Beispiel  
  
### <a name="description"></a>Beschreibung  
 Die folgende [Content_Types] .xml-Datei beschreibt ein normales VSIX-Paket.  
  
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
 [VSIX-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [OPC: Ein neuer Standard für das Verpacken Ihrer Datendiensts](http://go.microsoft.com/fwlink/?LinkID=148207)
