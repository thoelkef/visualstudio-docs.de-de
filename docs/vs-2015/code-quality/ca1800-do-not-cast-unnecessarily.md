---
title: 'CA1800: nicht unnötig umwandeln | Microsoft-Dokumentation'
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
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547796"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Keine unnötigen Umwandlungen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Category|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode führt doppelte Umwandlungen für eines ihrer Argumente oder lokale Variablen aus. Für eine vollständige Analyse dieser Regel muss die getestete Assembly mithilfe von Debuginformationen erstellt werden, und die zugehörige Programm Datenbankdatei (. pdb) muss verfügbar sein.

## <a name="rule-description"></a>Beschreibung der Regel
 Doppelte Umwandlungen beeinträchtigen die Leistung, insbesondere wenn die Umwandlungen in kompakten Iterationsanweisungen ausgeführt werden. Speichern Sie bei expliziten doppelten Umwandlungs Vorgängen das Ergebnis der Umwandlung in einer lokalen Variablen, und verwenden Sie die lokale Variable anstelle der doppelten Umwandlungs Vorgänge.

 Wenn der c#- `is` Operator verwendet wird, um zu testen, ob die Umwandlung erfolgreich ist, bevor die tatsächliche Umwandlung ausgeführt wird, sollten Sie ggf. das Ergebnis des `as` Operators testen. Dadurch wird die gleiche Funktionalität ohne den impliziten Umwandlungs Vorgang bereitstellt, der vom-Operator ausgeführt wird `is` .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie die Implementierung der-Methode, um die Anzahl der Umwandlungs Vorgänge zu minimieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken oder die Regel vollständig zu ignorieren, wenn die Leistung nicht relevant ist.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Methode, die mit dem c#-Operator gegen die Regel verstößt `is` . Eine zweite Methode erfüllt die Regel, indem der- `is` Operator durch einen Test für das Ergebnis des- `as` Operators ersetzt wird, wodurch die Anzahl von Umwandlungs Vorgängen pro Iterationen von zwei auf 1 verringert wird.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die-Methode, die `start_Click` über mehrere doppelte explizite Umwandlungen verfügt, die gegen die Regel verstoßen, und eine Methode, `reset_Click` , die die Regel erfüllt, indem die Umwandlung in einer lokalen Variablen gespeichert wird.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Weitere Informationen
 [as](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43) unverändert
