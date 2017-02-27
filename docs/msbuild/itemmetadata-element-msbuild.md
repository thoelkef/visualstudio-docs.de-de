---
title: "ItemMetadata Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemMetadata Element [MSBuild]"
  - "<ItemMetadata> Element [MSBuild]"
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# ItemMetadata Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält einen benutzerdefinierten Elementmetadatenschlüssel, der den Elementmetadatenwert enthält.  Ein Element kann beliebig viele Metadatenschlüssel\/Wert\-Paare aufweisen.  
  
## Syntax  
  
```  
<ItemMetadataName> Item Metadata value </ItemMetadataName>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung.  Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Element](../msbuild/item-element-msbuild.md)|Ein benutzerdefiniertes Element, das die Eingaben für den Buildprozess definiert.|  
  
## Textwert  
 Ein Textwert ist optional.  
  
 Dieser Text gibt den Elementmetadatenwert an, der entweder das Text\- oder das XML\-Format aufweisen kann.  
  
## Hinweise  
  
## Beispiel  
 Im folgenden Codebeispiel wird veranschaulicht, wie dem Element `CSFile` `Culture`\-Metadaten mit dem Wert `fr` hinzugefügt werden.  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)