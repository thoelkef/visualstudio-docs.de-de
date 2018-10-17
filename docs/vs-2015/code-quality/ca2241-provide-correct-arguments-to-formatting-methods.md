---
title: ': Ca2241 geeignete Argumente für Formatierungsmethoden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2241
- Provide correct arguments to formatting methods
- ProvideCorrectArgumentsToFormattingMethods
helpviewer_keywords:
- ProvideCorrectArgumentsToFormattingMethods
- CA2241
ms.assetid: 83639bc4-4c91-4a07-a40e-dc5e49a84494
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8288059b2330d96d9912036b820ec3d3c859752f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171989"
---
# <a name="ca2241-provide-correct-arguments-to-formatting-methods"></a>CA2241: Geeignete Argumente für Formatierungsmethoden angeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Verstöße gegen die Regel an.

 [!code-csharp[FxCop.Usage.FormattingArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/cs/FxCop.Usage.FormattingArguments.cs#1)]
 [!code-vb[FxCop.Usage.FormattingArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.FormattingArguments/vb/FxCop.Usage.FormattingArguments.vb#1)]



