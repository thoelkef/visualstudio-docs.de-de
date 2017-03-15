---
title: "VSIXLanguagePack-Element (Schema f&#252;r VSIX-Language Pack) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# VSIXLanguagePack-Element (Schema f&#252;r VSIX-Language Pack)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erforderlich. Stellt das Stammelement für ein VSIX\-Language Pack bereit. Das VSIX\-Sprachpaket enthält lokalisierte Installationsinformationen für ein VSIX\-Paket.  
  
## Syntax  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`xmlns`|Der XML\-Namespace, in dem das VSIX\-Language Pack\-Schema definiert ist.|  
  
## Xmlns\-Attribut  
  
|Wert|Beschreibung|  
|----------|------------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Erforderlich. Der Speicherort der Datei, die das Schema für Language Packs definiert.|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[LocalizedName\-Element](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Erforderlich. Der lokalisierte Name der Erweiterung installiert werden.|  
|[LocalizedDescription\-Element](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Erforderlich. Die lokalisierte Beschreibung der Erweiterung installiert werden.|  
|[MoreInfoURL\-Element](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Optional. Ein Link zu lokalisierten Informationen über die Erweiterung.|  
|[Lizenzelement](../extensibility/license-element-vsix-language-pack-schema.md)|Optional. Der Pfad einer lokalisierten Version der Lizenzdatei für die Erweiterung.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Keine||  
  
## Elementinformationen  
  
|||  
|-|-|  
|Namespace|http:\/\/Schemas.Microsoft.com\/Developer\/VSX\-Schema\-LP\/2010|  
|Schemaname|Schema für VSIX\-Language Pack|  
|Validierungsdatei|VSIXLanguagePackSchema.xsd|  
|Leer kann sein|Nein|  
  
## Siehe auch  
 [Schemareferenz für VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalisieren von VSIX\-Paketen](../extensibility/localizing-vsix-packages.md)   
 [VSIX\-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)