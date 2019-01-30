---
title: SDK-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 01/25/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24392fe34069025209f0e2c02e1231d1cbbe3397
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993273"
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

|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Name`|Erforderliches Attribut.<br /><br /> Der Name des Projekt-SDK.|  
|`Version`|Optionales Attribut.<br /><br /> Die Version des Projekt-SDK.|  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente  

| Element | Beschreibung |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] -Projektdatei. |

## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verweisen auf ein MSBuild-Projekt-SDK](../msbuild/how-to-use-project-sdk.md)   
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
