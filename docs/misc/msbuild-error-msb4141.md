---
title: "MSBuild-Fehler MSB4141 | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4141"
ms.assetid: 0d190884-e64d-4d6b-817d-ce4644788fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild-Fehler MSB4141
**MSB4141: MSBuildToolsPath ist für die ToolsVersion "\<x.x\>" nicht angegeben.**  
  
 Ein benutzerdefiniertes Toolset ist definiert, es ist jedoch kein Wert für `MSBuildToolsPath` angegeben.  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie beim Definieren eines benutzerdefinierten Toolsets in der Registrierung oder der [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Konfigurationsdatei einen gültigen Wert für `MSBuildToolsPath` an.  
  
## Siehe auch  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)