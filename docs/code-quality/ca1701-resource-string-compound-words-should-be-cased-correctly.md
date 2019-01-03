---
title: 'CA1701: Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte beachtet werden'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2cc74bb7d3cc15e593d465a8c8d0d55275954ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841780"
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte beachtet werden

|||
|-|-|
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|
|CheckId|CA1701|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Ressourcenzeichenfolge enthält ein zusammengesetztes Wort, das anscheinend nicht beachtet werden.

## <a name="rule-description"></a>Regelbeschreibung

Jedes Wort in der Ressourcenzeichenfolge wird in einzelne Token unterteilt, die auf die Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft-Bibliothek überprüft. Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß. Beispiele für zusammengesetzte Wörter, die dazu führen, einen Verstoß dass sind "CheckSum" und "MultiPart", die als "Checksum" und "Multipart", bzw. Groß-/Kleinschreibung beachtet werden sollten. Aufgrund von vorherigen gängige Nutzungsform einige Ausnahmen werden in der Regel erstellt, und mehrere einzelne Wörter gekennzeichnet sind, z. B. "Toolbar" und "Filename", die als zwei unterschiedliche Wörter Groß-/Kleinschreibung beachtet werden sollten. In diesem Beispiel würde "ToolBar" und "FileName" gekennzeichnet werden.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Ändern Sie das Wort, sodass es die richtige Groß-/Kleinschreibung wird.

## <a name="change-the-dictionary-language"></a>Ändern Sie die Wörterbuchsprache

Standardmäßig wird die Englisch (En) Version der Rechtschreibprüfung verwendet. Wenn Sie die Sprache der Rechtschreibprüfung ändern möchten, erreichen Sie daher durch das Hinzufügen eines der folgenden Attribute auf Ihre *"AssemblyInfo.cs"* oder *AssemblyInfo.vb* Datei:

- Verwendung <xref:System.Reflection.AssemblyCultureAttribute> die Kultur angeben, wenn Ihre Ressourcen in einer Satellitenassembly befinden.
- Verwendung <xref:System.Resources.NeutralResourcesLanguageAttribute> an die *neutrale Kultur* Ihrer Assembly, wenn Ihre Ressourcen in der gleichen Assembly wie Ihren Code sind.

> [!IMPORTANT]
> Wenn Sie die Kultur auf etwas anderes als eine Kultur auf Englisch basierenden festlegen, ist diese Codeanalyse-Regelsätze im Hintergrund deaktiviert.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn beide Teile der zusammengesetzte Begriff von der Wörterbuch erkannt werden und die Absicht ist, verwenden Sie zwei Wörter.

Sie können auch ein benutzerdefiniertes Wörterbuch für die Rechtschreibprüfung zusammengesetzte Wörter hinzugefügt. Wörter im benutzerdefinierten Wörterbuchs verursachen keine Verstöße. Weitere Informationen finden Sie unter [Vorgehensweise: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="related-rules"></a>Verwandte Regeln

- [CA1702: BEI Bei zusammengesetzten Begriffen sollte beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)
- [CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
- [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

## <a name="see-also"></a>Siehe auch

- [Konventionen für die Groß-/Kleinschreibung](/dotnet/standard/design-guidelines/capitalization-conventions)
- [Richtlinien für die Benennung](/dotnet/standard/design-guidelines/naming-guidelines)