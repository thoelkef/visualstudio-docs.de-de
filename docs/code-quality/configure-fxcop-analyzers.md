---
title: Konfigurieren von FxCop-Analyzern mithilfe von Editor config
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- FxCop analyzers, configuring
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7619b040343720198e190f551741f565e62fa145
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186399"
---
# <a name="configure-fxcop-analyzers"></a>Konfigurieren von FxCop-Analyzern

Das [Paket FxCop](install-fxcop-analyzers.md) Analyzer besteht aus den wichtigsten "FxCop"-Regeln aus der Legacy-Analyse, die in .NET Compiler Platform-basierte Code Analysen konvertiert wurden. Bei bestimmten FxCop-Regeln können Sie durch [konfigurierbare Optionen](fxcop-analyzer-options.md)verfeinern, auf welche Teile Ihrer Codebasis Sie angewendet werden sollen. Jede Option wird durch Hinzufügen eines Schlüssel-Wert-Paars zu einer [Editor config](https://editorconfig.org) -Datei angegeben. Eine Konfigurationsdatei kann [für ein projektspezifisch](#per-project-configuration) sein oder von zwei oder mehr Projekten [gemeinsam genutzt](#shared-configuration) werden.

> [!TIP]
> Sie können dem Projekt eine Editor config-Datei hinzufügen, indem Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und**Neues Element** **Hinzufügen** > auswählen. Geben Sie im Fenster **Neues Element hinzufügen** im Suchfeld den Text **Editor config** ein. Wählen Sie die Vorlage **Editor config file (Standard)** aus, und wählen Sie **Hinzufügen**aus.
>
> ![Editor config-Datei dem Projekt in Visual Studio hinzufügen](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Informationen zum Konfigurieren des schwere Grads einer Regel (z. b. ob es sich um einen Fehler oder eine Warnung handelt) finden Sie unter [Festlegen des Regel schwere Grads in einer Editor config-Datei](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Sie können auch einen der integrierten [Regelsätze](analyzer-rule-sets.md) auswählen, um eine Kategorie von Regeln schnell zu aktivieren oder zu deaktivieren.

::: moniker-end

Im restlichen Teil dieses Artikels wird die allgemeine Syntax der [Optionen erläutert,](fxcop-analyzer-options.md) die die Anwendung von FxCop-Regeln verfeinern.

> [!NOTE]
> Es ist nicht möglich, ältere FxCop-Regeln mithilfe einer Editor config-Datei zu konfigurieren. Informationen zu den Unterschieden zwischen Legacy-und FxCop-Analyzern finden Sie unter Häufig gestellte Fragen zur [FxCop](fxcop-analyzers-faq.md)-Analyse.

## <a name="option-scopes"></a>Options Bereiche

Jede Option zum verfeinern kann für alle Regeln, für eine Kategorie von Regeln (z. b. Benennung oder Entwurf) oder für eine bestimmte Regel konfiguriert werden.

### <a name="all-rules"></a>Alle Regeln

Die Syntax zum Konfigurieren einer Option für *alle* Regeln lautet wie folgt:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality. OptionName = OptionValue | `dotnet_code_quality.api_surface = public` |

### <a name="category-of-rules"></a>Kategorie von Regeln

Die Syntax zum Konfigurieren einer Option für eine *Kategorie* von Regeln (z. b. Benennung, Entwurf oder Leistung) lautet wie folgt:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality. Rulecategory. optionName = OptionValue | `dotnet_code_quality.Naming.api_surface = public` |

### <a name="specific-rule"></a>Bestimmte Regel

Die Syntax zum Konfigurieren einer Option für eine *bestimmte* Regel lautet wie folgt:

|Syntax|Beispiel|
|-|-|
| dotnet_code_quality. RuleId. optionName = OptionValue | `dotnet_code_quality.CA1040.api_surface = public` |

## <a name="per-project-configuration"></a>Konfiguration pro Projekt

Fügen Sie dem Stammverzeichnis des Projekts eine *Editor config* -Datei hinzu, um die Editor config-basierte Analyse Konfiguration für ein bestimmtes Projekt zu aktivieren.

Zurzeit gibt es keine hierarchische Unterstützung für das Kombinieren von Editor config-Dateien, die auf unterschiedlichen Verzeichnis Ebenen vorhanden sind, z. b. die Projekt Mappe und die Projektebene.

## <a name="shared-configuration"></a>Freigegebene Konfiguration

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
> Der beliebige freigegebene Speicherort der hier beschriebenen Editor config-Datei gilt nur für die Konfiguration des Bereichs bestimmter FxCop-Analyse Regeln. Bei anderen Einstellungen, wie z. b. Schweregrad der Regel, allgemeinen Editor-Einstellungen und Codestil, muss die editorconfig-Datei immer im Projektordner oder in einem übergeordneten Ordner abgelegt werden.

## <a name="see-also"></a>Siehe auch

- [Optionen für den Regelbereich für FxCop-Analysen](fxcop-analyzer-options.md)
- [Analyse Konfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [FxCop-Analysen](install-fxcop-analyzers.md)
- [.Net-Codierungs Konventionen für Editor config](../ide/editorconfig-code-style-settings-reference.md)
