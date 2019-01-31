---
title: PropertyGroup-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#PropertyGroup
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <PropertyGroup> element [MSBuild]
- PropertyGroup element [MSBuild]
ms.assetid: ff1e6c68-b9a1-4263-a1ce-dc3b829a64d4
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb3ae2ba566c42ef1cde10e4a758fe8f9698ed13
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54772526"
---
# <a name="propertygroup-element-msbuild"></a>PropertyGroup-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Enthält eine Reihe von benutzerdefinierten [Eigenschaft](../msbuild/property-element-msbuild.md)-Elementen. Jedes `Property`-Element, das in einem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekt verwendet wird, muss ein untergeordnetes Element eines `PropertyGroup`-Elements sein.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>Syntax  
  
```  
<PropertyGroup Condition="'String A' == 'String B'">  
    <Property1>...</Property1>  
    <Property2>...</Property2>  
</PropertyGroup>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|Bedingung|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Eigenschaft](../msbuild/property-element-msbuild.md)|Optionales Element.<br /><br /> Ein benutzerdefinierter Eigenschaftenname, der den Wert der Eigenschaft enthält. Es kann kein oder mehrere *Eigenschafts*-Elemente in einem `PropertyGroup`-Element geben.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] -Projektdatei.|  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Einstellung von Eigenschaften auf der Grundlage einer Bedingung veranschaulicht. Wenn der Wert der `CompileConfig`-Eigenschaft in diesem Beispiel `DEBUG`, `Optimization`, `Obfuscate` ist und `OutputPath`-Eigenschaften im `PropertyGroup`-Element festgelegt sind.  
  
```  
<PropertyGroup Condition="'$(CompileConfig)' == 'DEBUG'" >  
    <Optimization>false</Optimization>  
    <Obfuscate>false</Obfuscate>  
    <OutputPath>$(OutputPath)\debug</OutputPath>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md) (Referenz zum Projektdateischema von MSBuild)  
 [MSBuild-Eigenschaften](msbuild-properties1.md)
