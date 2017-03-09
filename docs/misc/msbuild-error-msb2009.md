---
title: "MSBuild Error MSB2009 | Microsoft Docs"
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
  - "MSBuild.UnrecognizedAttribute"
helpviewer_keywords: 
  - "MSB2009"
ms.assetid: 34fd83b4-dead-49e5-b1ee-b23dc5a95244
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB2009
**Das Attribut "\<Attributname\>" des \<Elementname\>\-Elements ist nicht gültig.**  
  
 Der Attributname ist nicht richtig geschrieben oder wird von [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] nicht erkannt.  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Rechtschreibung des Attributnamens.  
  
-   Überprüfen Sie, ob die Projektdatei geändert wurde oder beschädigt ist.  Wenn sie geändert wurde oder beschädigt ist, öffnen Sie das Projekt in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Version, in der es erstellt wurde, speichern Sie es, und versuchen Sie dann erneut, es zu konvertieren.  
  
## Siehe auch  
 [Project File Schema Reference](../msbuild/msbuild-project-file-schema-reference.md)