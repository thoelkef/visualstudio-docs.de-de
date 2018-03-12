---
title: ProjectExtensions-Element (MSBuild) | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ProjectExtensions
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ProjectExtensions> element [MSBuild]
- ProjectExtensions element [MSBuild]
ms.assetid: f95f312f-ff92-41eb-9469-ad99e236a307
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b0b6ab3795e312cb083dd1237d814e262fa6375e
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions-Element (MSBuild)
Ermöglicht es [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projektdateien, nicht-[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Informationen zu enthalten. Alles innerhalb eines `ProjectExtensions`-Elements wird von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ignoriert.  

 \<Project>  
 \<ProjectExtensions>  

## <a name="syntax"></a>Syntax  

```  
<ProjectExtensions>  
    Non-MSBuild information to include in file.  
</ProjectExtensions>  
```  

## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  

### <a name="attributes"></a>Attribute  
 Keiner  

### <a name="child-elements"></a>Untergeordnete Elemente  
 Keiner  

### <a name="parent-elements"></a>Übergeordnete Elemente  

|Element|description|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] -Projektdatei.|  

## <a name="remarks"></a>Hinweise  
 Nur ein `ProjectExtensions`-Element kann in einem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Projekt verwendet werden.  

## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt Informationen aus der IDE, die in einem `ProjectExtensions`-Element gespeichert werden.  

```xml  
<ProjectExtensions>  
    <VSIDE>  
        <External>  
            <!--  
            Raw XML passed to the IDE by an external source  
            -->  
        </External>  
    </VSIDE>  
</ProjectExtensions>  
```  

## <a name="see-also"></a>Siehe auch  
 [Referenz zum Projektdateischema](../msbuild/msbuild-project-file-schema-reference.md)  
 [MSBuild](../msbuild/msbuild.md)
