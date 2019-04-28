---
title: 'Vorgehensweise: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte'
ms.date: 11/04/2016
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
manager: wpickett
ms.workload:
- cplusplus
ms.openlocfilehash: 11eb9701c900284ee8021f908263bc5f27ab8206
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815823"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Vorgehensweise: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte
Sie können konfigurieren, welche Regeln das Codeanalysetool verwendet, um den Code in jede Konfiguration des Projekts zu analysieren. Darüber hinaus können Sie weiterleiten, Codeanalyse, um Warnungen zu Code zu unterdrücken, die generiert und von einem Drittanbieter-Tool zu Ihrem Projekt hinzugefügt wurde.

## <a name="code-analysis-property-page"></a>Code Analysis-Eigenschaftenseite
 Die **Codeanalyse** Eigenschaftenseite enthält alle Konfigurationseinstellungen der Code-Analyse für ein Projekt. Öffnen Sie die Eigenschaftenseite für die Analyse für ein Projekt in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**. Erweitern Sie als Nächstes, **Konfigurationseigenschaften** , und wählen Sie die **Codeanalyse** Registerkarte.

## <a name="project-configuration-and-platform"></a>Projektkonfiguration und Plattform
 Die **Konfiguration** Liste und **Plattform** Liste können Sie verschiedene codeanalyseeinstellungen auf Konfiguration und Plattform-Kombinationen von anderen Projekt anwenden. Beispielsweise können Sie weiterleiten, Codeanalyse, um eine Reihe von Regeln für Ihr Projekt für das Debuggen gelten erstellt und ein anderen Satz für die Veröffentlichung erstellt.

## <a name="enabling-code-analysis"></a>Aktivieren der Codeanalyse
 Sie können entscheiden, ob die Codeanalyse für Ihr Projekt zu aktivieren, indem **Codeanalyse für C/C++ auf Build aktivieren**. In Kombination mit der **Konfiguration** Liste, Sie können beispielsweise festlegen, zum Deaktivieren der Codeanalyse für Debugbuilds und aktivieren sie für Releasebuilds.

 Wenn das Projekt über verwalteten Code enthält, können Sie entscheiden, ob aktivieren oder deaktivieren dazu Code Analysis **Codeanalyse für Build aktivieren**.

 Codeanalyse soll Ihnen helfen, die Qualität Ihres Codes zu verbessern und häufige Fehler vermeiden. Aus diesem Grund sollten Sie sorgfältig, ob die Codeanalyse deaktiviert. Normalerweise ist es besser, Regelsätze zu deaktivieren, oder einzelne Regeln, die Sie nicht möchten, die auf Ihr Projekt angewendet.

## <a name="generated-code"></a>Generierter Code
 Entwickler verwenden häufig Tools können Sie schnell Anwendungen zu entwickeln. Diese Tools können Code generieren, die dem Projekt hinzugefügt wird. Sie möchten die Verletzungen von Namensregeln anzuzeigen, die Codeanalyse in generiertem Code ermittelt. Möglicherweise möchten Sie jedoch nicht angezeigt, wenn Sie nicht, als die Codewartung möchten.

 Die **Ergebnisse vom generierten Code unterdrücken** auf das Kontrollkästchen der **allgemeine** Eigenschaftenseite können Sie auswählen, ob codeanalysewarnungen aus verwaltetem Code, der von einem Drittanbieter-Tool generiert wird, finden Sie unter werden sollen .

## <a name="rule-sets"></a>Regelsätze
 Wenn Ihr Projekt über verwalteten Code enthält, können Sie auswählen, dass die Regeln in einer Codeanalyse angewendet wird, durch Auswahl eines Regelsatzes aus der **diesen Regelsatz ausführen** Liste.

## <a name="see-also"></a>Siehe auch

- [Analysieren der Qualität von verwaltetem Code](../code-quality/code-analysis-for-managed-code-overview.md)
- [Codeanalyse für C/C++-Warnungen](../code-quality/code-analysis-for-c-cpp-warnings.md)