---
title: 'CA1703: Ressourcen Zeichenfolgen sollten korrekt geschrieben werden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2e720c1c491e88b6d89fb4b1f0175e8bc8a56e27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544052"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ResourceStringsShouldBeSpelledCorrectly|
|CheckId|CA1703|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt wird.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel analysiert die Ressourcen Zeichenfolge in Wörter (tokenarisierung von zusammengesetzten Wörtern) und überprüft die Schreibweise der einzelnen Wörter/Token. Weitere Informationen zum Algorithmus für die Verarbeitung finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

 Standardmäßig wird die englische Version (en) der Rechtschreibprüfung verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie komplette Wörter, die richtig geschrieben sind, oder fügen Sie einem benutzerdefinierten Wörterbuch die Wörter hinzu. Weitere Informationen zum Verwenden von benutzerdefinierten Wörterbüchern finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Korrekt geschriebene Wörter verkürzen die Zeit, die erforderlich ist, um neue Software Bibliotheken zu erlernen.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden.](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Bezeichner sollten korrekt geschrieben werden.](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen.](../code-quality/ca2204-literals-should-be-spelled-correctly.md)
