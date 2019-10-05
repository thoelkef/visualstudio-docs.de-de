---
title: FxCop-Analyse Regelsätze
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 313b578743fd734da3354989a8cee16022779242
ms.sourcegitcommit: 39a04f42d23597b70053686d7e927ba78f38a9a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/05/2019
ms.locfileid: "71974695"
---
# <a name="rule-sets-for-analyzer-packages"></a>Regelsätze für Analysepakete

Vordefinierte Regelsätze sind in einigen nuget Analyzer-Paketen enthalten. Beispielsweise aktivieren oder deaktivieren die Regelsätze, die im nuget Analyzer-Paket [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) enthalten sind (beginnend mit Version 2.6.2), Regeln basierend auf ihrer Kategorie, z. b. Sicherheit, Benennung oder Leistung. Durch die Verwendung von Regelsätzen können Sie auf einfache Weise nur die Regel Verletzungen erkennen, die eine bestimmte Regel Kategorie betreffen.

Bei einem Regelsatz handelt es sich um eine Gruppierung von Code Analyse Regeln, mit denen gezielte Probleme und bestimmte Bedingungen identifiziert werden. Regelsätze ermöglichen das Aktivieren oder Deaktivieren von Regeln und Festlegen des schwere Grads einzelner Regel Verletzungen. Das nuget-Paket FxCop Analyzer enthält vordefinierte Regelsätze für die folgenden Regel Kategorien:

- Entwurf
- Dokumentation
- Verwaltbarkeit
- Benennen
- Leistung
- Zuverlässigkeit
- Sicherheit
- Verwendung

Wenn Sie von der veralteten "FxCop"-Analyse zur .NET Compiler Platform basierten Code Analyse migrieren, können Sie mit diesen Regelsätzen ähnliche Regel Konfigurationen verwenden, [die Sie zuvor verwendet](rule-set-reference.md)haben.

## <a name="use-analyzer-package-rule-sets"></a>Verwenden von analysepaketregelsätzen

Nachdem Sie [ein nuget Analyzer-Paket installiert](install-roslyn-analyzers.md)haben, suchen Sie den vordefinierten Regelsatz im *RuleSets* -Verzeichnis. Wenn Sie z. b. auf das `Microsoft.CodeAnalysis.FxCopAnalyzers` Analyzer-Paket verwiesen haben, finden Sie das *zugehörige RuleSets* -Verzeichnis unter *% User Profile% \\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers @ no__t-4 @ no__t-5version @ no__t-6\rulesets*. Kopieren Sie von dort eine oder mehrere der RuleSets, und fügen Sie Sie in das Verzeichnis ein, das das Visual Studio-Projekt enthält, oder direkt in **Projektmappen-Explorer**.

Sie können auch [einen vordefinierten Regelsatz anpassen](how-to-create-a-custom-rule-set.md) . Beispielsweise können Sie den Schweregrad einer oder mehrerer Regeln ändern, sodass Verstöße im **Fehlerliste**als Fehler oder Warnungen angezeigt werden.

## <a name="set-the-active-rule-set"></a>Festlegen des aktiven Regelsatzes

Der Vorgang zum Festlegen des aktiven Regelsatzes ist ein wenig anders, je nachdem, ob Sie über ein .net Core/. NET Standard-Projekt oder ein .NET Framework Projekt verfügen.

### <a name="net-core"></a>.NET Core

Wenn Sie einen Regelsatz für den aktiven Regelsatz für die Analyse in .net Core-oder .NET Standard-Projekten festlegen möchten, fügen Sie die Eigenschaft " **codeanalysisruleset** " manuell zu Ihrer Projektdatei hinzu. Der folgende Code Ausschnitt legt z. b. `HelloWorld.ruleset` als aktiven Regelsatz fest.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

### <a name="net-framework"></a>.NET Framework

So erstellen Sie einen Regelsatz für den aktiven Regelsatz für die Analyse in .NET Framework Projekten:

- Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften**aus.

- Wählen Sie auf den Eigenschaften Seiten des Projekts die Registerkarte **Code Analyse** aus.

::: moniker range="vs-2017"

- Wählen Sie unter **diesen Regelsatz ausführen**die Option **Durchsuchen**aus, und wählen Sie dann den gewünschten Regelsatz aus, den Sie in das Projektverzeichnis kopiert haben.

::: moniker-end

::: moniker range=">=vs-2019"

- Wählen Sie unter **aktive Regeln**die Option **Durchsuchen**aus, und wählen Sie dann den gewünschten Regelsatz aus, den Sie in das Projektverzeichnis kopiert haben.

::: moniker-end

   Nun sehen Sie nur Regel Verletzungen für die Regeln, die im ausgewählten Regelsatz aktiviert sind.

## <a name="available-rule-sets"></a>Verfügbare Regelsätze

Die vordefinierten analyseregelsätze enthalten drei RuleSets, die sich auf alle Regeln im Paket @ no__t-0one auswirken, das Sie alle aktiviert, eine, die alle deaktiviert, und eine, die die Standardeinstellungen für den Schweregrad und die Aktivierung der Regel berücksichtigt:

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
- [Analysen konfigurieren](use-roslyn-analyzers.md)
- [Verwenden von Regelsätzen zum Gruppieren von Code Analyse Regeln](using-rule-sets-to-group-code-analysis-rules.md)
