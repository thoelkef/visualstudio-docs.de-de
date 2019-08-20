---
title: Analyse Regelsätze
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68410fd43f182873c27e3d5fed742bed7ba8a4ed
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585134"
---
# <a name="rule-sets-for-analyzer-packages"></a>Regelsätze für Analysepakete

Vordefinierte Regelsätze sind in einigen nuget Analyzer-Paketen enthalten. Beispielsweise aktivieren oder deaktivieren die Regelsätze, die im nuget Analyzer-Paket [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) enthalten sind (beginnend mit Version 2.6.2), Regeln basierend auf ihrer Kategorie, z. b. Sicherheit, Benennung oder Leistung. Durch die Verwendung von Regelsätzen können Sie auf einfache Weise nur die Regel Verletzungen erkennen, die eine bestimmte Regel Kategorie betreffen.

Wenn Sie von der veralteten "FxCop"-Analyse zur .NET Compiler Platform basierten Code Analyse migrieren, können Sie mit diesen Regelsätzen ähnliche Regel Konfigurationen verwenden, [die Sie zuvor verwendet](rule-set-reference.md)haben.

## <a name="use-analyzer-package-rule-sets"></a>Verwenden von analysepaketregelsätzen

Nachdem Sie [ein nuget Analyzer-Paket installiert](install-roslyn-analyzers.md)haben, suchen Sie den vordefinierten Regelsatz im *RuleSets* -Verzeichnis. Wenn Sie z. b. auf `Microsoft.CodeAnalysis.FxCopAnalyzers` das Analysepaket verwiesen haben, finden Sie das zugehörige *RuleSets* -Verzeichnis unter *% User\\profile%\\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\<Version. \>\rulesets*. Kopieren Sie von dort eine oder mehrere der RuleSets, und fügen Sie Sie in das Verzeichnis ein, das das Visual Studio-Projekt enthält, oder direkt in **Projektmappen-Explorer**.

Sie können auch [einen vordefinierten Regelsatz anpassen](how-to-create-a-custom-rule-set.md) . Beispielsweise können Sie den Schweregrad einer oder mehrerer Regeln ändern, sodass Verstöße im **Fehlerliste**als Fehler oder Warnungen angezeigt werden.

## <a name="set-the-active-rule-set"></a>Festlegen des aktiven Regelsatzes

Der Vorgang zum Festlegen des aktiven Regelsatzes ist ein wenig anders, je nachdem, ob Sie über ein .net Core/. NET Standard-Projekt oder ein .NET Framework Projekt verfügen.

### <a name="net-core"></a>.NET Core

Wenn Sie einen Regelsatz für den aktiven Regelsatz für die Analyse in .net Core-oder .NET Standard-Projekten festlegen möchten, fügen Sie die Eigenschaft " **codeanalysisruleset** " manuell zu Ihrer Projektdatei hinzu. Der folgende Code Ausschnitt legt `HelloWorld.ruleset` z. b. den aktiven Regelsatz fest.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

Um einen Regelsatz für den aktiven Regelsatz für die Analyse in .NET Framework Projekten festzulegen, klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus. Wählen Sie auf den Eigenschaften Seiten des Projekts die Registerkarte **Code Analyse** aus. Wählen Sie unter **diesen Regelsatz ausführen**die Option **Durchsuchen**aus, und wählen Sie dann den gewünschten Regelsatz aus, den Sie in das Projektverzeichnis kopiert haben. Nun sehen Sie nur Regel Verletzungen für die Regeln, die im ausgewählten Regelsatz aktiviert sind.

## <a name="available-rule-sets"></a>Verfügbare Regelsätze

Die vordefinierten analyseregelsätze enthalten drei RuleSets, die sich auf alle Regeln im&mdash;Paket auswirken, das Sie alle aktiviert, eine, die alle deaktiviert, und eine, die die Standardeinstellungen für den Schweregrad und die Aktivierung jeder Regel berücksichtigt:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Außerdem gibt es zwei Regelsätze für jede Kategorie von Regeln im Paket, z. b. Leistung oder Sicherheit. Mit einem Regelsatz werden alle Regeln für die Kategorie aktiviert, und ein Regelsatz berücksichtigt die Standardeinstellungen für Schweregrad und Aktivierung für jede Regel in der Kategorie.

Das nuget Analyzer-Paket [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) enthält Regelsätze für die folgenden Kategorien:

- Entwurf
- Dokumentation
- Verwaltbarkeit
- Benennen
- Leistung
- Zuverlässigkeit
- Sicherheit
- Verwendung

## <a name="see-also"></a>Siehe auch

- [FAQ zu Analysetools](analyzers-faq.md)
- [Overview of .NET Compiler Platform analyzers (Übersicht über .NET Compiler Platform-Analysetools)](roslyn-analyzers-overview.md)
- [Installieren von Analyzern](install-roslyn-analyzers.md)
- [Verwenden von Analyzern](use-roslyn-analyzers.md)
- [Verwenden von Regelsätzen zum Gruppieren von Code Analyse Regeln](using-rule-sets-to-group-code-analysis-rules.md)
