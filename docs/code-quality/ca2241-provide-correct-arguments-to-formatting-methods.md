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
ms.openlocfilehash: 10a4cdaa1e2de768cadc569424a490aa4adb7135
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253213"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Geben Sie die korrekte Anzahl für Formatierungsmethoden an.

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Das `format` Zeichen folgen Argument, das an eine Methode <xref:System.Console.WriteLine%2A>wie <xref:System.Console.Write%2A>, oder <xref:System.String.Format%2A?displayProperty=fullName> übermittelt wird, enthält kein Format Element, das jedem Objekt Argument entspricht, oder umgekehrt.

## <a name="rule-description"></a>Regelbeschreibung
<xref:System.Console.WriteLine%2A>Die Argumente für Methoden, z. b., <xref:System.Console.Write%2A>und <xref:System.String.Format%2A> , bestehen aus einer Format Zeichenfolge, gefolgt von mehreren <xref:System.Object?displayProperty=fullName> -Instanzen. Die Format Zeichenfolge besteht aus Text-und eingebetteten Format Elementen in der Form {Index [, Alignment] [: formatString]}. ' Index ' ist eine Null basierte ganze Zahl, die angibt, welche der-Objekte formatiert werden sollen. Wenn ein Objekt keinen entsprechenden Index in der Format Zeichenfolge enthält, wird das Objekt ignoriert. Wenn das durch ' Index ' angegebene Objekt nicht vorhanden ist, wird <xref:System.FormatException?displayProperty=fullName> zur Laufzeit eine ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, geben Sie ein Format Element für jedes Objekt Argument an, und geben Sie für jedes Format Element ein Objekt Argument an.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt zwei Verstöße gegen die Regel.

[!code-vb[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/VisualBasic/ca2241-provide-correct-arguments-to-formatting-methods_1.vb)]
[!code-csharp[FxCop.Usage.FormattingArguments#1](../code-quality/codesnippet/CSharp/ca2241-provide-correct-arguments-to-formatting-methods_1.cs)]