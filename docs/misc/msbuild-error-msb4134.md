---
title: "MSBuild Error MSB4134 | Microsoft Docs"
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
  - "MSB4134"
ms.assetid: 2e4e6beb-c0c9-40ef-b75c-1c16244eba10
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB4134
**MSB4134: DefaultToolsVersion kann nicht festgelegt werden, nachdem ein Projekt in das Modul geladen wurde.**  
  
 Dieser Fehler tritt auf, wenn versucht wurde, den Wert von `DefaultToolsVersion` zu ändern, nachdem [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] bereits ein Projekt erstellt hat.  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Wert von `DefaultToolsVersion`, bevor Sie ein Projekt erstellen.  
  
## Siehe auch  
 <xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>   
 <xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>   
 [Project Element \(MSBuild\)](../msbuild/project-element-msbuild.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)