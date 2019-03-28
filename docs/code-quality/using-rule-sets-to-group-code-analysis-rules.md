---
title: Regelsätze für die Codeanalyse
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c95b442835289265d197b6806c6d87fa051f2c1b
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515232"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Verwenden von Regelsätzen zum Gruppe von Codeanalyseregeln

Wenn Sie die Codeanalyse in Visual Studio konfigurieren, können Sie aus einer Liste von integrierten *-Regelsätze*. Ein Regelsatz ist eine Gruppierung von Codeanalyseregeln, die gezielte Probleme und bestimmte Bedingungen für das Projekt zu identifizieren. Beispielsweise können Sie einen Regelsatz anwenden, der entwickelt wurde, um Code auf öffentlich verfügbare APIs überprüft. Sie können auch einen Regelsatz anwenden, der alle verfügbaren Regeln enthält.

Sie können einen Regelsatz durch Regeln hinzufügen oder löschen oder ändern die Regel Schweregrade als Warnungen oder Fehler angezeigt werden Anpassen der **Fehlerliste**. Benutzerdefinierte Regelsätze können Sie an Ihre spezielle Entwicklungsumgebung anpassen. Wenn Sie einen Regelsatz anpassen, bietet der Regelsatz-Editor suchen und Filtern von Tools, die Sie während des Vorgangs helfen.

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

## <a name="specify-a-rule-set-for-a-project"></a>Geben Sie einen Regelsatz für ein Projekt

Der Regelsatz für ein Projekt, indem angegeben wird die **CodeAnalysisRuleSet** Eigenschaft in der Visual Studio-Projektdatei. Zum Beispiel:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Siehe auch

- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)