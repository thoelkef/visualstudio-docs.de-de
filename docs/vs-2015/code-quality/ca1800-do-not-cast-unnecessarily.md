---
title: 'CA1800: Keine unnötigen Umwandlungen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d31cc102aae54ef60b8c16742ffe7e4381df5325
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946483"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Keine unnötigen Umwandlungen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode führt die doppelte Umwandlungen für eines der Argumente oder lokale Variablen. Für die vollständige Analyse durch diese Regel muss der getestete Assembly mit Debuginformationen erstellt werden, und die zugehörigen Programmdatenbankdatei (.pdb) muss verfügbar sein.

## <a name="rule-description"></a>Regelbeschreibung
 Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. Für explizite doppelte Umwandlungsvorgänge speichern Sie das Ergebnis der Umwandlung in eine lokale Variable, und verwenden Sie die lokale Variable anstelle der doppelten Umwandlungsvorgänge.

 Wenn der C#- `is` Operator wird verwendet, um zu testen, ob die Umwandlung erfolgreich ist, bevor die eigentliche Umwandlung ausgeführt wird, sollten Sie erwägen, das Ergebnis der `as` Operator stattdessen. Dies bietet dieselbe Funktionalität ohne die implizite Umwandlung von ausgeführten Vorgang die `is` Operator.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung der Methode um die Anzahl der Cast-Vorgänge zu minimieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, unterdrücken Sie eine Warnung dieser Regel, oder die Regel vollständig zu ignorieren, wenn Leistung nicht relevant ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die die Regel verletzen, mit der C#- `is` Operator. Eine zweite Methode entspricht die Regel durch Ersetzen der `is` Operator in einem Test für das Ergebnis der `as` -Operator, der verringert die Anzahl der Cast-Vorgänge pro Iteration von zwei auf einen.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, `start_Click`, besitzt mehrere doppelte explizite Umwandlungen, die gegen die Regel, und eine Methode, `reset_Click`, die der Regel entspricht, durch die Umwandlung in eine lokale Variable zu speichern.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Siehe auch
 [as](http://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](http://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
