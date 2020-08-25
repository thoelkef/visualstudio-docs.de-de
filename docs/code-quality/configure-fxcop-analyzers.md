---
title: Konfigurieren von .NET-Code Qualitäts Analyzern mithilfe von Editor config
ms.date: 09/23/2019
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a131b7d69eec61f9b9106f7a4274b3882c51f0ff
ms.sourcegitcommit: a801ca3269274ce1de4f6b2c3f40b58bbaa3f460
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88800735"
---
# <a name="configure-net-code-quality-analyzers"></a>Konfigurieren von .NET-Code Qualitätsanalysen

Für bestimmte .NET-Code Qualitätsanalysen (solche, deren Regel-IDs beginnen mit `CA` ) können Sie die Teile Ihrer Codebasis, auf die Sie angewendet werden sollen, durch [konfigurierbare Optionen](fxcop-analyzer-options.md)verfeinern. Jede Option wird durch Hinzufügen eines Schlüssel-Wert-Paars zu einer [Editor config](https://editorconfig.org) -Datei angegeben. Eine Konfigurationsdatei kann für eine Datei, ein Projekt, eine Lösung oder das gesamte Repository spezifisch sein.

> [!TIP]
> Fügen Sie dem Projekt eine Editor config-Datei hinzu, indem Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Add**  >  **Neues Element**hinzufügen auswählen. Geben Sie im Fenster **Neues Element hinzufügen** im Suchfeld den Text **Editor config** ein. Wählen Sie die Vorlage **Editor config file (Standard)** aus, und wählen Sie **Hinzufügen**aus.
>
> ![Editor config-Datei dem Projekt in Visual Studio hinzufügen](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Informationen zum Konfigurieren des schwere Grads einer Regel (z. b. ob es sich um einen Fehler oder eine Warnung handelt) finden Sie unter [Festlegen des Regel schwere Grads in einer Editor config-Datei](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Oder Sie können eine der integrierten [Editor config-Dateien oder Regelsätze](analyzer-rule-sets.md) auswählen, um eine Kategorie von Regeln schnell zu aktivieren oder zu deaktivieren.

::: moniker-end

Im restlichen Teil dieses Artikels wird die allgemeine Syntax für die [Optionen erläutert,](fxcop-analyzer-options.md) die die Anwendung von .NET-Code Qualitätsanalysen verfeinern.

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

## <a name="enabling-editorconfig-based-configuration"></a>Aktivieren der Editor config-basierten Konfiguration

Die Editor config-basierte Analyse Konfiguration kann für die folgenden Bereiche aktiviert werden:

- Bestimmte Dokumente
- Bestimmte Ordner
- Bestimmte Projekt (e)
- Bestimmte Lösungen
- Gesamtes Repository

Um die Konfiguration zu aktivieren, fügen Sie eine *Editor config* -Datei mit den Optionen im entsprechenden Verzeichnis hinzu. Diese Datei kann auch Editor config-basierte Konfigurationseinträge des Diagnose schwere Grads enthalten. Ausführlichere Informationen finden Sie [hier](use-roslyn-analyzers.md#rule-severity).

## <a name="see-also"></a>Weitere Informationen

- [Optionen für den Regelbereich für .NET-Code Qualitätsanalysen](fxcop-analyzer-options.md)
- [Analysetoolkonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [.Net-Codierungs Konventionen für Editor config](../ide/editorconfig-code-style-settings-reference.md)
