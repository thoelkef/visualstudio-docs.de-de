---
title: Problembehandlung für Codeanalysefehler | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
caps.latest.revision: 7
author: erickson-doug
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1b21666094d2a13054be49980028afcc7a7e39a3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49224015"
---
# <a name="troubleshooting-code-analysis-issues"></a>Problembehandlung für Codeanalysefehler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Thema enthält Problembehandlungsinformationen für die folgenden Visual Studio-Codeanalyseprobleme.  
  
-   [Änderungen in einem Visual Studio 2010-Regelsatz werden nicht in vorherigen Versionen von Visual Studio dargestellt](#ChildRuleSetChangesInPreviousVersions)  
  
##  <a name="ChildRuleSetChangesInPreviousVersions"></a>Änderungen in einem Visual Studio 2010-Regelsatz werden nicht in vorherigen Versionen von Visual Studio dargestellt  
 Wenn Sie einen Regelsatz, der einen untergeordneten Regelsatz enthält, in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] erstellen, werden Änderungen an dem untergeordneten Regelsatz möglicherweise nicht in der Codeanalyse von älteren Visual Studio-Versionen angewendet. Um dieses Problem zu beheben müssen Sie den übergeordneten Regelsatz, der den untergeordneten Regelsatz enthält, erneut generieren.  
  
1.  Öffnen Sie den übergeordneten Regelsatz in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)].  
  
2.  Nehmen Sie eine Änderung vor, indem Sie beispielsweise eine Regel hinzufügen oder entfernen, und speichern Sie den Regelsatz anschließend.  
  
3.  Öffnen Sie den Regelsatz erneut, machen die Änderung rückgängig, und speichern Sie den Regelsatz.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)   
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Verwenden von Regelsätzen zum Gruppieren von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)



