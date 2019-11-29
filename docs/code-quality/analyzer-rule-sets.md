---
title: FxCop Analyzer-Regelsätze und Editor config-Dateien
ms.date: 10/08/2019
ms.topic: conceptual
helpviewer_keywords:
- analyzer packages, rule sets
- rule sets for analyzers
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2cf385aaf24db2172a61ddbe7ecf77dcbe40f3c
ms.sourcegitcommit: 08105865a9643fb20dce9b8b7580452cfbbe7ee7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/26/2019
ms.locfileid: "74537773"
---
# <a name="enable-a-category-of-rules"></a>Aktivieren der Regelkategorie

Analysepakete können vordefinierte [Editor config](use-roslyn-analyzers.md#rule-severity) -und [Regel Satz](using-rule-sets-to-group-code-analysis-rules.md) Dateien enthalten, die es Ihnen ermöglichen, eine Kategorie von Regeln, wie z. b. Sicherheits-oder Entwurfs Regeln, schnell und einfach zu aktivieren. Das nuget Analyzer-Paket [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) enthält sowohl Regelsätze (beginnend mit Version 2.6.2) als auch Editor config-Dateien (beginnend mit Version 2.9.5). Indem Sie eine bestimmte Kategorie von Regeln aktivieren, können Sie gezielte Probleme und bestimmte Bedingungen ermitteln.

> [!NOTE]
> Das Aktivieren von Analyse Regeln und das Festlegen Ihres schwere Grads mithilfe einer Editor config-Datei wird ab Visual Studio 2019 Version 16,3 unterstützt.

Das nuget-Paket FxCop Analyzer enthält vordefinierte Regelsätze und Editor config-Dateien für die folgenden Regel Kategorien:

- Alle Regeln
- Datenfluss
- Entwerfen
- Documentation
- Globalisierung
- Interoperabilität
- Verwaltbarkeit
- Ernannte
- Leistung
- Portiert von FxCop
- Zuverlässigkeit
- Sicherheit
- Verwendungs-

Jede dieser Kategorien von Regeln verfügt über eine Editor config-oder Regel Satz Datei für Folgendes:

- alle Regeln in der Kategorie aktivieren (und alle anderen Regeln deaktivieren)
- Standardeinstellung für Schweregrad und Einstellung jeder Regel verwenden (und alle anderen Regeln deaktivieren)

> [!TIP]
> Die Kategorie "alle Regeln" verfügt über eine zusätzliche Editor config-oder Regel Satz Datei, um alle Regeln zu deaktivieren. Verwenden Sie diese Datei, um alle Analyse Warnungen oder-Fehler in einem Projekt schnell zu entfernen.

> [!TIP]
> Wenn Sie von der veralteten "FxCop"-Analyse zur .NET Compiler Platform basierten Code Analyse migrieren, können Sie mit den Editor config-und Regel Satz Dateien ähnliche Regel Konfigurationen verwenden, die [Sie zuvor verwendet](rule-set-reference.md)haben.

## <a name="predefined-editorconfig-files"></a>Vordefinierte Editor config-Dateien

Die vordefinierten Editor config-Dateien für das Microsoft. Code Analysis. fxcopanalyzers Analyzer-Paket befinden sich im Verzeichnis *% User Profile%\\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\\\<Version\>\editor config* . Beispielsweise befindet sich die Editor config-Datei, um alle Sicherheitsregeln zu aktivieren, unter *% User Profile%\\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\\\<Version\>\editor config\securityrulesenabled\\. Editor config*.

Kopieren Sie die ausgewählte Editor config-Datei in das Stammverzeichnis Ihres Projekts.

## <a name="predefined-rule-sets"></a>Vordefinierter Regelsatz

Die vordefinierten Regel Satz Dateien für das Microsoft. Code Analysis. fxcopanalyzers Analyzer-Paket befinden sich im Verzeichnis *% User Profile%\\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\\\<Version\>\rulesets* . Beispielsweise befindet sich die Regel Satz Datei, um alle Sicherheitsregeln zu aktivieren, unter *% User Profile%\\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\\\<Version\>\ruleseung\securityrulesenabled.RuleSet*.

Kopieren Sie mindestens einen Regelsatz, und fügen Sie ihn in das Verzeichnis ein, das das Visual Studio-Projekt enthält, oder direkt in **Projektmappen-Explorer**.

Sie können auch [einen vordefinierten Regelsatz anpassen](how-to-create-a-custom-rule-set.md) . Beispielsweise können Sie den Schweregrad einer oder mehrerer Regeln ändern, sodass Verstöße im **Fehlerliste**als Fehler oder Warnungen angezeigt werden.

### <a name="set-the-active-rule-set"></a>Festlegen des aktiven Regelsatzes

Der Vorgang zum Festlegen des aktiven Regelsatzes ist ein wenig anders, je nachdem, ob Sie über ein .net Core/. NET Standard-Projekt oder ein .NET Framework Projekt verfügen.

#### <a name="net-core"></a>.NET Core

Wenn Sie einen Regelsatz für den aktiven Regelsatz für die Analyse in .net Core-oder .NET Standard-Projekten festlegen möchten, fügen Sie die Eigenschaft " **codeanalysisruleset** " manuell zu Ihrer Projektdatei hinzu. Der folgende Code Ausschnitt legt z. b. `HelloWorld.ruleset` als aktiven Regelsatz fest.

```xml
<PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
  ...
  <CodeAnalysisRuleSet>HelloWorld.ruleset</CodeAnalysisRuleSet>
</PropertyGroup>
```

#### <a name="net-framework"></a>.NET Framework

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

## <a name="see-also"></a>Siehe auch

- [FAQ zu Analysetools](analyzers-faq.md)
- [Overview of .NET Compiler Platform analyzers (Übersicht über .NET Compiler Platform-Analysetools)](roslyn-analyzers-overview.md)
- [Installieren von Analyzern](install-roslyn-analyzers.md)
- [Analysen konfigurieren](use-roslyn-analyzers.md)
- [Verwenden von Regelsätzen zum Gruppieren von Code Analyse Regeln](using-rule-sets-to-group-code-analysis-rules.md)
