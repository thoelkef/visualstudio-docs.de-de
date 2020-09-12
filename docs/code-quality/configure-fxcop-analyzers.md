---
title: Konfigurieren von .NET-Code Qualitätsanalysen mithilfe von Editor config
ms.date: 09/01/2020
ms.topic: conceptual
helpviewer_keywords:
- .NET analyzers
- FxCop analyzers, configuring
- code quality
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc237082ec1188d71241facead975db1df2cf3af
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035429"
---
# <a name="configure-net-code-quality-analysis-with-editorconfig"></a>Konfigurieren der .NET-Code Qualitätsanalyse mit Editor config

Jeder Code Quality Analyzer (der, dessen Regel-IDs beginnen mit `CA` ), kann so verfeinert werden, dass er auf die Teile Ihrer Codebasis durch konfigurierbare Optionen angewendet wird. Jede Option wird durch Hinzufügen eines Schlüssel-Wert-Paars zu einer [Editor config](https://editorconfig.org) -Datei angegeben. Eine Konfigurationsdatei kann für eine Datei, ein Projekt, eine Lösung oder das gesamte Repository spezifisch sein.

> [!TIP]
> Fügen Sie dem Projekt eine Editor config-Datei hinzu, indem Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Add**  >  **Neues Element**hinzufügen auswählen. Geben Sie im Fenster **Neues Element hinzufügen** im Suchfeld den Text **Editor config** ein. Wählen Sie die Vorlage **Editor config file (Standard)** aus, und wählen Sie **Hinzufügen**aus.
>
> ![Editor config-Datei dem Projekt in Visual Studio hinzufügen](media/add-editorconfig-file.png)

::: moniker range=">=vs-2019"

Informationen zum Konfigurieren des schwere Grads einer Regel (z. b. ob es sich um einen Fehler oder eine Warnung handelt) finden Sie unter [Festlegen des Regel schwere Grads in einer Editor config-Datei](use-roslyn-analyzers.md#set-rule-severity-in-an-editorconfig-file). Oder Sie können eine der integrierten [Editor config-Dateien oder Regelsätze](analyzer-rule-sets.md) auswählen, um eine Kategorie von Regeln schnell zu aktivieren oder zu deaktivieren.

::: moniker-end

Im restlichen Teil dieses Artikels wird die allgemeine Syntax für die Optionen erläutert, die die Anwendung von .NET-Code Qualitätsanalysen verfeinern.

## <a name="option-scopes"></a>Options Bereiche

Jede Option zum verfeinern kann für alle Regeln, für eine Kategorie von Regeln (z. b. Sicherheit oder Entwurf) oder für eine bestimmte Regel konfiguriert werden.

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

Um die Konfiguration zu aktivieren, fügen Sie eine *Editor config* -Datei mit den Optionen im entsprechenden Verzeichnis hinzu. Diese Datei kann auch Editor config-basierte Konfigurationseinträge des Diagnose schwere Grads enthalten. Ausführlichere Informationen finden Sie [hier](use-roslyn-analyzers.md#configure-severity-levels).

## <a name="enable-a-category-of-rules"></a>Aktivieren der Regelkategorie

Analysepakete können vordefinierte [Editor config](use-roslyn-analyzers.md#configure-severity-levels) -und/oder [Regel Satz](using-rule-sets-to-group-code-analysis-rules.md) Dateien enthalten, die es Ihnen ermöglichen, eine Kategorie von Regeln, wie z. b. Sicherheits-oder Entwurfs Regeln, schnell und einfach zu aktivieren. Das nuget Analyzer-Paket [Microsoft. Code Analysis. netanalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) enthält sowohl Editor config-Dateien als auch Regelsätze. Indem Sie eine bestimmte Kategorie von Regeln aktivieren, können Sie gezielte Probleme und bestimmte Bedingungen ermitteln.

> [!NOTE]
> Das Aktivieren von Analyse Regeln und das Festlegen Ihres schwere Grads mithilfe einer Editor config-Datei wird ab Visual Studio 2019 Version 16,3 unterstützt.

Das "netanalyzers"-nuget-Paket enthält vordefinierte Editor config-Dateien und Regelsätze für die folgenden Regel Kategorien:

- Alle Regeln
- Datenfluss
- Entwurf
- Dokumentation
- Globalisierung
- Interoperabilität
- Wartbarkeit
- Benennung
- Leistung
- Portiert von FxCop
- Zuverlässigkeit
- Sicherheit
- Verwendung

Jede dieser Kategorien von Regeln verfügt über eine Editor config-oder Regel Satz Datei für Folgendes:

- Alle Regeln in der Kategorie aktivieren (und alle anderen Regeln deaktivieren)
- Standard Schweregrad der Regel verwenden und standardmäßig aktiviert (und alle anderen Regeln deaktivieren)

> [!TIP]
> Die Kategorie "alle Regeln" verfügt über eine zusätzliche Editor config-oder Regel Satz Datei, um alle Regeln zu deaktivieren. Verwenden Sie diese Datei, um alle Analyse Warnungen oder-Fehler in einem Projekt schnell zu entfernen.

> [!TIP]
> Wenn Sie von der veralteten "FxCop"-Analyse zur .NET Compiler Platform basierten Code Analyse migrieren, können Sie mit den Editor config-und Regel Satz Dateien ähnliche Regel Konfigurationen verwenden, die [Sie zuvor verwendet](rule-set-reference.md)haben.

## <a name="predefined-editorconfig-files"></a>Vordefinierte Editor config-Dateien

Die vordefinierten Editor config-Dateien für das Microsoft. Code Analysis. netanalyzers Analyzer-Paket befinden sich im Verzeichnis " *% User Profile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editor config* ". Beispielsweise befindet sich die Datei "Editor config", um alle Sicherheitsregeln zu aktivieren, unter *% User Profile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \editoriconfig\securityrulesenabled \\ . Editor config*.

Kopieren Sie die ausgewählte Editor config-Datei in das Stammverzeichnis Ihres Projekts.

## <a name="predefined-rule-sets"></a>Vordefinierter Regelsatz

Die vordefinierten Regel Satz Dateien für das Microsoft. Code Analysis. netanalyzers Analyzer-Paket befinden sich im Verzeichnis *% User Profile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \rulesets* . Beispielsweise befindet sich die Regel Satz Datei, um alle Sicherheitsregeln zu aktivieren, unter *% User Profile% \\ . nuget\packages\microsoft.CodeAnalysis.netanalyzers \\ \<version\> \ruleset\securityrulesenabled.RuleSet*.

Kopieren Sie mindestens einen Regelsatz, und fügen Sie ihn in das Verzeichnis ein, das das Visual Studio-Projekt enthält, oder direkt in **Projektmappen-Explorer**.

Sie können auch [einen vordefinierten Regelsatz anpassen](how-to-create-a-custom-rule-set.md) . Beispielsweise können Sie den Schweregrad einer oder mehrerer Regeln ändern, sodass Verstöße im **Fehlerliste**als Fehler oder Warnungen angezeigt werden.


## <a name="rule-scope-options-for-net-code-quality-analyzers"></a>Optionen für den Regelbereich für .NET-Code Qualitätsanalysen

Sie können Optionen in einer [Editor config-Datei](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)angeben. Sie können z. b. die folgenden Optionen angeben.

> [!TIP]
> Die vollständige Liste der verfügbaren Optionen finden Sie in der [Configuration.MD-Analyse Datei](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md). Im folgenden finden Sie ein Beispiel dafür, wie eine Option in der Datei *Analyzer Configuration.MD* dokumentiert wird:
>
> Options Name: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Optionswerte: ganzzahlige Werte \
> Standardwert: spezifisch für jede konfigurierbare Regel (standardmäßig "100000" für die meisten Regeln) \
> Beispiel: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Der zu analysierende Teil der API-Oberfläche | `public`<br/>`internal` oder `friend`<br/>`private`<br/>`all`<br/><br/>Trennen Sie mehrere Werte durch ein Komma (,). | `public` | [CA1000](ca1000.md) [CA1003](ca1003.md) [CA1008](ca1008.md) [CA1010](ca1010.md)<br/>[CA1012](ca1012.md) [CA1024](ca1024.md) [CA1027](ca1027.md) [CA1028](ca1028.md)<br/>[CA1030](ca1030.md) [CA1036](ca1036.md) [CA1040](ca1040.md) [CA1041](ca1041.md)<br/>[CA1043](ca1043.md) [CA1044](ca1044.md) [CA1051](ca1051.md) [CA1052](ca1052.md)<br/>[CA1054](ca1054.md) [CA1055](ca1055.md) [CA1056](ca1056.md) [CA1058](ca1058.md)<br/>[CA1063](ca1063.md) [CA1708](ca1708.md) [CA1710](ca1710.md) [CA1711](ca1711.md)<br/>[CA1714](ca1714.md) [CA1715](ca1715.md) [CA1716](ca1716.md) [CA1717](ca1717.md)<br/>[CA1720](ca1720.md) [CA1721](ca1721.md) [CA1725](ca1725.md) [CA1801](ca1801.md)<br/>[CA1802](ca1802.md) [CA1815](ca1815.md) [CA1819](ca1819.md) [CA2217](ca2217.md)<br/>[CA2225](ca2225.md) [CA2226](ca2226.md) [CA2231](ca2231.md) [CA2234](ca2234.md)<br/>|

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Gibt an, ob asynchrone Methoden ignoriert werden sollen, die keinen Wert zurückgeben. | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> In Version 2.6.3 und früher des Analyzer-Pakets hieß diese Option `skip_async_void_methods` .

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Ob [Typparameter](/dotnet/csharp/programming-guide/generics/generic-type-parameters) mit einem Zeichen aus der Regel ausgeschlossen werden sollen, z. b. `S` in `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715.md) |

> [!NOTE]
> In Version 2.6.3 und früher des Analyzer-Pakets hieß diese Option `allow_single_letter_type_parameters` .

## <a name="output_kind"></a>output_kind

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Gibt an, dass Code in einem Projekt analysiert werden soll, das diesen Assemblytyp generiert. | Ein oder mehrere Felder der- <xref:Microsoft.CodeAnalysis.OutputKind> Enumeration.<br/><br/>Trennen Sie mehrere Werte durch ein Komma (,). | Alle Ausgabearten | [CA2007](ca2007.md) |

## <a name="required_modifiers"></a>required_modifiers

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Gibt die erforderlichen modifiziererer für APIs an, die analysiert werden sollen. | Mindestens ein Wert aus der unten angegebenen Tabelle mit den Modifiziererwerten<br/><br/>Trennen Sie mehrere Werte durch ein Komma (,). | Hängt von jeder Regel ab | [CA1802](ca1802.md) |

| Zulässiger Modifizierer | Zusammenfassung |
| --- | --- |
| `none` | Keine modifiziereranforderung |
| `static` oder `Shared` | Muss in Visual Basic als "static" ("Shared") deklariert werden. |
| `const` | Muss als "Konstanten" deklariert werden. |
| `readonly` | Muss als ' schreibgeschützt ' deklariert werden |
| `abstract` | Muss als "abstract" deklariert werden |
| `virtual` | Muss als "Virtual" deklariert werden |
| `override` | Muss als ' override ' deklariert werden |
| `sealed` | Muss als ' sealed ' deklariert werden |
| `extern` | Muss als "extern" deklariert werden |
| `async` | Muss als "Async" deklariert werden. |

## <a name="exclude_extension_method_this_parameter"></a>exclude_extension_method_this_parameter

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Ob die Analyse für den `this` Parameter der Erweiterungs Methoden übersprungen werden soll. | `true`<br/>`false` | `false` | [CA1062](ca1062.md) |

## <a name="null_check_validation_methods"></a>null_check_validation_methods

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen der Überprüfungsmethoden zur Validierung von Null-Überprüfungen, die die an die Methode übergebenen Argumente überprüfen | Zulässige Methodennamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Methodenname (schließt alle Methoden mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols mit einem optionalen `M:` Präfix | Keine | [CA1062](ca1062.md) |

## <a name="additional_string_formatting_methods"></a>additional_string_formatting_methods

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen von zusätzlichen Zeichen folgen-Formatierungs Methoden | Zulässige Methodennamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Methodenname (schließt alle Methoden mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols mit einem optionalen `M:` Präfix | Keine | [CA2241](ca2241.md) |

## <a name="excluded_type_names_with_derived_types"></a>excluded_type_names_with_derived_types

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen von Typen, sodass der Typ und alle abgeleiteten Typen für die Analyse ausgeschlossen sind | Zulässige Symbolnamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Typname (schließt alle Typen mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols mit einem optionalen `T:` Präfix | Keine | [CA1303](ca1303.md) |

## <a name="excluded_symbol_names"></a>excluded_symbol_names

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen von Symbolen, die für die Analyse ausgeschlossen sind | Zulässige Symbolnamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Symbol Name (schließt alle Symbole mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols. Jeder Symbol Name erfordert ein Symbolart-Präfix, z. b. "M:"-Präfix für Methoden, "T:"-Präfix für Typen, "N:"-Präfix für Namespaces usw.<br/> - `.ctor` für Konstruktoren und `.cctor` für statische Konstruktoren | Keine | [CA1062](ca1062.md) [CA1303](ca1303.md) [CA2000](ca2000.md) [CA2100](ca2100.md) [CA2301](ca2301.md) [CA2302](ca2302.md)<br/>[CA2311](ca2311.md) [CA2312](ca2312.md) [CA2321](ca2321.md) [CA2322](ca2322.md) [CA2327](ca2327.md) [CA2328](ca2328.md)<br/>[CA2329](ca2329.md) [CA2330](ca2330.md) [CA3001](ca3001.md) [CA3002](ca3002.md) [CA3003](ca3003.md) [CA3004](ca3004.md)<br/>[CA3005](ca3005.md) [CA3006](ca3006.md) [CA3007](ca3007.md) [CA3008](ca3008.md) [CA3009](ca3009.md) [CA3010](ca3010.md)<br/>[CA3011](ca3011.md) [CA3012](ca3012.md) [CA5361](ca5361.md) CA5376 CA5377 [CA5378](ca5378.md)<br/>[CA5380](ca5380.md) [CA5381](ca5381.md) CA5382 CA5383 CA5384 CA5387<br/>CA5388 [CA5389](ca5389.md) CA5390 |

## <a name="disallowed_symbol_names"></a>disallowed_symbol_names

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Namen von Symbolen, die im Kontext der Analyse nicht zulässig sind | Zulässige Symbolnamen Formate (durch Trennzeichen getrennt `|` ):<br/> -Nur Symbol Name (schließt alle Symbole mit dem Namen ein, unabhängig vom enthaltenden Typ oder Namespace)<br/> -Voll qualifizierte Namen im [Dokumentations-ID-Format](https://github.com/dotnet/csharplang/blob/master/spec/documentation-comments.md#id-string-format)des Symbols. Jeder Symbol Name erfordert ein Symbolart-Präfix, z. b. "M:"-Präfix für Methoden, "T:"-Präfix für Typen, "N:"-Präfix für Namespaces usw.<br/> - `.ctor` für Konstruktoren und `.cctor` für statische Konstruktoren | Keine | [CA1031](ca1031.md) |

## <a name="see-also"></a>Weitere Informationen

- [Analysetoolkonfiguration](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [.Net-Codierungs Konventionen für Editor config](../ide/editorconfig-code-style-settings-reference.md)
