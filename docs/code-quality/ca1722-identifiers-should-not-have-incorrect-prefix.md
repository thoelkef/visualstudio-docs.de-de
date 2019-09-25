---
title: 'CA1722: Bezeichner sollten kein falsches Präfix aufweisen.'
ms.date: 11/04/2016
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
ms.openlocfilehash: eb41f2ad4548933d10137e7f72cae59643d33043
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233875"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Bezeichner sollten kein falsches Präfix aufweisen.

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein Bezeichner weist ein falsches Präfix auf.

## <a name="rule-description"></a>Regelbeschreibung
Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen.

Typnamen haben kein bestimmtes Präfix und sollten kein "C" als Präfix aufweisen. Diese Regel meldet Verstöße gegen Typnamen wie z. b. "CMyClass" und meldet keine Verstöße gegen Typnamen, wie z. b. "Cache".

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Diese Konsistenz reduziert die Lernkurve, die für neue Software Bibliotheken erforderlich ist, und steigert das Kunden Vertrauen, dass die Bibliothek von einer Person entwickelt wurde, die über Kenntnisse in der Entwicklung von verwaltetem Code verfügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Entfernen Sie das Präfix aus dem Bezeichner.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
[CA1715: Bezeichner sollten ein korrektes Präfix aufweisen.](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)