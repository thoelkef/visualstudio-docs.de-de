---
title: 'CA1800: Nicht unnötig umwandeln | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 466309cef8905faa9b659e2d3652975d815767fb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663103"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Keine unnötigen Umwandlungen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode führt doppelte Umwandlungen für eines ihrer Argumente oder lokale Variablen aus. Für eine vollständige Analyse dieser Regel muss die getestete Assembly mithilfe von Debuginformationen erstellt werden, und die zugehörige Programm Datenbankdatei (. pdb) muss verfügbar sein.

## <a name="rule-description"></a>Regelbeschreibung
 Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. Speichern Sie bei expliziten doppelten Umwandlungs Vorgängen das Ergebnis der Umwandlung in einer lokalen Variablen, und verwenden Sie die lokale Variable anstelle der doppelten Umwandlungs Vorgänge.

 Wenn der C# `is`-Operator verwendet wird, um zu testen, ob die Umwandlung erfolgreich ist, bevor die tatsächliche Umwandlung ausgeführt wird, sollten Sie stattdessen das Ergebnis des `as`-Operators testen. Dadurch wird die gleiche Funktionalität ohne den impliziten Umwandlungs Vorgang bereitstellt, der vom `is`-Operator ausgeführt wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung der-Methode, um die Anzahl der Umwandlungs Vorgänge zu minimieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken oder die Regel vollständig zu ignorieren, wenn die Leistung nicht relevant ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die die Regel mit dem C# `is`-Operator verletzt. Eine zweite Methode erfüllt die Regel, indem der `is`-Operator durch einen Test für das Ergebnis des `as`-Operators ersetzt wird, der die Anzahl von Umwandlungs Vorgängen pro Iterationen von zwei auf 1 verringert.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode (`start_Click`) mit mehreren doppelten expliziten Umwandlungen, die gegen die Regel verstoßen, und eine Methode, `reset_Click`, die die Regel erfüllt, indem die Umwandlung in einer lokalen Variablen gespeichert wird.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Siehe auch
 [as](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
