---
title: "Property-Element (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
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
  - "< Property >-Element [MSBuild]"
  - "Property-Element [MSBuild]"
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Property-Element (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein benutzerdefinierter Eigenschaftenname und Wert enthält. Jede Eigenschaft, die in verwendet ein [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] Projekt muss angegeben werden, als untergeordnetes Element ein `PropertyGroup` Element.  
  
 \< Projekt>  
 \< PropertyGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Condition`|Optionales Attribut.<br /><br /> Die Bedingung ausgewertet werden soll. Weitere Informationen finden Sie unter [Bedingungen](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Gruppierungselement für Eigenschaften.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist optional.  
  
 Dieser Text gibt den Eigenschaftswert an und enthält möglicherweise XML.  
  
## <a name="remarks"></a>Hinweise  
 Eigenschaftennamen sind ASCII-Zeichen enthalten. Eigenschaftswerte im Projekt verwiesen werden, durch die Platzierung der Eigenschaftenname zwischen "`$(`"und"`)`". Z. B. `$(builddir)\classes` würde in "Build\classes" aufgelöst, wenn die `builddir` Eigenschaft hat den Wert `build`. Weitere Informationen zu Eigenschaften finden Sie unter [MSBuild-Eigenschaften](../msbuild/msbuild-properties.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden code wird die `Optimization` -Eigenschaft `false` und die `DefaultVersion` Eigenschaft `1.0` Wenn die `Version` -Eigenschaft ist leer.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Siehe auch
[MSBuild-Eigenschaften](../msbuild/msbuild-properties.md)  
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)