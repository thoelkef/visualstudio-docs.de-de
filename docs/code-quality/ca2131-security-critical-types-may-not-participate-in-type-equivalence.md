---
title: 'CA2131: Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a6689e6f0be6db4b14f03006d1aa784ae70642ef
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915694"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Sicherheitskritische Typen dürfen nicht an Typäquivalenz beteiligt sein
|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ beteiligt, Typäquivalenz und der Typ selbst oder ein Member oder Feld des Typs ist mit markiert die <xref:System.Security.SecurityCriticalAttribute> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel wird für alle wichtigen Typen ausgelöst oder für Typen, die wichtige Methoden oder Felder enthalten, die an der Typäquivalenz beteiligt sind. Wenn die CLR einen derartigen Typ erkennt, ein Fehler auftritt, laden Sie es mit einem <xref:System.TypeLoadException> zur Laufzeit. In der Regel wird diese Regel nur ausgelöst, wenn Benutzer Typäquivalenz manuell implementieren und die Typäquivalenz nicht von tlbimp und den Compilern ausführen lassen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das SecurityCritical-Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Die folgenden Beispiele veranschaulichen eine Schnittstelle, eine Methode und ein Feld, das mit dieser Regel Auslösung bewirkt.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]

## <a name="see-also"></a>Siehe auch
 [Sicherheitstransparenter Code, Ebene 2](/dotnet/framework/misc/security-transparent-code-level-2)