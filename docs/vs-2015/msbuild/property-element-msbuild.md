---
title: Property-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8b9ebd5207b4fc4a6274090b91e8fa3ab0b20cb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262995"
---
# <a name="property-element-msbuild"></a>Property-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Enthält einen benutzerdefinierten Eigenschaftennamen und -wert. Jedes Element, das in einem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekt verwendet wird, muss als untergeordnetes Element eines `PropertyGroup`-Elements angegeben werden.  
  
 \<Project>  
 \<PropertyGroup>  
  
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
|`Condition`|Optionales Attribut.<br /><br /> Die auszuwertende Bedingung. Weitere Informationen finden Sie unter [Conditions](../msbuild/msbuild-conditions.md) (MSBuild-Bedingungen).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Grouping-Element für Eigenschaften.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist optional.  
  
 Dieser Text gibt den Eigenschaftswert an und enthält möglicherweise XML.  
  
## <a name="remarks"></a>Hinweise  
 Eigenschaftennamen sind auf ASCII-Zeichen beschränkt. Im Projekt wird durch die Platzierung der Eigenschaftenname zwischen „`$(`“ und „`)`“ verwiesen werden. Beispielsweise würde `$(builddir)\classes` in „Build\classes“ aufgelöst, wenn die `builddir`-Eigenschaft den Wert `build` hat. Weitere Informationen zu Eigenschaften finden Sie unter [MSBuild-Eigenschaften](msbuild-properties1.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Code wird die `Optimization`-Eigenschaft auf `false` und die `DefaultVersion`-Eigenschaft auf `1.0` festgelegt, wenn die `Version`-Eigenschaft leer ist.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>Siehe auch
[MSBuild-Eigenschaften](msbuild-properties1.md)  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md) (Referenz zum Projektdateischema von MSBuild)



