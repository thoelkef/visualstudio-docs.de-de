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
ms.openlocfilehash: 2643ff7cb8ce401462be7e5c1e52d5f985896f3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546270"
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

Diese Regel analysiert die Ressourcenzeichenfolge in Wörter, die (mit Token versehen zusammengesetzte Wörter) und überprüft die Rechtschreibung eines einzelnen Worts/Tokens. Informationen zu den Analysealgorithmus, finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie vollständige Wörtern, die richtig geschrieben sind, oder fügen die Wörter zu einem Benutzerwörterbuch. Weitere Informationen zur Verwendung von benutzerdefinierten Wörterbüchern finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="change-the-dictionary-language"></a>Ändern Sie die Wörterbuchsprache

Standardmäßig wird die Englisch (En) Version der Rechtschreibprüfung verwendet. Wenn Sie die Sprache der Rechtschreibprüfung ändern möchten, erreichen Sie daher durch das Hinzufügen eines der folgenden Attribute auf Ihre *"AssemblyInfo.cs"* oder *AssemblyInfo.vb* Datei:

- Verwendung <xref:System.Reflection.AssemblyCultureAttribute> die Kultur angeben, wenn Ihre Ressourcen in einer Satellitenassembly befinden.
- Verwendung <xref:System.Resources.NeutralResourcesLanguageAttribute> an die *neutrale Kultur* Ihrer Assembly, wenn Ihre Ressourcen in der gleichen Assembly wie Ihren Code sind.

> [!IMPORTANT]
> Wenn Sie die Kultur auf etwas anderes als eine Kultur auf Englisch basierenden festlegen, ist diese Codeanalyse-Regelsätze im Hintergrund deaktiviert.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel. Ordnungsgemäß verringern geschriebene Wörter Zeitspanne, die für neue Softwarebibliotheken erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1701: Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)
- [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)