---
title: ItemDefinitionGroup-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ItemDefinitionGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ItemDefinitionGroup Element [MSBuild]
- <ItemDefinitionGroup> Element [MSBuild]
ms.assetid: 4e9fb04b-5148-4ae5-a394-42861dd62371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbb9e018968c8336c098f36991ee92651c85fd5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512901"
---
# <a name="itemdefinitiongroup-element-msbuild"></a>ItemDefinitionGroup-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ItemDefinitionGroup-Element (MSBuild)](https://docs.microsoft.com/visualstudio/msbuild/itemdefinitiongroup-element-msbuild).  
  
  
Mit dem `ItemDefinitionGroup`-Element können Sie einen Satz von Elementdefinitionen festlegen, die Metadatenwerte sind, die standardmäßig auf alle Elemente im Projekt angewandt werden. Mit ItemDefinitionGroup ist die Verwendung der [CreateItem-Aufgabe](../msbuild/createitem-task.md) und [CreateProperty-Aufgabe](../msbuild/createproperty-task.md) überflüssig. Weitere Informationen finden Sie unter [Item Definitions (Elementdefinitionen)](../msbuild/item-definitions.md).  
  
 \<Project>  
 \<ItemDefinitionGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ItemGroup Condition="'String A' == 'String B'">  
    <Item1>... </Item1>  
    <Item2>... </Item2>  
</ItemGroup>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut. Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Item](../msbuild/item-element-msbuild.md)|Definiert die Eingaben für den Buildprozess. Es kann keine oder mehrere `Item`-Elemente in einer `ItemDefinitionGroup` geben.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projektdatei.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel werden zwei Metadatenelemente, m und n, in einer ItemDefinitionGroup definiert. In diesem Beispiel wird das Standardmetadatum "m" auf das Element "i" angewendet, da das Metadatum "m" nicht explizit durch das Element "i" definiert wird. Das Standardmetadatum "n" wird jedoch nicht auf das Element "i" angewendet, da das Metadatum "n" bereits durch Element "i" definiert ist.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [Elemente](../msbuild/msbuild-items.md)



