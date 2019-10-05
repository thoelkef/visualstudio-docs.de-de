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
ms.openlocfilehash: 5480d3dde926dfe31b018a5cd0b1ea6a5813063b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234339"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden.

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechen: Wenn Assemblys ausgelöst werden.<br /><br /> Nicht unterbrechend: Wenn für Typparameter ausgelöst wird.|

## <a name="cause"></a>Ursache

Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß-/Kleinschreibung.

## <a name="rule-description"></a>Regelbeschreibung

Der Name des Bezeichners wird in Wörter aufgeteilt, die auf der Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination aus zwei Wörtern wird von der Bibliothek der Microsoft-Rechtschreibprüfung überprüft. Wenn es erkannt wird, führt der Bezeichner zu einem Verstoß gegen die Regel. Beispiele für zusammengesetzte Wörter, die zu einer Verletzung führen, sind "Checksum" und "multipart", die als "Checksum" und "multipart" bezeichnet werden müssen. Aufgrund früherer allgemeiner Verwendung sind mehrere Ausnahmen in die Regel integriert, und es werden mehrere einzelne Wörter gekennzeichnet, z. b. "Toolbar" und "filename", die als zwei unterschiedliche Wörter (in diesem Fall "Toolbar" und "filename") geschrieben werden sollten.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Ändern Sie den Namen so, dass er richtig geschrieben ist.

## <a name="language"></a>Sprache

Die Rechtschreibprüfung prüft zurzeit nur auf englischsprachige Kultur Wörterbücher. Sie können die Kultur des Projekts in der Projektdatei ändern, indem Sie das Element " **codeanalysiscculture** " hinzufügen.

Beispiel:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Wenn Sie die Kultur auf eine andere Kultur als Englisch festlegen, wird diese Code Analyse Regel im Hintergrund deaktiviert.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn beide Teile des Verbund Worts vom Rechtschreib Wörterbuch erkannt werden und die Absicht ist, zwei Wörter zu verwenden.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1701: Ressourcen Zeichenfolgen-Verbund Wörter sollten korrekt geschrieben werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Bezeichner sollten sich um mehr als einen Fall unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Siehe auch

- [Richtlinien für die Benennung](/dotnet/standard/design-guidelines/naming-guidelines)
- [Konventionen für die Groß-/Kleinschreibung](/dotnet/standard/design-guidelines/capitalization-conventions)