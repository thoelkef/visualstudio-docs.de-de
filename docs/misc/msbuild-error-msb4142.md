---
title: "MSBuild-Fehler MSB4142 | Microsoft Docs"
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
  - "MSB4142"
ms.assetid: 56121c76-f952-43d1-ba23-1d1792fef0bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild-Fehler MSB4142
**MSB4142: MSBuildToolsPath ist mit MSBuildBinPath für die ToolsVersion "\<x.x\>" nicht identisch.**  
  
 Die Toolsetdefinition gibt andere Werte für `MSBuildBinPath` und `MSBuildToolsPath` an.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Werte für `MSBuildBinPath` und `MSBuildToolsPath` die gleichen wie in der Toolsetdefinition sind.  
  
## Siehe auch  
 [Standard and Custom Toolset Configurations](../msbuild/standard-and-custom-toolset-configurations.md)   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)