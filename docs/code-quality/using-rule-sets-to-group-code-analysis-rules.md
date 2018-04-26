---
title: Regel zur Codeanalyse legt in Visual Studio
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
ms.openlocfilehash: 20e727fd331ebd98a74acbb63738e6921e5ad1a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Verwenden von Regelsätzen zum Gruppe von Codeanalyseregeln

Wenn Sie die Codeanalyse in Visual Studio konfigurieren, können Sie auswählen, aus einer Liste integrierter *-Regelsätze*. Ein Regelsatz gilt für ein Projekt, und es ist eine Gruppierung von Code Analyseregeln, die gezielte Probleme und bestimmte Bedingungen für dieses Projekt zu identifizieren. Angenommen, Sie können einen Regelsatz, der mit dem Code auf öffentlich verfügbare APIs überprüft anwenden oder nur die empfohlene Mindestregeln für eigene. Sie können auch einen Regelsatz anwenden, der alle Regeln enthält.

Sie können anpassen ein Regelsatzes durch Hinzufügen oder Löschen von Regeln oder durch Ändern der Regel Schweregrade als Warnungen oder Fehler im angezeigt werden die **Fehlerliste**. Benutzerdefinierte Regelsätze können Sie an Ihre spezielle Entwicklungsumgebung anpassen. Wenn Sie einen Regelsatz anpassen, bietet den Regelsatz-Editor Such- und Filtertools hilft Ihnen bei den Vorgang.

## <a name="rule-set-format"></a>Regelsatz-format

Ein Regelsatz wird angegeben, im XML-Format in eine *ruleSet* Datei. Regeln, die eine ID umfassen und ein *Aktion*, gruppiert nach Analyzer-ID und den Namespace in der Datei.

Der XML-Inhalt von einem *ruleSet* Datei sieht etwa wie folgt:

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
> Es ist einfacher, [bearbeiten ein Regelsatzes](../code-quality/working-in-the-code-analysis-rule-set-editor.md) im grafischen **Regelsatz-Editor** als per hand katalogisiert wird.

Der Regelsatz für ein Projekt, durch angegeben wird die `CodeAnalysisRuleSet` Eigenschaft in der Visual Studio-Projektdatei. Zum Beispiel:

```xml
<CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
```

## <a name="see-also"></a>Siehe auch

- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)
