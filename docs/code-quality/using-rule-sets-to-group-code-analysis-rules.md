---
title: Regelsätze für die Codeanalyse
ms.date: 04/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa287570213e6238d0a8dffc9f6e70367b133591
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204426"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Verwenden von Regelsätzen zum Gruppe von Codeanalyseregeln

Wenn Sie die Codeanalyse in Visual Studio konfigurieren, können Sie aus einer Liste von integrierten *-Regelsätze*. Ein Regelsatz gilt für ein Projekt, und es ist eine Gruppierung von Code Analyseregeln, die gezielte Probleme und bestimmte Bedingungen für das Projekt zu identifizieren. Beispielsweise können Sie einen Regelsatz, der mit dem Code auf öffentlich verfügbare APIs überprüft anwenden, oder nur die empfohlene Mindestregeln für eigene. Sie können auch einen Regelsatz anwenden, der alle Regeln enthält.

Sie können einen Regelsatz durch Hinzufügen oder Löschen von Regeln oder durch Ändern der Regel Schweregrade als Warnungen oder Fehler angezeigt werden Anpassen der **Fehlerliste**. Benutzerdefinierte Regelsätze können Sie an Ihre spezielle Entwicklungsumgebung anpassen. Wenn Sie einen Regelsatz anpassen, bietet der Regelsatz-Editor suchen und Filtern von Tools, die Sie während des Vorgangs helfen.

Regelsätze stehen für [statische Analyse von verwaltetem Code](how-to-configure-code-analysis-for-a-managed-code-project.md), [Analyse von C++-Code](using-rule-sets-to-specify-the-cpp-rules-to-run.md), und [Roslyn-Analysetools](analyzer-rule-sets.md).

## <a name="rule-set-format"></a>Regel festgelegten format

Ein Regelsatz wird angegeben, in der XML-Format in eine *ruleSet* Datei. Regeln, die eine ID enthalten und eine *Aktion*, werden die Analysetool-ID und den Namespace in der Datei gruppiert werden.

Den Inhalt einer *ruleSet* Datei ähnlich wie in dieser XML-Code:

```xml
<RuleSet Name="Rules for Hello World project" Description="These rules focus on critical issues for the Hello World app." ToolsVersion="10.0">
  <Localization ResourceAssembly="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.dll" ResourceBaseName="Microsoft.VisualStudio.CodeAnalysis.RuleSets.Strings.Localized">
    <Name Resource="HelloWorldRules_Name" />
    <Description Resource="HelloWorldRules_Description" />
  </Localization>
  <Rules AnalyzerId="Microsoft.Analyzers.ManagedCodeAnalysis" RuleNamespace="Microsoft.Rules.Managed">
    <Rule Id="CA1001" Action="Warning" />
    <Rule Id="CA1009" Action="Warning" />
    <Rule Id="CA1016" Action="Warning" />
    <Rule Id="CA1033" Action="Warning" />
  </Rules>
  <Rules AnalyzerId="Microsoft.CodeQuality.Analyzers" RuleNamespace="Microsoft.CodeQuality.Analyzers">
    <Rule Id="CA1802" Action="Error" />
    <Rule Id="CA1814" Action="Info" />
    <Rule Id="CA1823" Action="None" />
    <Rule Id="CA2217" Action="Warning" />
  </Rules>
</RuleSet>
```

> [!TIP]
> Es ist einfacher, [bearbeiten ein Regelsatzes](../code-quality/working-in-the-code-analysis-rule-set-editor.md) im grafischen **Regelsatz-Editor** als von hand.

Der Regelsatz für ein Projekt, indem angegeben wird die **CodeAnalysisRuleSet** Eigenschaft in der Visual Studio-Projektdatei. Zum Beispiel:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>Siehe auch

- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)