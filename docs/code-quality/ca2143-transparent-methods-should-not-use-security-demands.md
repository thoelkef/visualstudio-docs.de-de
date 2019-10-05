---
title: 'CA2143: Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a182beba738e583fad83c3f51d7efa312761906d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231982"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143: Transparente Methoden dürfen keine Sicherheitsanforderungen verwenden.

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein übergeordneter Typ oder eine übergeordnete Methode wird deklarativ <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> mit einem `.Demand` Bedarf gekennzeichnet, oder <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> die-Methode ruft die-Methode auf.

## <a name="rule-description"></a>Regelbeschreibung
Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern. Sicherheitstransparenter Code sollte mithilfe von vollständigen Anforderungen Sicherheitsentscheidungen fällen, und sicherheitskritischer Code sollte für die vollständige Anforderung nicht auf transparentem Code beruhen. Jeder Code, der Sicherheitsüberprüfungen durchführt, wie z. b. Sicherheitsanforderungen, sollte stattdessen sicherheitsrelevant sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, markieren Sie die Methode im Allgemeinen mit <xref:System.Security.SecuritySafeCriticalAttribute> dem-Attribut. Sie können auch die Anforderung entfernen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Die Regel Dateien für den folgenden Code, da eine transparente Methode eine deklarative Sicherheitsanforderung durchführt.

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Siehe auch
[CA2142: Transparenter Code darf nicht mit LinkDemand geschützt werden.](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)