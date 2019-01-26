---
title: 'CA1722: Bezeichner sollten kein falsches Präfix aufweisen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e997bce3c3e6cd96478e5b7ba6899d8563b4ac7e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029673"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Bezeichner sollten kein falsches Präfix aufweisen.

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Bezeichner weist ein falsches Präfix.

## <a name="rule-description"></a>Regelbeschreibung
 Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen.

 Typnamen müssen sich nicht auf ein bestimmtes Präfix und nicht das Präfix ein "C". Diese Regel meldet Verstöße Typnamen wie "CMyClass und meldet keine Verstöße für Typnamen wie"Cache".

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Diese Konsistenz reduziert die Lernkurve, die für neue Softwarebibliotheken erforderlich ist und zudem wird das Kundenvertrauen, dass die Bibliothek von einer Person entwickelt wurde, die Erfahrung in der Entwicklung von verwaltetem Code hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie das Präfix aus einem Bezeichner.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1715: Bezeichner sollten ein korrektes Präfix aufweisen](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)