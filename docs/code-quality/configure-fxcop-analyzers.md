---
title: Konfigurieren von FxCop-Analyzern mithilfe von Editor config
ms.date: 03/11/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 68c175a55c9e60e870a5466a831aaae50d62dced
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293446"
---
# <a name="configure-fxcop-analyzers"></a>Konfigurieren von FxCop-Analyzern

Die [FxCop-Analysen](install-fxcop-analyzers.md) bestehen aus den wichtigsten "FxCop"-Regeln aus der Legacy Analyse, die in .NET Compiler Platform-basierten Code Analysen konvertiert wurden. Sie können FxCop-Code Analysen auf zwei Arten konfigurieren:

- Mit einem [Regelsatz](#fxcop-analyzer-rule-sets), mit dem Sie Regel aktivieren oder deaktivieren und den Schweregrad einzelner Regelverstöße festlegen können.

- Ab Version 2.6.3 des [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) -nuget-Pakets über eine [Editor config-Datei](#editorconfig-file). Mit den [konfigurierbaren Optionen](fxcop-analyzer-options.md) können Sie verfeinern, welche Teile Ihrer Codebasis analysiert werden.

> [!TIP]
> Informationen zu den Unterschieden zwischen Legacy-und FxCop-Analyzern finden Sie unter Häufig gestellte Fragen zur [FxCop](fxcop-analyzers-faq.md)-Analyse.

## <a name="fxcop-analyzer-rule-sets"></a>FxCop-Analyse Regelsätze

Eine Möglichkeit zum Konfigurieren von FxCop-Analyzern ist die Verwendung eines XML- *Regelsatzes*. Bei einem Regelsatz handelt es sich um eine Gruppierung von Code Analyse Regeln, mit denen gezielte Probleme und bestimmte Bedingungen identifiziert werden. Regelsätze ermöglichen das Aktivieren oder Deaktivieren von Regeln und Festlegen des schwere Grads einzelner Regel Verletzungen.

Das nuget-Paket FxCop Analyzer enthält vordefinierte Regelsätze für die folgenden Regel Kategorien:

- Entwurf
- Dokumentation
- Verwaltbarkeit
- Benennen
- Leistung
- Zuverlässigkeit
- Sicherheit
- Verwendung

Weitere Informationen finden Sie unter [Regelsätze für Code Analysen](analyzer-rule-sets.md).

## <a name="editorconfig-file"></a>Editor config-Datei

Sie können FxCop-Analyse Regeln konfigurieren, indem Sie einer [Editor config](https://editorconfig.org) -Datei Schlüssel-Wert-Paare hinzufügen. Eine Konfigurationsdatei kann [für ein projektspezifisch](#per-project-configuration) sein oder von zwei oder mehr Projekten [gemeinsam genutzt](#shared-configuration) werden.

> [!NOTE]
> Es ist nicht möglich, ältere FxCop-Regeln mithilfe einer Editor config-Datei zu konfigurieren.

### <a name="per-project-configuration"></a>Konfiguration pro Projekt

Fügen Sie dem Stammverzeichnis des Projekts eine *Editor config* -Datei hinzu, um die Editor config-basierte Analyse Konfiguration für ein bestimmtes Projekt zu aktivieren.

> [!TIP]
> Sie können dem Projekt eine Editor config-Datei hinzufügen, indem Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und**Neues Element** **Hinzufügen** > auswählen. Geben Sie im Fenster **Neues Element hinzufügen** im Suchfeld den Text **Editor config** ein. Wählen Sie die Vorlage **Editor config file (Standard)** aus, und wählen Sie **Hinzufügen**aus.
>
> ![Editor config-Element dem Projekt in Visual Studio hinzufügen](media/add-editorconfig-file.png)

Zurzeit gibt es keine hierarchische Unterstützung für das Kombinieren von Editor config-Dateien, die auf unterschiedlichen Verzeichnis Ebenen vorhanden sind, z. b. die Projekt Mappe und die Projektebene.

### <a name="shared-configuration"></a>Freigegebene Konfiguration

Sie können eine Editor config-Datei für die Konfiguration von FxCop Analyzer zwischen zwei oder mehr Projekten freigeben, es sind jedoch einige zusätzliche Schritte erforderlich.

1. Speichern Sie die *Editor config* -Datei an einem gemeinsamen Speicherort.

2. Erstellen Sie eine *.* -Eigenschaften Datei mit folgendem Inhalt:

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

3. Fügen Sie der *csproj* -oder *vbproj* -Datei eine Zeile hinzu, um die im vorherigen Schritt erstellte *.* -Datei zu importieren. Diese Zeile muss vor allen Zeilen platziert werden, in denen die FxCop Analyzer *.* -Eigenschaften Dateien importiert werden. Beispiel: die Datei ".-Eigenschaften" hat den Namen " *Editor config.* -Eigenschaften":

   ```xml
   ...
   <Import Project="..\..\editorconfig.props" Condition="Exists('..\..\editorconfig.props')" />
   <Import Project="..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props" Condition="Exists('..\packages\Microsoft.CodeAnalysis.FxCopAnalyzers.2.6.3\build\Microsoft.CodeAnalysis.FxCopAnalyzers.props')" />
   ...
   ```

4. Laden Sie das Projekt neu.

> [!NOTE]
> Der beliebige freigegebene Speicherort der hier beschriebenen Editor config-Datei gilt nur für die Konfiguration von FxCop-Analyzers. Bei anderen Einstellungen, wie einzügkeit und Codestil, muss die editorconfig-Datei immer im Projektordner oder in einem übergeordneten Ordner abgelegt werden.

## <a name="option-scopes"></a>Options Bereiche

Jede Option kann für alle Regeln, für eine Kategorie von Regeln (z. b. Benennung oder Entwurf) oder für eine bestimmte Regel konfiguriert werden.

### <a name="all-rules"></a>Alle Regeln

Die Syntax zum Konfigurieren einer Option für alle Regeln lautet wie folgt:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kategorie von Regeln

Die Syntax zum Konfigurieren einer Option für eine *Kategorie* von Regeln (z. b. Benennung, Entwurf oder Leistung) lautet wie folgt:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality. Rulecategory. optionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Bestimmte Regel

Die Syntax zum Konfigurieren einer Option für eine bestimmte Regel lautet wie folgt:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality. RuleId. optionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="see-also"></a>Siehe auch

- [Analyse Konfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop-Analysen](install-fxcop-analyzers.md)
- [.Net-Codierungs Konventionen für Editor config](../ide/editorconfig-code-style-settings-reference.md)
