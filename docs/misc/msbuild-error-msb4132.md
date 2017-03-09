---
title: "MSBuild Error MSB4132 | Microsoft Docs"
ms.custom: ""
ms.date: "11/23/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSB4132"
ms.assetid: 4ac265a7-0f8d-4fec-ba6e-cd70cbd5d89e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB4132
**MSB4132: Die Toolsversion "'\<Version\>'" ist unbekannt.**  
  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] konnte ein Toolset finden, das dem angegebenen Wert von `ToolsVersion` entspricht.  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie einen gültigen Wert für `ToolsVersion` im Projekttag oder in der Befehlszeile an, wenn Sie den **\/ToolsVersion**\-Schalter von MSBuild verwenden.  
  
## Siehe auch  
 <xref:Microsoft.Build.Tasks.MSBuild.ToolsVersion%2A>   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)