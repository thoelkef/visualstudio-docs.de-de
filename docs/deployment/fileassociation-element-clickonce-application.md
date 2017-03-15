---
title: "&lt;fileAssociation&gt; Element (ClickOnce Application) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<fileAssociation> element [ClickOnce application manifest]"
  - "manifests [ClickOnce], fileAssociation element"
ms.assetid: 8f951b4f-54f9-412e-a9e5-af4e379fcf08
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;fileAssociation&gt; Element (ClickOnce Application)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt eine Dateierweiterung an, die der Anwendung zugeordnet sein soll.  
  
## Syntax  
  
```  
<fileAssociation  
    xmlns="urn:schemas-microsoft-com:clickonce.v1"  
    extension  
    description  
    progid  
    defaultIcon  
/>  
```  
  
## Elemente und Attribute  
 Das `fileAssociation`\-Element ist optional.  Das Element verfügt über die folgenden Attribute.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`extension`|Erforderlich.  Die Dateierweiterung, die der Anwendung zugeordnet werden soll.|  
|`description`|Erforderlich.  Eine Beschreibung des Dateityps, der von der Shell verwendet werden soll.|  
|`progid`|Erforderlich.  Ein Name, der den Dateityp eindeutig identifiziert.|  
|`defaultIcon`|Erforderlich.  Gibt das Symbol an, das für Dateien mit dieser Erweiterung verwendet werden soll.  Die Symboldatei muss durch das [\<file\> Element](../deployment/file-element-clickonce-application.md) in dem [\<assembly\> Element](../deployment/assembly-element-clickonce-application.md) angegeben werden, das dieses Element enthält.|  
  
## Hinweise  
 Dieses Element muss einen XML\-Namespaceverweis auf "urn:schemas\-microsoft\-com:clickonce.v1" einschließen.  Wenn das `<fileAssociation>`\-Element verwendet wird, muss es nach dem `<application>`\-Element in seinem übergeordneten [\<assembly\> Element](../deployment/assembly-element-clickonce-application.md) eingeordnet werden.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] überschreibt keine vorhandenen Dateizuordnungen.  Allerdings kann eine ClickOnce\-Anwendung die Dateierweiterung nur für den aktuellen Benutzer überschreiben.  Nach der Deinstallation der ClickOnce\-Anwendung löscht ClickOnce die Dateizuordnung für den Benutzer, und die Zuordnung pro Computer ist wieder aktiv.  
  
## Beispiel  
 Im folgenden Codebeispiel werden `fileAssociation`\-Elemente in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bereitgestellte Texteditoranwendung veranschaulicht.  In diesem Codebeispiel ist auch das vom `defaultIcon`\-Attribut angeforderte [\<file\> Element](../deployment/file-element-clickonce-application.md) enthalten.  
  
```  
<file name="text.ico" size="4286">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>0joAqhmfeBb93ZneZv/oTMP2brY=</dsig:DigestValue>  
  </hash>  
</file>  
<file name="writing.ico" size="9662">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>2cL2U7cm13nG40v9MQdxYKazIwI=</dsig:DigestValue>  
  </hash>  
</file>  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".text" description="Text  Document (ClickOnce)" progid="Text.Document" defaultIcon="text.ico" />  
<fileAssociation xmlns="urn:schemas-microsoft-com:clickonce.v1" extension=".writing" description="Writings (ClickOnce)" progid="Writing.Document" defaultIcon="writing.ico" />  
```  
  
## Siehe auch  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)