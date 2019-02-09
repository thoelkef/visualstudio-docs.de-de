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
ms.openlocfilehash: a13aeeffbc77e4f40ff886c0d890f181697fcc11
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950681"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Keine unnötigen Umwandlungen.

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine Methode führt die doppelte Umwandlungen für eines der Argumente oder lokale Variablen.

Für die vollständige Analyse durch diese Regel muss der getestete Assembly mit Debuginformationen erstellt werden, und die zugehörigen Programmdatenbankdatei (.pdb) muss verfügbar sein.

## <a name="rule-description"></a>Regelbeschreibung
Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. Für explizite doppelte Umwandlungsvorgänge speichern Sie das Ergebnis der Umwandlung in eine lokale Variable, und verwenden Sie die lokale Variable anstelle der doppelten Umwandlungsvorgänge.

Wenn der C#- `is` Operator wird verwendet, um zu testen, ob die Umwandlung erfolgreich ist, bevor die eigentliche Umwandlung ausgeführt wird, sollten Sie erwägen, das Ergebnis der `as` Operator stattdessen. Dies bietet dieselbe Funktionalität ohne die implizite Umwandlung von ausgeführten Vorgang die `is` Operator. In c# 7.0 und höher verwenden die `is` -Operator mit [Musterabgleich](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) zum Überprüfen der typkonvertierung und wandeln Sie den Ausdruck auf eine Variable dieses Typs in einem Schritt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung der Methode um die Anzahl der Cast-Vorgänge zu minimieren.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel, oder die Regel vollständig zu ignorieren, wenn Leistung nicht relevant ist.

## <a name="examples"></a>Beispiele
 Das folgende Beispiel zeigt eine Methode, die die Regel verletzen, mit der C#- `is` Operator. Eine zweite Methode entspricht die Regel durch Ersetzen der `is` Operator in einem Test für das Ergebnis der `as` -Operator, der verringert die Anzahl der Cast-Vorgänge pro Iteration von zwei auf einen. Eine dritte Methode führt die Regel auch mithilfe `is` mit [Musterabgleich](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) , eine Variable des gewünschten Typs zu erstellen, wenn die Konvertierung erfolgreich ausgeführt werden würde.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 Das folgende Beispiel zeigt eine Methode, `start_Click`, besitzt mehrere doppelte explizite Umwandlungen, die gegen die Regel, und eine Methode, `reset_Click`, die der Regel entspricht, durch die Umwandlung in eine lokale Variable zu speichern.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Siehe auch

- [As (C#-Referenz)](/dotnet/csharp/language-reference/keywords/as)
- [is (C#-Referenz)](/dotnet/csharp/language-reference/keywords/is)