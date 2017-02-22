---
title: "Problembehandlung f&#252;r Codeanalysefehler | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 5
caps.handback.revision: 5
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
---
# Problembehandlung f&#252;r Codeanalysefehler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Thema enthält Problembehandlungsinformationen für die folgenden Visual Studio\-Codeanalyseprobleme:  
  
-   [Änderungen in einem Visual Studio 2010\-Regelsatz werden nicht in Visual Studio\-Versionen übernommen](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a> Änderungen in einem Visual Studio 2010\-Regelsatz werden nicht in Visual Studio\-Versionen übernommen  
 Wenn Sie in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] einen Regelsatz erstellen, der einen untergeordneten Regelsatz enthält, werden Änderungen an dem untergeordneten Regelsatz bei der Codeanalyse auf Computern mit einer älteren Visual Studio\-Version möglicherweise nicht übernommen.  Erzwingen Sie zum Beheben dieses Problems, dass der übergeordnete Regelsatz \(also der Regelsatz mit dem untergeordneten Regelsatz\) erneut geschrieben wird.  
  
1.  Öffnen Sie den übergeordneten Regelsatz in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Nehmen Sie eine Änderung vor, indem Sie beispielsweise eine Regel hinzufügen oder entfernen, und speichern Sie den Regelsatz anschließend.  
  
3.  Öffnen Sie den Regelsatz erneut, machen Sie die Änderung rückgängig, und speichern Sie den Regelsatz.  
  
## Siehe auch  
 [Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)