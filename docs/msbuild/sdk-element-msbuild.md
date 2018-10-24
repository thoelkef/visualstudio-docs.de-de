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
ms.openlocfilehash: 1069a22e700eebfd9d1e8c387af99cf4241ffbe0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834174"
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

| Element | Beschreibung  |
| - | - |
| [Projekt](../msbuild/project-element-msbuild.md) | Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] -Projektdatei. |

## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verweis auf ein MSBuild-Projekt-SDK](../msbuild/how-to-use-project-sdk.md)   
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)
