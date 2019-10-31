---
title: Konfigurationsoptionen für FxCop Analyzer
ms.date: 09/23/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 26435db42e3214bb19438226faba0db0e5ac0f4f
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73188832"
---
# <a name="rule-scope-options-for-fxcop-analyzers"></a>Optionen für den Regelbereich für FxCop-Analysen

Mit einigen FxCop-Analyse Regeln können Sie verfeinern, auf welche Teile Ihrer Codebasis Sie angewendet werden sollen. Auf dieser Seite werden die verfügbaren Optionen für die Bereichs Konfiguration, die zulässigen Werte und die Regeln aufgelistet, auf die Sie angewendet werden können. Wenn Sie diese Optionen verwenden möchten, geben Sie Sie in einer [Editor config-Datei](../ide/create-portable-custom-editor-options.md#add-an-editorconfig-file-to-a-project)an.

Diese Konfigurationsoptionen sind ab Version 2.6.3 des nuget-Pakets [Microsoft. Code Analysis. fxcopanalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) verfügbar.

> [!TIP]
> Die vollständige Liste der Optionen, die für eine bestimmte Version des Pakets "fxcopanalyzers" verfügbar sind, finden Sie in der *Analyse Configuration.MD* -Datei im *Dokumentations* Ordner für das Paket. Die Datei befindet sich unter *% User Profile%\\. nuget\packages\microsoft.CodeAnalysis.fxcopanalyzers\\\<Version\>\documentation\analyzer Configuration.MD*. Diese Konfigurations Dokumentations Datei ist in jeder Version des Pakets enthalten, beginnend mit Version 2.6.5. Im folgenden finden Sie ein Beispiel dafür, wie eine Option in der Datei *Analyzer Configuration.MD* dokumentiert wird:
>
> Options Name: `sufficient_IterationCount_for_weak_KDF_algorithm`\
> Optionswerte: ganzzahlige Werte \
> Standardwert: spezifisch für jede konfigurierbare Regel (standardmäßig "100000" für die meisten Regeln) \
> Ein Beispiel: `dotnet_code_quality.CA5387.sufficient_IterationCount_for_weak_KDF_algorithm = 100000`

## <a name="api_surface"></a>api_surface

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Der zu analysierende Teil der API-Oberfläche | `public`<br/>`internal` oder `friend`<br/>`private`<br/>`all`<br/><br/>Trennen Sie mehrere Werte durch ein Komma (,). | `public` | [CA1000](ca1000-do-not-declare-static-members-on-generic-types.md)<br/>[CA1003](ca1003-use-generic-event-handler-instances.md)<br/>[CA1008](ca1008-enums-should-have-zero-value.md)<br/>[CA1010](ca1010-collections-should-implement-generic-interface.md)<br/>[CA1012](ca1012-abstract-types-should-not-have-constructors.md)<br/>[CA1024](ca1024-use-properties-where-appropriate.md)<br/>[CA1027](ca1027-mark-enums-with-flagsattribute.md)<br/>[CA1028](ca1028-enum-storage-should-be-int32.md)<br/>[CA1030](ca1030-use-events-where-appropriate.md)<br/>[CA1036](ca1036-override-methods-on-comparable-types.md)<br/>[CA1040](ca1040-avoid-empty-interfaces.md)<br/>[CA1041](ca1041-provide-obsoleteattribute-message.md)<br/>[CA1043](ca1043-use-integral-or-string-argument-for-indexers.md)<br/>[CA1044](ca1044-properties-should-not-be-write-only.md)<br/>[CA1051](ca1051-do-not-declare-visible-instance-fields.md)<br/>[CA1052](ca1052-static-holder-types-should-be-sealed.md)<br/>[CA1054](ca1054-uri-parameters-should-not-be-strings.md)<br/>[CA1055](ca1055-uri-return-values-should-not-be-strings.md)<br/>[CA1056](ca1056-uri-properties-should-not-be-strings.md)<br/>[CA1058](ca1058-types-should-not-extend-certain-base-types.md)<br/>[CA1063](ca1063-implement-idisposable-correctly.md)<br/>[CA1708](ca1708-identifiers-should-differ-by-more-than-case.md)<br/>[CA1710](ca1710-identifiers-should-have-correct-suffix.md)<br/>[CA1711](ca1711-identifiers-should-not-have-incorrect-suffix.md)<br/>[CA1714](ca1714-flags-enums-should-have-plural-names.md)<br/>[CA1715](ca1715-identifiers-should-have-correct-prefix.md)<br/>[CA1716](ca1716-identifiers-should-not-match-keywords.md)<br/>[CA1717](ca1717-only-flagsattribute-enums-should-have-plural-names.md)<br/>[CA1720](ca1720-identifiers-should-not-contain-type-names.md)<br/>[CA1721](ca1721-property-names-should-not-match-get-methods.md)<br/>[CA1725](ca1725-parameter-names-should-match-base-declaration.md)<br/>[CA1802](ca1802.md)<br/>[CA1815](ca1815.md)<br/>[CA1819](ca1819.md)<br/>[CA2217](ca2217.md)<br/>[CA2225](ca2225.md)<br/>[CA2226](ca2226.md)<br/>[CA2231](ca2231.md)<br/>[CA2234](ca2234.md) |

## <a name="exclude_async_void_methods"></a>exclude_async_void_methods

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Gibt an, ob asynchrone Methoden ignoriert werden sollen, die keinen Wert zurückgeben. | `true`<br/>`false` | `false` | [CA2007](ca2007.md) |

> [!NOTE]
> In Version 2.6.3 und früher des Analyzer-Pakets wurde diese Option `skip_async_void_methods`benannt.

## <a name="exclude_single_letter_type_parameters"></a>exclude_single_letter_type_parameters

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Ob [Typparameter](/dotnet/csharp/programming-guide/generics/generic-type-parameters) mit einem Zeichen aus der Regel ausgeschlossen werden sollen, z. b. `S` in `Collection<S>` | `true`<br/>`false` | `false` | [CA1715](ca1715-identifiers-should-have-correct-prefix.md) |

> [!NOTE]
> In Version 2.6.3 und früher des Analyzer-Pakets wurde diese Option `allow_single_letter_type_parameters`benannt.

## <a name="output_kind"></a>output_kind

| Beschreibung | Zulässige Werte | Standardwert | Konfigurierbare Regeln |
| - | - | - | - |
| Gibt an, dass Code in einem Projekt analysiert werden soll, das diesen Assemblytyp generiert. | Ein oder mehrere Felder der <xref:Microsoft.CodeAnalysis.OutputKind>-Enumeration<br/><br/>Trennen Sie mehrere Werte durch ein Komma (,). | Alle Ausgabearten | [CA2007](ca2007.md) |
