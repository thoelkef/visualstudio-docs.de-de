---
title: 'CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ParameterNamesShouldNotMatchMemberNames
- CA1719
helpviewer_keywords:
- CA1719
- ParameterNamesShouldNotMatchMemberNames
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2aa55993758df24346b78eb4d9ad022014d9d81c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233985"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Der Name eines extern sichtbaren Elements entspricht dem Vergleich ohne Beachtung der Groß-/Kleinschreibung dem Namen eines seiner Parameter.

## <a name="rule-description"></a>Regelbeschreibung
Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Wählen Sie einen Parameternamen aus, der nicht mit dem Elementnamen identisch ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Bei der neuen Entwicklung treten keine bekannten Szenarien auf, in denen Sie eine Warnung aus dieser Regel unterdrücken müssen. Bei Versand Bibliotheken müssen Sie möglicherweise eine Warnung aus dieser Regel unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
[CA1709: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

[CA1708: Bezeichner sollten sich um mehr als einen Fall unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

[CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)