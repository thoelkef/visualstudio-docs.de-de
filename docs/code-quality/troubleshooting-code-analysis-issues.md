---
title: Problembehandlung für Codeanalysefehler
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9029c7be21fe02b9d6b1c4436658df74eb3c37f9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
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
 [Analysieren der Anwendungsqualität](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md) [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md) [mithilfe der Regel wird auf Gruppe von Codeanalyseregeln](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)