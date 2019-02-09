---
title: 'CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden.'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f78ea4f44c48d2740df58def03a6335bce6637a2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942764"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden.

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechend – Wenn ausgelöst von Assemblys.<br /><br /> Nicht unterbrechend – Wenn ausgelöst von Typparametern.|

## <a name="cause"></a>Ursache

Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß-/Kleinschreibung.

## <a name="rule-description"></a>Regelbeschreibung

Der Name des Bezeichners ist in Wörter unterteilt, die auf die Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination von zwei Wörtern, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek aktiviert ist. Der Bezeichner erzeugt, wenn es erkannt wird, einen Verstoß gegen die Regel. Beispiele für zusammengesetzte Wörter, die dazu führen, einen Verstoß dass sind "CheckSum" und "MultiPart", die als "Checksum" und "Multipart", bzw. Groß-/Kleinschreibung beachtet werden sollten. Aufgrund von vorherigen gängige Nutzungsform werden einige Ausnahmen in der Regel erstellt, und es werden mehrere einzelne Wörter gekennzeichnet, z. B. "Toolbar" und "Filename", sollten werden Groß-/Kleinschreibung als zwei unterschiedliche Wörter (in diesem Fall "ToolBar" und "FileName").

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Ändern Sie den Namen, damit sie die richtige Groß-/Kleinschreibung ist.

## <a name="language"></a>Sprache

Die Rechtschreibprüfung überprüft, zurzeit nur für die Kultur auf Englisch basierenden Wörterbücher. Sie können die Kultur des Projekts in der Projektdatei ändern, durch das Hinzufügen der **CodeAnalysisCulture** Element.

Zum Beispiel:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Wenn Sie die Kultur auf etwas anderes als eine Kultur auf Englisch basierenden festlegen, ist diese Codeanalyse-Regelsätze im Hintergrund deaktiviert.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn beide Teile der zusammengesetzte Begriff von der Wörterbuch erkannt werden und die Absicht ist, verwenden Sie zwei Wörter.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1701: Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Siehe auch

- [Richtlinien für die Benennung](/dotnet/standard/design-guidelines/naming-guidelines)
- [Konventionen für die Groß-/Kleinschreibung](/dotnet/standard/design-guidelines/capitalization-conventions)