---
title: Property-Element (MSBuild) | Microsoft-Dokumentation
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
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 958692d9227017eba0901ddb48a19502af9ec452
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54769194"
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
  
## <a name="remarks"></a>Anmerkungen  
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
