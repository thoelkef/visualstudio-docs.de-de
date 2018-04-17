---
title: 'Vorgehensweise: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native
- VC.Project.VCCLCompilerTool.EnablePrefast
- VC.Project.VCFxCopTool.EnablePREfast
- VC.Project.VCFxCopTool.IgnoreGeneratedCode
helpviewer_keywords:
- properties, C/C++ Code Analysis
- properties, Code Analysis
- code analysis properties
- C/C++ code analysis properties
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
author: mikeblome
ms.author: mblome
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 89671da363d6079ad7a81dc41f1c6f82b713d32d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Gewusst wie: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte
Sie können konfigurieren, welche Regeln das Codeanalysetool verwendet wird, um den Code in den einzelnen Konfigurationen Ihres Projekts analysieren. Darüber hinaus können Sie die Codeanalyse unterdrücken von Warnungen zu Code, die generiert wurde, und dem Projekt hinzugefügt, von einem Drittanbieter-Tool weiterleiten.  
  
## <a name="code-analysis-property-page"></a>Code Analysis-Eigenschaftenseite  
 Die **Codeanalyse** Eigenschaftenseite enthält alle Code Analysis-Konfigurationseinstellungen für ein Projekt. Öffnen Sie die Eigenschaftenseite für die Analyse für ein Projekt im **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**. Erweitern Sie als Nächstes **Konfigurationseigenschaften** , und wählen Sie die **Codeanalyse** Registerkarte.  
  
## <a name="project-configuration-and-platform"></a>Projektkonfiguration und Plattform  
 Die **Konfiguration** Liste und **Plattform** Liste können Sie die verschiedenen codeanalyseeinstellungen für Kombinationen aus anderen Projekt Konfiguration und Plattform gelten. Sie können z. B. weiterleiten Codeanalyse, um eine Reihe von Regeln für Ihr Projekt für das Debuggen gelten erstellt und ein anderen Satz für Version erstellt.  
  
## <a name="enabling-code-analysis"></a>Codeanalyse aktivieren  
 Sie können entscheiden, ob die Codeanalyse für das Projekt zu aktivieren, indem **Analyse für C/C++ auf Build aktivieren**. In Kombination mit der **Konfiguration** Liste, könnten Sie z. B. möchten, deaktivieren die Codeanalyse für Debug-Builds und aktivieren sie für Releasebuilds.  
  
 Wenn Ihr Projekt verwalteten Code enthält, können Sie entscheiden, ob aktivieren oder deaktivieren dazu Codeanalyse **Codeanalyse für Build aktivieren**.  
  
 Codeanalyse dient zum Verbessern der Qualität des Codes und häufige Fehlerquellen vermeiden. Aus diesem Grund sollten Sie sorgfältig, ob die Codeanalyse deaktiviert. Es ist in der Regel besser, Regelsätze deaktivieren, oder einzelne Regeln, die Sie nicht möchten, die auf das Projekt angewendet.  
  
## <a name="generated-code"></a>Generierter Code  
 Entwickler verwenden oft Tools helfen beim Entwickeln von Anwendungen schnell. Diese Tools können Code generieren, die dem Projekt hinzugefügt wird. Möglicherweise möchten die Verletzungen von Schwellenwertregeln angezeigt, die Codeanalyse in generiertem Code ermittelt. Möglicherweise möchten Sie jedoch nicht angezeigt, wenn Sie nicht, um den Code beizubehalten möchten.  
  
 Die **Ergebnisse vom generierten Code unterdrücken** Kontrollkästchen auf der **allgemeine** Eigenschaftenseite können Sie auswählen, ob Warnungen der Codeanalyse von verwaltetem Code, der von einem Drittanbieter-Tool generiert wird, angezeigt werden soll .  
  
## <a name="rule-sets"></a>Regelsätze  
 Wenn Ihr Projekt verwalteten Code enthält, können Sie auswählen, dass die Regeln in einer Codeanalyse angewendet werden, durch Auswahl eines Regelsatzes aus der **diesen Regelsatz ausführen** Liste.  
  
## <a name="see-also"></a>Siehe auch  
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Codeanalyse für C/C++-Warnungen](../code-quality/code-analysis-for-c-cpp-warnings.md)