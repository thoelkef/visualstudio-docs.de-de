---
title: 'CA1800: Keine unnötigen Umwandlungen.'
ms.date: 10/26/2017
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 85d168e97f422a3965096a334cb2a448406604f9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233840"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Keine unnötigen Umwandlungen.

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine Methode führt doppelte Umwandlungen für eines ihrer Argumente oder lokale Variablen aus.

Für eine vollständige Analyse dieser Regel muss die getestete Assembly mithilfe von Debuginformationen erstellt werden, und die zugehörige Programm Datenbankdatei (. pdb) muss verfügbar sein.

## <a name="rule-description"></a>Regelbeschreibung
Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. Speichern Sie bei expliziten doppelten Umwandlungs Vorgängen das Ergebnis der Umwandlung in einer lokalen Variablen, und verwenden Sie die lokale Variable anstelle der doppelten Umwandlungs Vorgänge.

Wenn der C# `is` -Operator verwendet wird, um zu testen, ob die Umwandlung erfolgreich ist, bevor die tatsächliche Umwandlung ausgeführt wird, sollten `as` Sie stattdessen das Ergebnis des Operators testen. Dadurch wird die gleiche Funktionalität ohne den impliziten Umwandlungs Vorgang bereitstellt, der `is` vom-Operator ausgeführt wird. Oder verwenden Sie C# in 7,0 und höher den `is` -Operator mit [Muster](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) Abgleich, um die Typkonvertierung zu überprüfen und den Ausdruck in einem Schritt in eine Variable dieses Typs umzuwandeln.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung der-Methode, um die Anzahl der Umwandlungs Vorgänge zu minimieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken oder die Regel vollständig zu ignorieren, wenn die Leistung nicht relevant ist.

## <a name="examples"></a>Beispiele
Das folgende Beispiel zeigt eine Methode, die die Regel mit dem C# `is` -Operator verletzt. Eine zweite Methode erfüllt die Regel, indem der `is` -Operator durch einen Test für das Ergebnis `as` des-Operators ersetzt wird, wodurch die Anzahl von Umwandlungs Vorgängen pro Iterationen von zwei auf 1 verringert wird. Eine dritte Methode erfüllt die Regel auch, indem `is` mit dem [Muster](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) Vergleich verwendet wird, um eine Variable des gewünschten Typs zu erstellen, wenn die Typkonvertierung erfolgreich war.

[!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

Das folgende Beispiel zeigt die-Methode `start_Click`, die über mehrere doppelte explizite Umwandlungen verfügt, die gegen die Regel verstoßen, und `reset_Click`eine Methode,, die die Regel erfüllt, indem die Umwandlung in einer lokalen Variablen gespeichert wird.

[!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
[!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Siehe auch

- [AS (C# Referenz)](/dotnet/csharp/language-reference/keywords/as)
- [is (C# Reference)](/dotnet/csharp/language-reference/keywords/is)