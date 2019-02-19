---
title: ProjectExtensions-Element (MSBuild) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a8241033be738e7f608f3a83531d6fde52e9361
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54801547"
---
# <a name="projectextensions-element-msbuild"></a>ProjectExtensions-Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Ermöglicht es [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projektdateien, nicht-[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Informationen zu enthalten. Alles innerhalb eines `ProjectExtensions`-Elements wird von [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ignoriert.  
  
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
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Projekt](../msbuild/project-element-msbuild.md)|Erforderliches Stammelement einer [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] -Projektdatei.|  
  
## <a name="remarks"></a>Anmerkungen  
 Nur ein `ProjectExtensions`-Element kann in einem [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]-Projekt verwendet werden.  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel zeigt Informationen aus der IDE, die in einem `ProjectExtensions`-Element gespeichert werden.  
  
```  
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
 [MSBuild](msbuild.md)
