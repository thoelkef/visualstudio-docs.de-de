---
title: SDK-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Sdk element [MSBuild]
- <Sdk> element [MSBuild]
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d674e7613898816f905e0d0a11bdc2484cf4f25
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325322"
---
# <a name="sdk-element-msbuild"></a>SDK-Element (MSBuild)
Verweist auf ein [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekt-SDK.  

 \<Project>  
 \<Sdk>  


## <a name="syntax"></a>Syntax  

```xml  
<Sdk Name="My.Custom.Sdk"
     Version="1.0.0" />  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  

|Attribut|Beschreibung |  
|---------------|-----------------|  
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projekt-SDK.|  
|`Version`|Optionales Attribut.<br /><br /> Die Version des Projekt-SDK.|  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente  
 |Element|Beschreibung |  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] -Projektdatei.|  

## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verweis auf ein MSBuild-Projekt-SDK](../msbuild/how-to-use-project-sdk.md)   
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
