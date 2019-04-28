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
ms.openlocfilehash: 001983bf9ca182f89587b23e04828b93d12d98f1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545784"
---
# <a name="ca1719-parameter-names-should-not-match-member-names"></a>CA1719: Parameternamen sollten nicht mit Membernamen übereinstimmen.

|||
|-|-|
|TypeName|ParameterNamesShouldNotMatchMemberNames|
|CheckId|CA1719|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name eines extern sichtbaren Members übereinstimmt, in einem Groß-/Kleinschreibung Vergleich, der den Namen des einen seiner Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln. Diese stimmen in der Regel nicht überein. Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Wählen Sie einen Parameternamen an, der den Namen des Members nicht übereinstimmen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Für neue Entwicklungen keine bekannte Szenarios auftreten, in dem Sie eine Warnung dieser Regel unterdrücken müssen. Um den rückversand für Bibliotheken, müssen Sie möglicherweise eine Warnung dieser Regel zu unterdrücken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1709: Bezeichner sollten beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Bezeichner sollten sich durch die Groß-/Kleinschreibung unterscheiden.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Bezeichner sollten keine Unterstriche enthalten.](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)