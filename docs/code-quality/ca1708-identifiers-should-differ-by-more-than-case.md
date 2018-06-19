---
title: 'CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldDifferByMoreThanCase
- CA1708
helpviewer_keywords:
- CA1708
- IdentifiersShouldDifferByMoreThanCase
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4c952d4cf2533034c12a287149404bee6d267214
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915583"
---
# <a name="ca1708-identifiers-should-differ-by-more-than-case"></a>CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden
|||
|-|-|
|TypeName|IdentifiersShouldDifferByMoreThanCase|
|CheckId|CA1708|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Die Namen von zwei Typen, Member, Parameter oder vollständig qualifizierte Namespaces sind identisch, wenn sie in Kleinbuchstaben konvertiert wurden.

## <a name="rule-description"></a>Regelbeschreibung
 Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß-/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß- und Kleinschreibung unterscheiden müssen. Beispielsweise [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ist eine weit verbreitete Sprache, Groß-/Kleinschreibung.

 Mit dieser Regel wird für nur öffentlich sichtbare Elemente ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Namen, der eindeutig ist, wenn es mit anderen Bezeichnern in Groß-und Kleinschreibung verglichen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Die Bibliothek ist möglicherweise nicht verwendbar in allen verfügbaren Sprachen in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes
 Das folgende Beispiel zeigt einen Verstoß gegen diese Regel.

 [!code-csharp[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)