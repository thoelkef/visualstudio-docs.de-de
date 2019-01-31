---
title: ItemMetadata-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemMetadata Element [MSBuild]
- <ItemMetadata> Element [MSBuild]
ms.assetid: e3db5122-202d-43a9-b2f4-3e0ec4ed3d08
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6bcc8502d5404308246ac3ece80780e6a0ccadd3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802958"
---
# <a name="itemmetadata-element-msbuild"></a>ItemMetadata-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
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
  
## <a name="remarks"></a>Hinweise  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht das Hinzufügen von `Culture`-Metadaten mit dem Wert `fr` zum Element `CSFile`.  
  
```  
<ItemGroup>  
    <CSFile Include="main.cs" >  
        <Culture>fr</Culture>  
    </CSFile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elemente](../msbuild/msbuild-items.md)
