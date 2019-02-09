---
title: 'CA2131: Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9b5cc0920e56b9fc27ef120d3328f2ba528b54dd
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55947695"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ, beteiligt von Typäquivalenz und der Typ selbst oder ein Member oder Feld des Typs wird mit markiert die <xref:System.Security.SecurityCriticalAttribute> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird für alle wichtigen Typen ausgelöst oder für Typen, die wichtige Methoden oder Felder enthalten, die an der Typäquivalenz beteiligt sind. Wenn die CLR einen derartigen Typ erkennt, ein Fehler auftritt, laden es mit einem <xref:System.TypeLoadException> zur Laufzeit. In der Regel wird diese Regel nur ausgelöst, wenn Benutzer Typäquivalenz manuell implementieren und die Typäquivalenz nicht von tlbimp und den Compilern ausführen lassen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das SecurityCritical-Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die folgenden Beispiele veranschaulichen eine Schnittstelle, eine Methode und ein Feld, das diese Regel ausgelöst zu werden.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Siehe auch
 [Sicherheitstransparenter Code, Ebene 2](/dotnet/framework/misc/security-transparent-code-level-2)