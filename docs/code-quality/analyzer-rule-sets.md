---
title: Analyzer-Regelsätze
ms.date: 07/20/2018
ms.topic: conceptual
helpviewer_keywords:
- analyzers, rule sets
- rule sets for analyzers
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: da5eab1424ac6f6fe580ec0f71ec3efd6e120020
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57866996"
---
# <a name="rule-sets-for-roslyn-analyzers"></a>Regelsätze für Roslyn-Analysetools

Vordefinierten Regelsätzen sind einige Analyzer-NuGet-Pakete enthalten. Z. B. die Regelsätze, die enthalten sind die [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) NuGet-Analyzer-Paket (ab Version 2.6.2) aktivieren oder Deaktivieren von Regeln basierend auf ihrer Kategorie, z. B. Sicherheit, Benennung von oder die Leistung. Verwenden von Regelsätzen erleichtert es, nur diese Verletzungen von Namensregeln schnell zu erkennen, die auf einer bestimmten Kategorie der Regel beziehen.

Wenn Sie über ältere "FxCop" statische Codeanalyse zu Roslyn-Analysetools migrieren, aktivieren diese Regelsätze Sie weiterhin mithilfe der gleichen Regelkonfigurationen, die Sie zuvor verwendet.

## <a name="use-analyzer-rule-sets"></a>Verwenden von Regelsätzen für analyzer

Nach dem [installieren ein NuGet-Pakets Analyzer](install-roslyn-analyzers.md), suchen Sie die vordefinierten Regeln in der *Rulesets* Verzeichnis, z. B. *% USERPROFILE%\\.nuget\packages\ Microsoft.codequality.Analyzers\<Version > \rulesets*. Von dort Sie können ziehen und ablegen, oder kopieren und einfügen, eine oder mehrere der die Rulesets mit Ihrem Visual Studio-Projekt in **Projektmappen-Explorer**.

Um einen Regelsatz zu den aktiven Regelsatz für die Analyse zu machen, mit der Maustaste, auf das Projekt im **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**. Wählen Sie in den Eigenschaftenseiten des Projekts, das **Codeanalyse** Registerkarte. Klicken Sie unter **diesen Regelsatz ausführen**Option **Durchsuchen**, und wählen Sie dann den gewünschten Regelsatz, den Sie in das Projektverzeichnis kopiert. Jetzt sehen Sie nur Verletzungen von Namensregeln für solche Regeln, die im ausgewählten Regelsatz aktiviert sind.

Sie können auch [Anpassen eines vordefinierten Regelsatzes](how-to-create-a-custom-rule-set.md#create-a-custom-rule-set) nach Bedarf. Sie können z. B. den Schweregrad der eine oder mehrere Regeln ändern, sodass Verletzungen als Fehler oder Warnungen angezeigt werden. die **Fehlerliste**.

## <a name="available-rule-sets"></a>Verfügbare Regelsätze

Der vordefinierte Analyse Regel umfassen drei Regelsätze, die alle Regeln im Paket betreffen&mdash;eine, die alle ermöglicht, eine, die alle deaktiviert, und eine, die Standardeinstellungen Schweregrad und die Aktivierung für jede Regel berücksichtigt:

- AllRulesEnabled.ruleset
- AllRulesDisabled.ruleset
- AllRulesDefault.ruleset

Darüber hinaus stehen zwei Regelsätze für die einzelnen Kategorien von Regeln, die im Paket, z. B. die Leistung oder Sicherheit. Ein Regelsatz aktiviert alle Regeln für die Kategorie aus, und ein Regelsatz berücksichtigt die Einstellungen der Schweregrad und die Aktivierung für jede Regel in der Kategorie.

Die [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) Analyzer NuGet-Paket enthält die Regelsätze für die folgenden Kategorien, die die Übereinstimmung der Regelsätze für ältere "FxCop" statische Codeanalyse verfügbar:

- Entwurf
- Dokumentation
- Verwaltbarkeit
- Benennen
- Leistung
- Zuverlässigkeit
- Sicherheit
- Verwendung

## <a name="see-also"></a>Siehe auch

- [Analyzer – häufig gestellte Fragen](analyzers-faq.md)
- [Overview of .NET Compiler Platform analyzers (Übersicht über .NET Compiler Platform-Analysetools)](roslyn-analyzers-overview.md)
- [Installieren von Analysen](install-roslyn-analyzers.md)
- [Verwenden von Analysen](use-roslyn-analyzers.md)
- [Verwenden von Regelsätzen zum Gruppe von Codeanalyseregeln](using-rule-sets-to-group-code-analysis-rules.md)