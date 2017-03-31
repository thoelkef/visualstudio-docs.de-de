---
title: ItemMetadata-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 17
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 0e5a449ef396e7b9fd23a2c018bdc7f8791b7b38
ms.openlocfilehash: 3c92bc200ac47bdd5b1b0f6f707cd2cb9f9aada5
ms.lasthandoff: 03/13/2017

---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata-Element (MSBuild)
Enthält einen benutzerdefinierten Elementmetadatenschlüssel, der den Elementmetadatenwert enthält. Ein Element kann über eine beliebige Anzahl von Metadaten-Schlüssel-Wert-Paaren verfügen.  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Syntax  

```  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions (Bedingungen)](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|Beschreibung|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Ein benutzerdefiniertes Element, das die Eingaben für den Buildprozess definiert.|  

## <a name="text-value"></a>Textwert  
 Ein Textwert ist optional.  

 Dieser Text legt den Elementmetadatenwert fest, der im Text- oder XML-Format vorhanden sein kann.  

## <a name="remarks"></a>Hinweise  

## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht das Hinzufügen von `Culture`-Metadaten mit dem Wert `fr` zum Element `CSFile`.  

```xml  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  

## <a name="see-also"></a>Siehe auch  
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [Items](../msbuild/msbuild-items.md) (MSBuild-Elemente)

