---
title: Regelsätze für die Codeanalyse
ms.date: 04/02/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.rulesets.learnmore
helpviewer_keywords:
- code analysis, rule sets
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca48d0cad8ad6e22aa2264390d230590438e8579
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77506466"
---
# <a name="use-rule-sets-to-group-code-analysis-rules"></a>Verwenden von Regelsätzen zum Gruppieren von Code Analyse Regeln

Wenn Sie die Code Analyse in Visual Studio konfigurieren, können Sie aus einer Liste integrierter *Regelsätze*auswählen. Bei einem Regelsatz handelt es sich um eine Gruppierung von Code Analyse Regeln, mit denen gezielte Probleme und bestimmte Bedingungen für das Projekt identifiziert werden. Sie können z. b. einen Regelsatz anwenden, der für die Überprüfung von Code auf öffentlich verfügbare APIs konzipiert ist. Sie können auch einen Regelsatz anwenden, der alle verfügbaren Regeln enthält.

Sie können einen Regelsatz anpassen, indem Sie Regeln hinzufügen oder löschen oder Regel Schweregrade ändern, damit Sie im **Fehlerliste**als Warnungen oder Fehler angezeigt werden. Benutzerdefinierte Regelsätze können Sie an Ihre spezielle Entwicklungsumgebung anpassen. Wenn Sie einen Regelsatz anpassen, stellt der Regelsatz-Editor Such-und Filter Tools bereit, die Sie bei diesem Prozess unterstützen.

Regelsätze sind für die [Analyse von verwaltetem Code](analyzer-rule-sets.md), die [Legacy Analyse von verwaltetem Code](how-to-configure-code-analysis-for-a-managed-code-project.md)und [ C++ die Code Analyse](/cpp/code-quality/using-rule-sets-to-specify-the-cpp-rules-to-run)verfügbar.

## <a name="rule-set-format"></a>Regelsatz Format

Ein Regelsatz wird im XML-Format in einer *. RuleSet* -Datei angegeben. Regeln, die aus einer ID und einer *Aktion*bestehen, werden nach Analyse-ID und Namespace in der Datei gruppiert.

Der Inhalt einer *RuleSet* -Datei sieht in etwa wie folgt aus:

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
> Es ist einfacher, [einen Regelsatz](../code-quality/working-in-the-code-analysis-rule-set-editor.md) im grafischen **Regelsatz-Editor** als manuell zu bearbeiten.

## <a name="specify-a-rule-set-for-a-project"></a>Geben Sie einen Regelsatz für ein Projekt an.

Der Regelsatz für ein Projekt wird von der **codeanalysisruleset** -Eigenschaft in der Visual Studio-Projektdatei angegeben. Beispiel:

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

## <a name="see-also"></a>Weitere Informationen

- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)
