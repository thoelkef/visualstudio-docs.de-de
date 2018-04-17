---
title: 'CA1702 bei zusammengesetzten Begriffen: Bei zusammengesetzten Begriffen sollte werden Groß-/Kleinschreibung beachtet ordnungsgemäß | Microsoft Docs'
ms.date: 03/28/2018
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e554aa323127f74e25f60d515c4703b46a00bd5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden

|||
|-|-|
|TypeName|CompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1702|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechend – Wenn für Assemblys ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für Typparameter ausgelöst.|

## <a name="cause"></a>Ursache

Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß-/Kleinschreibung.

## <a name="rule-description"></a>Regelbeschreibung

Der Name des Bezeichners ist in Wörter aufgeteilt, die auf die Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination von zwei Wörtern aus, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek aktiviert ist. Wenn es erkannt wird, erzeugt der Bezeichner eine Verletzung der Regel an. Beispiele für zusammengesetzte Wörter, die dazu führen, eine Verletzung dass sind "CheckSum" und "MultiPart", "Checksum" und "Multipart", bzw. Groß-/Kleinschreibung beachtet werden sollten. Aufgrund von vorherigen häufig werden, sind einige Ausnahmen in der Regel integriert ist und mehrere einzelne Wörter gekennzeichnet sind, z. B. "Toolbar" und "Filename", sollte, Schreibweise als zwei unterschiedliche Wörter (in diesem Fall "ToolBar" und "FileName").

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandlung von Verstößen

Ändern Sie den Namen, damit es ordnungsgemäß Groß-/Kleinschreibung beachtet wird.

## <a name="language"></a>Sprache

Die Rechtschreibprüfung wird derzeit nur für die Kultur Englisch-basierte Wörterbücher überprüft. Sie können die Kultur des Projekts in der Projektdatei ändern, indem die **CodeAnalysisCulture** Element.

Zum Beispiel:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Wenn Sie die Kultur auf etwas anderes als eine Kultur Englisch-basierte festlegen, wird diese Regel zur Codeanalyse im Hintergrund deaktiviert.

## <a name="when-to-suppress-warnings"></a>Wenn Warnungen unterdrücken

Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn beide Teile des zusammengesetztes Wort werden vom des Wörterbuchs erkannt, und zwei Wörter verwendet wird.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Siehe auch

- [Richtlinien für die Benennung](/dotnet/standard/design-guidelines/naming-guidelines)
- [Konventionen für die Groß-/Kleinschreibung](/dotnet/standard/design-guidelines/capitalization-conventions)