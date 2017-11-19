---
title: "Problembehandlung für Codeanalysefehler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6e552570eb48b9210b366ebbfe157fe656ab3fe0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>Problembehandlung für Codeanalysefehler
Dieses Thema enthält Informationen zur Problembehandlung für die folgenden Visual Studio-Codeanalysefehler.  
  
-   [Änderungen in einem Visual Studio 2010 Regel Satz nicht widergespiegelt, die in früheren Versionen von Visual Studio](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Änderungen in einem Visual Studio 2010 Regel Satz nicht widergespiegelt, die in früheren Versionen von Visual Studio  
 Beim Erstellen eines Regelsatzes [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] , einen untergeordneten Regelsatz enthält, wird eine Änderung an den untergeordneten Regelsatz in Codeanalysen bei Computern mit einer früheren Version von Visual Studio nicht angewendet werden. Um dieses Problem zu beheben, müssen Sie eine neue Version des Regelsatzes übergeordneten erzwingen, die dem Regelsatz ist, der den untergeordneten Regelsatz enthält.  
  
1.  Öffnen Sie die übergeordnete Regel festgelegt [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Nehmen Sie eine Änderung vor, z. B. hinzufügen oder Löschen einer Regel, und speichern Sie den Regelsatz.  
  
3.  Öffnen Sie den Regelsatz erneut, die Änderung rückgängig zu machen und speichern Sie dann den Regelsatz erneut.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)