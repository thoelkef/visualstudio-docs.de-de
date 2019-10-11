---
title: 'CA1707: Bezeichner sollten keine Unterstriche enthalten.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252569"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Bezeichner sollten keine Unterstriche enthalten.

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Unterbrechen: Wenn Assemblys ausgelöst werden<br /><br /> Nicht unterbrechend: Wenn für Typparameter ausgelöst|

## <a name="cause"></a>Ursache

Der Name eines Bezeichners enthält den Unterstrich (\_).

## <a name="rule-description"></a>Regelbeschreibung

Gemäß der Konvention enthalten Bezeichnernamen nicht den Unterstrich (\_). Die Regel überprüft Namespaces, Typen, Member und Parameter.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Entfernen Sie alle Unterstrich Zeichen aus dem Namen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnungen für Produktionscode. Es ist jedoch sicher, diese Warnung für Testcode zu unterdrücken. Sie können Warnungen aus dieser Regel unterdrücken, indem Sie den [Schweregrad](use-roslyn-analyzers.md#rule-severity) auf **keine**festlegen. 

## <a name="related-rules"></a>Verwandte Regeln

- [CA1709: Bezeichner sollten korrekt geschrieben werden @ no__t-0
- [CA1708: Bezeichner sollten sich um mehr als die Groß-/Kleinschreibung unterscheiden
