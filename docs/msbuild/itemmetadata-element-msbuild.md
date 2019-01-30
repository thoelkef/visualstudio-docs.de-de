---
title: ItemMetadata-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78be9b906efd9720d9bc7ccdbe09614899ef6818
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989587"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata-Element (MSBuild)
Enthält einen benutzerdefinierten Elementmetadatenschlüssel, der den Elementmetadatenwert enthält. Ein Element kann über eine beliebige Anzahl von Metadaten-Schlüssel-Wert-Paaren verfügen.  

 \<Project>  
 \<ItemGroup>  
 \<Item>  

## <a name="syntax"></a>Syntax  

```xml  
<ItemMetadataName> Item Metadata value</ItemMetadataName>  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|Beschreibung|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Ein benutzerdefiniertes Element, das die Eingaben für den Buildprozess definiert.|  

## <a name="text-value"></a>Textwert  
 Ein Textwert ist optional.  

 Dieser Text legt den Elementmetadatenwert fest, der im Text- oder XML-Format vorhanden sein kann.  

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
 [Elemente](../msbuild/msbuild-items.md)
