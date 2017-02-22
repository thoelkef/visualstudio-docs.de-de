---
title: "ItemDefinitionGroup Element (MSBuild) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "ItemDefinitionGroup Element [MSBuild]"
  - "<ItemDefinitionGroup> Element [MSBuild]"
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# ItemDefinitionGroup Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem  `ItemDefinitionGroup`\-Element können Sie einen Satz von Elementdefinitionen festlegen, bei dem es sich um Metadatenwerte handelt, die standardmäßig auf alle Elemente im Projekt angewendet werden.  ItemDefinitionGroup macht die Verwendung von [CreateItem Task](../msbuild/createitem-task.md) und [CreateProperty Task](../msbuild/createproperty-task.md) überflüssig.  Weitere Informationen finden Sie unter [Item Definitions](../msbuild/item-definitions.md).  
  
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
|[Element](../msbuild/item-element-msbuild.md)|Definiert die Eingaben für den Buildprozess.  Es kann keine oder mehrere `Item`\-Elemente in einer `ItemDefinitionGroup` geben.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Project](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Projektdatei.|  
  
## Beispiel  
 Im folgenden Codebeispiel werden zwei Metadaten\-Elemente, m und n, in einer ItemDefinitionGroup definiert.  In diesem Beispiel wird das Standardmetadatum "m" auf das Element "i" angewendet, da das Metadatum "m" nicht explizit durch das Element "i" definiert wird.  Das Standardmetadatum "n" wird jedoch nicht auf das Element "i" angewendet, da das Metadatum "n" bereits durch Element "i" definiert ist.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemDefinitionGroup>  
        <i>  
            <m>m1</m>  
            <n>n1</n>  
        </i>        
    </ItemDefinitionGroup>  
    <ItemGroup>  
        <i Include="a">  
            <o>o1</o>  
            <n>n2</n>  
        </i>  
    </ItemGroup>  
    ...  
</Project>  
```  
  
## Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md)