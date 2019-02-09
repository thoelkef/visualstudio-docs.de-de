---
title: 'CA2241: Geben Sie die korrekte Anzahl für Formatierungsmethoden an.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f9f48f9cba146251aee1a58ffc7a3403ed899c4a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55921496"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Geben Sie die korrekte Anzahl für Formatierungsmethoden an.

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Die `format` Zeichenfolgenargument an eine Methode übergeben, wie z. B. <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, oder <xref:System.String.Format%2A?displayProperty=fullName> enthält keine Formatelement, das den einzelnen Objektargumenten (oder umgekehrt) entspricht.

## <a name="rule-description"></a>Regelbeschreibung
 Die Argumente für Methoden, z. B. <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A>, und <xref:System.String.Format%2A> bestehen aus einer Formatzeichenfolge gefolgt von mehreren <xref:System.Object?displayProperty=fullName> Instanzen. Die Formatzeichenfolge besteht aus Text und eingebetteten Formatelemente, die das Format {Index [, Ausrichtung] [: FormatString]}. "Index" ist eine nullbasierte ganze Zahl, die von den zu formatierenden Objekten angibt, an. Wenn ein Objekt nicht über einen entsprechenden Index in der Formatzeichenfolge verfügt, wird das Objekt ignoriert. Wenn das Objekt anhand des "Index" nicht vorhanden ist, eine <xref:System.FormatException?displayProperty=fullName> wird zur Laufzeit ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, geben Sie ein Formatelement, das für jedes Objektargument aus, und geben Sie ein Objektargument für jedes Formatelement.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Verstöße gegen die Regel an.

 [!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
 [!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]