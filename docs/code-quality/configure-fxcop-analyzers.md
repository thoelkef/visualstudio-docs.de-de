---
title: Konfigurieren Sie FxCop-Analysen, die mit "editorconfig"
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ac751b7ec130b6bfbb18752c02b491b6c342f172
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57874699"
---
# <a name="configure-fxcop-analyzers"></a>Konfigurieren Sie FxCop-Analysen

Die [FxCop-Analysetools](install-fxcop-analyzers.md) bestehen aus den Regeln für die wichtigsten "FxCop" aus der Analyse von statischem Code, in der Roslyn-Analysetools konvertiert. Sie können die FxCop-Code-Analyzer auf zwei Arten konfigurieren:

- Mit einem [Regelsatz](#fxcop-analyzer-rule-sets), wodurch aktivieren oder deaktivieren die Regel aus, und legen Sie den Schweregrad für die einzelnen Verletzungen.

- Ab Version 2.6.3, der die [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) NuGet-Paket, über eine [editorconfig-Datei](#editorconfig-file). Die [konfigurierbaren Optionen](fxcop-analyzer-options.md) können Sie, welche Teile Optimieren Ihrer Codebasis, um zu analysieren.

> [!TIP]
> Informationen zu den Unterschieden zwischen statischen FxCop-Codeanalyse und FxCop-Analysen, finden Sie unter [FxCop-Analyzer – häufig gestellte Fragen](fxcop-analyzers-faq.md).

## <a name="fxcop-analyzer-rule-sets"></a>FxCop-Analyse-Regelsätze

Eine Möglichkeit zum Konfigurieren von FxCop-Analysen wird mithilfe eines XML- *Regelsatz*. Ein Regelsatz ist eine Gruppierung von Codeanalyseregeln, die gezielte Probleme und bestimmte Bedingungen identifizieren. Regelsätze können Sie die aktivieren oder deaktivieren die Regel aus, und legen Sie den Schweregrad für die einzelnen Verletzungen.

Das NuGet-Paket von FxCop-Analyzer enthält vordefinierte Regel für den folgenden Regelkategorien:

- Entwurf
- Dokumentation
- Verwaltbarkeit
- Benennen
- Leistung
- Zuverlässigkeit
- Sicherheit
- Verwendung

Weitere Informationen finden Sie unter [von Regelsätzen für Roslyn-Analysetools](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>EditorConfig-Datei

Sie können die Analyzer-Regeln konfigurieren, durch das Hinzufügen von Schlüssel-Wert-Paare, ein [editorconfig](https://editorconfig.org) Datei. Eine Konfigurationsdatei möglich [für ein Projekt spezifisch](#per-project-configuration) oder [freigegebenen](#shared-configuration) zwischen mindestens zwei Projekte.

### <a name="per-project-configuration"></a>Pro-Projektkonfiguration

Um editorconfig-basierte analysekonfiguration für ein bestimmtes Projekt zu aktivieren, fügen eine *editorconfig* Datei zum Stammverzeichnis des Projekts.

> [!TIP]
> Sie können eine editorconfig-Datei zu Ihrem Projekt hinzufügen, indem Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer** und **hinzufügen** > **neues Element**. In der **neues Element hinzufügen** Fenster eingeben **"editorconfig"** in das Suchfeld. Wählen Sie die **Editorconfig-Datei (Standard)** Vorlage, und wählen Sie **hinzufügen**.
>
> ![Editorconfig-Element zum Projekt in Visual Studio hinzufügen](media/add-editorconfig-file.png)

Derzeit besteht keine hierarchische Unterstützung für "kombiniert" editorconfig-Dateien vorhanden sind auf anderen Verzeichnis, beispielsweise die Projektmappen- und Projektdateien-Ebene.

### <a name="shared-configuration"></a>Freigegebene Konfiguration

Sie können eine editorconfig-Datei für die Konfiguration des Analysemoduls zwischen zwei oder mehr Projekten freigeben, aber es ist einige zusätzliche Schritte erforderlich.

1. Speichern Sie die *editorconfig* in einen allgemeinen Speicherort.

2. Erstellen Sie eine *props* -Datei mit dem folgenden Inhalt:

   ```xml
   <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <SkipDefaultEditorConfigAsAdditionalFile>true</SkipDefaultEditorConfigAsAdditionalFile>
     </PropertyGroup>
     <ItemGroup Condition="Exists('<your path>\.editorconfig')" >
       <AdditionalFiles Include="<your path>\.editorconfig" />
     </ItemGroup>
   </Project>
   ```

3. Fügen Sie eine Zeile in Ihrer *csproj* oder *vbproj* zu importierende Datei die *props* Datei, die Sie im vorherigen Schritt erstellt haben. Diese Zeile muss platziert werden, vor dem alle Zeilen mit dem Importieren den FxCop-Analyzer *props* Dateien. Wenn Ihre .props-Datei heißt beispielsweise *editorconfig.props*:

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Laden Sie das Projekt ein.

> [!NOTE]
> Sie können keine vorheriger FxCop-Regeln (statische Codeanalyse FxCop) konfigurieren, mithilfe einer editorconfig-Datei.

## <a name="option-scopes"></a>Option-Bereiche

Jede Option kann für alle Regeln, für eine Kategorie von Regeln (z. B. "Naming" oder "Entwurf") oder für eine bestimmte Regel konfiguriert werden.

### <a name="all-rules"></a>Alle Regeln

Die Syntax für das Konfigurieren einer Option für alle Regeln lautet wie folgt aus:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality.OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kategorie von Regeln

Die Syntax zum Konfigurieren einer Option für eine *Kategorie* von Regeln (z. B. benennen, Entwurf und Leistung) lautet wie folgt:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality.RuleCategory.OptionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Entsprechende Regel

Die Syntax für das Konfigurieren einer Option für eine bestimmte Regel lautet wie folgt aus:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality.RuleId.OptionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Siehe auch

- [Analysekonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop-Analysen](install-fxcop-analyzers.md)
