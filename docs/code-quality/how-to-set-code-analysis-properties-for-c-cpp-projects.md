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
ms.openlocfilehash: 72866618383382389ad5e5706ae2a0999c89c346
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923984"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Vorgehensweise: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte
Sie können konfigurieren, welche Regeln das Code Analysetool verwendet, um den Code in jeder Konfiguration des Projekts zu analysieren. Außerdem können Sie die Code Analyse weiterleiten, um Warnungen aus dem Code zu unterdrücken, der von einem Drittanbieter Tool generiert und Ihrem Projekt hinzugefügt wurde.

## <a name="code-analysis-property-page"></a>Code Analyse (Eigenschaften Seite)
Die Eigenschaften Seite **Code Analyse** enthält alle Konfigurationseinstellungen für die Code Analyse für ein Projekt. Um die Eigenschaften Seite Code Analyse für ein Projekt in **Projektmappen-Explorer**zu öffnen, klicken Sie mit der rechten Maustaste auf das Projekt, und klicken Sie dann auf **Eigenschaften**. Erweitern Sie als nächstes **Konfigurations Eigenschaften** , und wählen Sie die Registerkarte **Code Analyse** aus.

## <a name="project-configuration-and-platform"></a>Projekt Konfiguration und Plattform
Mithilfe der **Konfigurations** Liste und der **Platt Form** Liste können Sie verschiedene Code Analyse Einstellungen auf verschiedene Projekt Konfigurationen und Platt Form Kombinationen anwenden. Beispielsweise können Sie die Code Analyse weiterleiten, um einen Satz von Regeln auf das Projekt für Debugbuilds und einen anderen Satz für Releasebuilds anzuwenden.

## <a name="enabling-code-analysis"></a>Aktivieren der Code Analyse
Sie können entscheiden, ob die Code Analyse für Ihr Projekt aktiviert werden soll, indem Sie **Code AnalyseC++ für C/on-Build aktivieren**auswählen. In Kombination mit der **Konfigurations** Liste können Sie z. b. entscheiden, die Code Analyse für Debugbuilds zu deaktivieren und für Releasebuilds zu aktivieren.

Wenn das Projekt verwalteten Code enthält, können Sie entscheiden, ob Sie die Code Analyse aktivieren oder deaktivieren möchten, indem Sie **Code Analyse beim Build aktivieren**auswählen.

Die Code Analyse soll Sie dabei unterstützen, die Qualität Ihres Codes zu verbessern und häufige Fehler zu vermeiden. Daher sollten Sie sorgfältig überlegen, ob die Code Analyse deaktiviert werden soll. Es ist in der Regel besser, Regelsätze oder einzelne Regeln zu deaktivieren, die nicht auf Ihr Projekt angewendet werden sollen.

## <a name="generated-code"></a>Generierter Code
Entwickler verwenden häufig Tools, mit denen Sie Anwendungen schnell entwickeln können. Diese Tools können Code generieren, der dem Projekt hinzugefügt wird. Möglicherweise möchten Sie die Regel Verletzungen sehen, die von der Code Analyse in generiertem Code erkannt werden. Sie möchten Sie jedoch möglicherweise nicht anzeigen, wenn Sie den Code nicht beibehalten möchten.

Mithilfe des Kontrollkästchens **Ergebnisse aus generiertem Code unterdrücken** auf der Seite **Allgemeine** Eigenschaften können Sie auswählen, ob Code Analyse Warnungen von verwaltetem Code angezeigt werden sollen, der von einem Drittanbieter Tool generiert wird.

## <a name="rule-sets"></a>Regelsätze
Wenn das Projekt verwalteten Code enthält, können Sie die Regeln auswählen, die in einer Code Analyse angewendet werden sollen, indem Sie in der Liste **diesen Regelsatz ausführen** einen Regelsatz auswählen.

## <a name="see-also"></a>Siehe auch

- [Analysieren der Qualität von verwaltetem Code](../code-quality/code-analysis-for-managed-code-overview.md)
- [Codeanalyse für C/C++-Warnungen](../code-quality/code-analysis-for-c-cpp-warnings.md)