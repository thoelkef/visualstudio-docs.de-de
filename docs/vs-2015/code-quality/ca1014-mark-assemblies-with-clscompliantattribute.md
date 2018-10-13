---
title: 'CA1014: Assemblys mit CLSCompliantAttribute markieren | Microsoft-Dokumentation'
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
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e394d4489359d53c72426d6926479b7e5609d3dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237184"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Assemblys mit CLSCompliantAttribute markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Assembly verfügt nicht über die <xref:System.CLSCompliantAttribute?displayProperty=fullName> angewendet werden.

## <a name="rule-description"></a>Regelbeschreibung
 In der Common Language Specification (CLS) sind Benennungseinschränkungen, Datentypen und Regeln definiert, denen Assemblys entsprechen müssen, wenn sie in verschiedenen Programmiersprachen verwendet werden sollen. Gute Entwurfsprinzipien verlangen, dass alle Assemblys die CLS-Kompatibilität mit explizit angegeben <xref:System.CLSCompliantAttribute>. Wenn das Attribut nicht auf eine Assembly vorhanden ist, ist die Assembly nicht kompatibel.

 Es ist möglich, dass eine CLS-kompatible Assembly enthalten Typen, oder geben die Elemente, die nicht kompatibel sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das Attribut auf die Assembly ein. Anstelle von markieren die gesamte Assembly als nicht kompatibel, sollten Sie ermitteln, welchen Typ oder Typmember, nicht kompatibel sind, und markieren diese Elemente entsprechend. Wenn möglich, sollten Sie eine CLS-kompatible Alternative für nicht kompatible Member bereitstellen, damit die größtmögliche Zielgruppe auf alle Funktionen der Assembly zugreifen kann.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie nicht, dass die Assembly kompatibel sein müssen möchten, wenden Sie das Attribut, und setzen ihren Wert auf `false`.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, die <xref:System.CLSCompliantAttribute?displayProperty=fullName> Attribut angewendet, die CLS-kompatibel deklariert.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Sprachenunabhängigkeit und sprachunabhängige Komponenten](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)



