---
title: Problembehandlung für Codeanalysefehler
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: 61c7e44d-2780-4df5-9bcb-49e40c1152fc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1285a3e7bcd96d06ed4cc4910f4cebdec83ee86c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
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