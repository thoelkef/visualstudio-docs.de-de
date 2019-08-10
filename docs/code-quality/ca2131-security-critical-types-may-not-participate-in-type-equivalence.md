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
ms.openlocfilehash: 521a44b432a5b8ea886b23aab6b39789efe3b1b0
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920706"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein.

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein Typ ist an typäquivalenz beteiligt, und der Typ selbst oder ein Member oder Feld des Typs ist mit dem <xref:System.Security.SecurityCriticalAttribute> -Attribut gekennzeichnet.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel wird für alle wichtigen Typen ausgelöst oder für Typen, die wichtige Methoden oder Felder enthalten, die an der Typäquivalenz beteiligt sind. Wenn die CLR einen solchen Typ erkennt, kann Sie zur Laufzeit nicht mit einem <xref:System.TypeLoadException> geladen werden. In der Regel wird diese Regel nur ausgelöst, wenn Benutzer Typäquivalenz manuell implementieren und die Typäquivalenz nicht von tlbimp und den Compilern ausführen lassen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Entfernen Sie das SecurityCritical-Attribut, um einen Verstoß gegen diese Regel zu beheben.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Die folgenden Beispiele veranschaulichen eine Schnittstelle, eine Methode und ein Feld, das dazu führt, dass diese Regel ausgelöst wird.

[!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Siehe auch
[Sicherheits transparenter Code, Ebene 2](/dotnet/framework/misc/security-transparent-code-level-2)