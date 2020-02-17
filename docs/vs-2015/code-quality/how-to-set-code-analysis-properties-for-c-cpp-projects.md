---
title: 'Gewusst wie: Festlegen von Code Analyse Eigenschaften für CC++ -Projekte | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: b2fb3cb81b49fd4b8cc83e0548110d2025c7488d
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277987"
---
# <a name="how-to-set-code-analysis-properties-for-cc-projects"></a>Gewusst wie: Festlegen von Codeanalyseeigenschaften für C/C++-Projekte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Weitere Informationen  
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Codeanalyse für C/C++-Warnungen](../code-quality/code-analysis-for-c-cpp-warnings.md)
