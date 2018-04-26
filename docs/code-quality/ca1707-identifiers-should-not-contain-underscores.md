---
title: 'CA1707: Bezeichner sollten keine Unterstriche enthalten'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 36ced0a2ef262a274931e3a17236da11e894f393
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Bezeichner sollten keine Unterstriche enthalten
|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechend – Wenn auf Assemblys ausgelöst<br /><br /> Nicht unterbrechend – Wenn für Typparameter ausgelöst|

## <a name="cause"></a>Ursache
 Der Name eines Bezeichners enthält den Unterstrich (_) enthalten.

## <a name="rule-description"></a>Regelbeschreibung
 Bezeichnernamen dürfen keinen Unterstrich (_) enthalten. Die Regel wird überprüft, Namespaces, Typen, Member und Parameter.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Entfernen Sie alle Unterstrichzeichen aus dem Namen ein.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)