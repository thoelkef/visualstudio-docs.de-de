---
title: "Lizenzelement (Schema f&#252;r VSIX-Language Pack) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Lizenzelement (Schema f&#252;r VSIX-Language Pack)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Optional. Der Pfad einer lokalisierten Version der Lizenzdatei für die Erweiterung.  
  
## Syntax  
  
```  
<License>FilePath\license.txt</License>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|Keine||  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|Keine||  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[VSIX\-Sprachpaket\-Element](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Erforderlich. Stellt das Stammelement für ein VSIX\-Language Pack bereit.|  
  
## Textwert  
 Der relative Pfad der lokalisierten Lizenzdatei angezeigt werden.  
  
## Hinweise  
 Wenn die `License` Element definiert ist, wird der Text der festgelegten Lizenzdatei während des Setups angezeigt, und der Benutzer muss die Lizenz weiterhin annehmen.  
  
## Elementinformationen  
  
|||  
|-|-|  
|Namespace|http:\/\/Schemas.Microsoft.com\/Developer\/VSX\-Schema\-LP\/2010|  
|Schemaname|Schema für VSIX\-Language Pack|  
|Validierungsdatei|VSIXLanguagePackSchema.xsd|  
|Leer kann sein|Nicht zutreffend|  
  
## Siehe auch  
 [Schemareferenz für VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Lokalisieren von VSIX\-Paketen](../extensibility/localizing-vsix-packages.md)   
 [VSIX\-Erweiterung Schemareferenz 1.0](http://msdn.microsoft.com/de-de/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)