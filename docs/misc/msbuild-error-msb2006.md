---
title: "MSBuild Error MSB2006 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.UnrecognizedElement"
helpviewer_keywords: 
  - "MSB2006"
ms.assetid: 89dc1b89-1621-46bc-9fe6-6d98cbcbebc8
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB2006
**In der Projektdatei ist das \<Projekt\>\-Stammelement nicht enthalten.**  
  
 Der Stammelementname ist nicht richtig geschrieben oder wird von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nicht erkannt.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Rechtschreibung des Elementnamens.  
  
-   Überprüfen Sie, ob die Projektdatei geändert wurde oder beschädigt ist.  Wenn sie geändert wurde oder beschädigt ist, öffnen Sie das Projekt in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Version, in der es erstellt wurde, speichern Sie es, und versuchen Sie dann erneut, es zu konvertieren.  
  
## Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)   
 [Additional Resources](../msbuild/additional-msbuild-resources.md)