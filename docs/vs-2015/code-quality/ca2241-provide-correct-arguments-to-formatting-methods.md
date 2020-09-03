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
ms.openlocfilehash: 1dfd770efd4d690930155d2486b8ff1859065272
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543649"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Geben Sie die korrekte Anzahl für Formatierungsmethoden an.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|ProvideCorrectArgumentsToFormattingMethods|
|CheckId|CA2241|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Das `format` Zeichen folgen Argument, das an eine Methode wie, oder übermittelt wird, <xref:System.Console.WriteLine%2A>  <xref:System.Console.Write%2A>  <xref:System.String.Format%2A?displayProperty=fullName> enthält kein Format Element, das jedem Objekt Argument entspricht, oder umgekehrt.

## <a name="rule-description"></a>Beschreibung der Regel
 Die Argumente für Methoden, z <xref:System.Console.WriteLine%2A> <xref:System.Console.Write%2A> . b., und, bestehen aus <xref:System.String.Format%2A> einer Format Zeichenfolge, gefolgt von mehreren- <xref:System.Object?displayProperty=fullName> Instanzen. Die Format Zeichenfolge besteht aus Text-und eingebetteten Format Elementen in der Form {Index [, Alignment] [: formatString]}. ' Index ' ist eine Null basierte ganze Zahl, die angibt, welche der-Objekte formatiert werden sollen. Wenn ein Objekt keinen entsprechenden Index in der Format Zeichenfolge enthält, wird das Objekt ignoriert. Wenn das durch ' Index ' angegebene Objekt nicht vorhanden ist, <xref:System.FormatException?displayProperty=fullName> wird zur Laufzeit eine ausgelöst.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, geben Sie ein Format Element für jedes Objekt Argument an, und geben Sie für jedes Format Element ein Objekt Argument an.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Verstöße gegen die Regel.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]
