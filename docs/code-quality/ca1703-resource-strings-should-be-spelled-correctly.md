---
title: 'CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden.'
ms.date: 03/28/2018
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edd3945953a07b10aee5c2690a25aafe446e2c10
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234326"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden.

|||
|-|-|
|TypeName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel analysiert die Ressourcen Zeichenfolge in Wörter (tokenarisierung von zusammengesetzten Wörtern) und überprüft die Schreibweise der einzelnen Wörter/Token. Weitere Informationen zum-Algorithmus finden [Sie unter CA1704: Bezeichner sollten korrekt](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)geschrieben werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie komplette Wörter, die richtig geschrieben sind, oder fügen Sie einem benutzerdefinierten Wörterbuch die Wörter hinzu. Weitere Informationen zum Verwenden von benutzerdefinierten Wörterbüchern finden [Sie unter CA1704: Bezeichner sollten korrekt](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)geschrieben werden.

## <a name="change-the-dictionary-language"></a>Ändern der Wörterbuch Sprache

Standardmäßig wird die englische Version (en) der Rechtschreibprüfung verwendet. Wenn Sie die Sprache der Rechtschreibprüfung ändern möchten, können Sie dies durch Hinzufügen eines der folgenden Attribute zu Ihrer *AssemblyInfo.cs* -oder *AssemblyInfo. vb* -Datei erreichen:

- Verwenden <xref:System.Reflection.AssemblyCultureAttribute> Sie, um die Kultur anzugeben, wenn sich Ihre Ressourcen in einer Satellitenassembly befinden.
- Verwenden <xref:System.Resources.NeutralResourcesLanguageAttribute> Sie, um die *neutrale Kultur* der Assembly anzugeben, wenn sich Ihre Ressourcen in derselben Assembly wie Ihr Code befinden.

> [!IMPORTANT]
> Wenn Sie die Kultur auf eine andere Kultur als Englisch festlegen, wird diese Code Analyse Regel im Hintergrund deaktiviert.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel. Korrekt geschriebene Wörter verkürzen die Zeit, die erforderlich ist, um neue Software Bibliotheken zu erlernen.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1701: Ressourcen Zeichenfolgen-Verbund Wörter sollten korrekt geschrieben werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Bezeichner sollten korrekt geschrieben werden.](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Literale sollten korrekt geschrieben werden.](../code-quality/ca2204-literals-should-be-spelled-correctly.md)