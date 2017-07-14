---
title: ItemGroup-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemGroup element [MSBuild]
- <ItemGroup> element [MSBuild]
ms.assetid: aac894e3-a9f1-4bbc-a796-6ef07001f35b
caps.latest.revision: 24
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 38c6099f912424d21df2aeea4cfdd0401ba57465
ms.openlocfilehash: e63c0dd4e201ef83f84f01148aacd4458806103d
ms.contentlocale: de-de
ms.lasthandoff: 07/14/2017

---
# ItemGroup-Element (MSBuild)
<a id="itemgroup-element-msbuild" class="xliff"></a>
Enthält eine Reihe von benutzerdefinierten [Item](../msbuild/item-element-msbuild.md)-Elementen. Jedes Element, das in einem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekt verwendet wird, muss als untergeordnetes Element eines `ItemGroup`-Elements angegeben werden.  
  
 \<Project>  
 \<ItemGroup>  
  
## Syntax
<a id="syntax" class="xliff"></a>  
  
```xml  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## Attribute und Elemente
<a id="attributes-and-elements" class="xliff"></a>  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute
<a id="attributes" class="xliff"></a>  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut. Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions (Bedingungen)](../msbuild/msbuild-conditions.md).|  
  
### Untergeordnete Elemente
<a id="child-elements" class="xliff"></a>  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Definiert die Eingaben für den Buildprozess. Es kann keine oder mehrere `Item`-Elemente in einer `ItemGroup` geben.|  
  
### Übergeordnete Elemente
<a id="parent-elements" class="xliff"></a>  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdatei.|  
|[Target](../msbuild/target-element-msbuild.md)|Ab.NET Framework 3.5 kann das `ItemGroup`-Element innerhalb eines `Target`-Elements angezeigt werden. Weitere Informationen finden Sie unter [Targets (Ziele)](../msbuild/msbuild-targets.md).|  
  
## Hinweise
<a id="remarks" class="xliff"></a>  
  
## Beispiel
<a id="example" class="xliff"></a>  
 Im folgenden Codebeispiel werden die benutzerdefinierten Elementsammlungen `Res` und `CodeFiles` gezeigt, die innerhalb eines `ItemGroup`-Element deklariert sind. Jedes der Elemente in der `Res`-Elementsammlung enthält ein benutzerdefiniertes untergeordnetes [ItemMetadata](../msbuild/itemmetadata-element-msbuild.md)-Element.  
  
```xml  
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
<a id="see-also" class="xliff"></a>  
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elemente](../msbuild/msbuild-items.md)   
 [Gemeinsame MSBuild-Projektelemente](../msbuild/common-msbuild-project-items.md)
