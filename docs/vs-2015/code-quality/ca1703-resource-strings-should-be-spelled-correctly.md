---
title: 'CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ResourceStringsShouldBeSpelledCorrectly
- CA1703
helpviewer_keywords:
- CA1703
- ResourceStringsShouldBeSpelledCorrectly
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e5f5541a048d1434f64bf53e7573fa8288933e4e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855002"
---
# <a name="ca1703-resource-strings-should-be-spelled-correctly"></a>CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 Standardmäßig wird die Englisch (En) Version der Rechtschreibprüfung verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie vollständige Wörtern, die richtig geschrieben sind, oder fügen die Wörter zu einem Benutzerwörterbuch. Weitere Informationen zur Verwendung von benutzerdefinierten Wörterbüchern finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Ordnungsgemäß verringern geschriebene Wörter Zeitspanne, die für neue Softwarebibliotheken erforderlich ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

 [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)



