---
title: "ItemGroup-Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemGroup-Element [MSBuild]"
  - "<ItemGroup>-Element [MSBuild]"
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ItemGroup-Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Enthält benutzerdefinierte [Item](../msbuild/item-element-msbuild.md)\-Elemente.  Jedes in einem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projekt verwendete Element muss als untergeordnetes Element eines `ItemGroup`\-Elements angegeben werden.  
  
## Syntax  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Condition`|Optionales Attribut.  Die auszuwertende Bedingung.  Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md).|  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Element](../msbuild/item-element-msbuild.md)|Definiert die Eingaben für den Buildprozess.  Es kann keine oder mehrere `Item`\-Elemente in einer `ItemGroup` geben.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei.|  
|[Target](../msbuild/target-element-msbuild.md)|Ab .NET Framework 3.5 kann das `ItemGroup`\-Element in einem `Target`\-Element angezeigt werden.  Weitere Informationen finden Sie unter [Targets](../msbuild/msbuild-targets.md).|  
  
## Hinweise  
  
## Beispiel  
 Das folgende Codebeispiel veranschaulicht die in einem `ItemGroup`\-Element deklarierten benutzerdefinierten Elementauflistungen `Res` und `CodeFiles`.  Jedes der Elemente in der `Res`\-Elementauflistung enthält ein benutzerdefiniertes untergeordnetes [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)\-Element.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Res Include = "Strings.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
        <Res Include = "Dialogs.fr.resources" >  
            <Culture>fr</Culture>  
        </Res>  
  
        <CodeFiles Include="**\*.cs" Exclude="**\generated\*.cs" />  
        <CodeFiles Include="..\..\Resources\Constants.cs" />  
    </ItemGroup>  
...  
</Project>  
```  
  
## Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)   
 [Common MSBuild Project Items](../msbuild/common-msbuild-project-items.md)