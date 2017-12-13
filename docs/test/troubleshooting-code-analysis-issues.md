---
title: "Problembehandlung für Codeanalysefehler | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: "5"
author: erickson-doug
ms.author: douge
manager: douge
ms.openlocfilehash: 3ef4a68d7b5cc8f904ea84f961083b3d7de24ef6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-code-analysis-issues"></a>Problembehandlung für Codeanalysefehler
Dieses Thema enthält Problembehandlungsinformationen für die folgenden Visual Studio-Codeanalyseprobleme.  
  
-   [Änderungen in einem Visual Studio 2010-Regelsatz werden nicht in vorherigen Versionen von Visual Studio dargestellt](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Änderungen in einem Visual Studio 2010-Regelsatz werden nicht in vorherigen Versionen von Visual Studio dargestellt  
 Wenn Sie einen Regelsatz, der einen untergeordneten Regelsatz enthält, in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] erstellen, werden Änderungen an dem untergeordneten Regelsatz möglicherweise nicht in der Codeanalyse von älteren Visual Studio-Versionen angewendet. Um dieses Problem zu beheben müssen Sie den übergeordneten Regelsatz, der den untergeordneten Regelsatz enthält, erneut generieren.  
  
1.  Öffnen Sie den übergeordneten Regelsatz in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)].  
  
2.  Nehmen Sie eine Änderung vor, indem Sie beispielsweise eine Regel hinzufügen oder entfernen, und speichern Sie den Regelsatz anschließend.  
  
3.  Öffnen Sie den Regelsatz erneut, machen die Änderung rückgängig, und speichern Sie den Regelsatz.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)