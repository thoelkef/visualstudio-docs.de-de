---
title: 'CA1800: Keine unnötigen Umwandlungen'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 34c03adb8ff34d3590ed93264d77536c4cdff080
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915568"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Keine unnötigen Umwandlungen
|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine Methode führt doppelte Umwandlungen für lokale Variablen oder Argumente.

Für die vollständige Analyse durch diese Regel muss die getestete Assembly mit Debuginformationen erstellt werden, und die zugehörigen Programmdatenbankdatei (.pdb) muss verfügbar sein.

## <a name="rule-description"></a>Regelbeschreibung
Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. Für explizite doppelte Umwandlungsvorgänge speichert das Ergebnis der Umwandlung in eine lokale Variable, und verwenden Sie die lokale Variable anstelle der doppelten Umwandlungsvorgänge.

Wenn die C#- `is` Operator wird verwendet, um zu testen, ob die Umwandlung erfolgreich ist, bevor die tatsächliche Umwandlung ausgeführt wird, sollten Sie das Ergebnis des Tests der `as` Operator stattdessen. Dies bietet die gleiche Funktionalität ohne die implizite Umwandlung-Vorgang, die von ausgeführt wird die `is` Operator. In c# 7.0 und höher verwenden die `is` -Operator mit [Mustervergleich](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) zum Überprüfen der typkonvertierung und wandeln Sie den Ausdruck auf eine Variable dieses Typs in einem Schritt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung der Methode um die Anzahl der Umwandlungsvorgänge zu minimieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, oder die Regel vollständig zu ignorieren, wenn Leistung nicht relevant ist.

## <a name="examples"></a>Beispiele
 Das folgende Beispiel zeigt eine Methode, die die Regel verletzt wird, mithilfe von C#- `is` Operator. Eine zweite Methode erfüllt die Regel, die durch Ersetzen der `is` Operator in einem Test für das Ergebnis der `as` -Operator, der verringert die Anzahl der Umwandlungsvorgänge pro Iteration aus zwei auf einen. Eine dritte Methode erfüllt die Regel auch mithilfe von `is` mit [Mustervergleich](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) auf eine Variable des gewünschten Typs zu erstellen, wenn die Konvertierung erfolgreich ausgeführt werden würde.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 Das folgende Beispiel zeigt eine Methode `start_Click`, mit dem mehrere doppelte explizite Umwandlungen, die gegen die Regel und eine Methode `reset_Click`, die die Regel erfüllt, indem die Umwandlung in einer lokalen Variablen speichern.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Siehe auch
[als (C#-Referenz)](/dotnet/csharp/language-reference/keywords/as)
[ist (C#-Referenz)](/dotnet/csharp/language-reference/keywords/is)