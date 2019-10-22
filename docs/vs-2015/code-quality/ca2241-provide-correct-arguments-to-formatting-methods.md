---
title: 'CA2241: Geben Sie korrekte Argumente für Formatierungs Methoden an. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 112065b2a8b9a88241ce62dda7b32a2f2c22fc75
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672028"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Geeignete Argumente für Formatierungsmethoden angeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Das `format` String-Argument, das an eine Methode wie z. b. <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> oder <xref:System.String.Format%2A?displayProperty=fullName> übermittelt wird, enthält kein Format Element, das den einzelnen Objekt Argumenten entspricht, oder umgekehrt.

## <a name="rule-description"></a>Regelbeschreibung
 Die Argumente für Methoden wie <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> und <xref:System.String.Format%2A> bestehen aus einer Format Zeichenfolge, gefolgt von mehreren <xref:System.Object?displayProperty=fullName> Instanzen. Die Format Zeichenfolge besteht aus Text-und eingebetteten Format Elementen in der Form {Index [, Alignment] [: formatString]}. ' Index ' ist eine Null basierte ganze Zahl, die angibt, welche der-Objekte formatiert werden sollen. Wenn ein Objekt keinen entsprechenden Index in der Format Zeichenfolge enthält, wird das Objekt ignoriert. Wenn das durch ' Index ' angegebene Objekt nicht vorhanden ist, wird zur Laufzeit ein <xref:System.FormatException?displayProperty=fullName> ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, geben Sie ein Format Element für jedes Objekt Argument an, und geben Sie für jedes Format Element ein Objekt Argument an.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Verstöße gegen die Regel.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
