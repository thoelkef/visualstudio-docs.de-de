---
title: 'CA1014: Assemblys mit CLSCompliantAttribute markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9408a7b55c800a7979c39075afdf8e9e6e4c7cdb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663157"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Assemblys mit CLSCompliantAttribute markieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Auf eine Assembly wird das <xref:System.CLSCompliantAttribute?displayProperty=fullName>-Attribut nicht angewendet.

## <a name="rule-description"></a>Regelbeschreibung
 In der Common Language Specification (CLS) sind Benennungseinschränkungen, Datentypen und Regeln definiert, denen Assemblys entsprechen müssen, wenn sie in verschiedenen Programmiersprachen verwendet werden sollen. Ein guter Entwurf bedeutet, dass alle Assemblys explizit die CLS-Konformität mit <xref:System.CLSCompliantAttribute> angeben. Wenn das Attribut in einer Assembly nicht vorhanden ist, ist die Assembly nicht kompatibel.

 Eine CLS-kompatible Assembly kann Typen oder Typmember enthalten, die nicht konform sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie der Assembly das-Attribut hinzu, um einen Verstoß gegen diese Regel zu beheben. Anstatt die gesamte Assembly als nicht kompatibel zu markieren, sollten Sie bestimmen, welche Typen oder Typmember nicht kompatibel sind, und diese Elemente als solche markieren. Wenn möglich, sollten Sie eine CLS-kompatible Alternative für nicht kompatible Member bereitstellen, damit die größtmögliche Zielgruppe auf die gesamte Funktionalität Ihrer Assembly zugreifen kann.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie nicht möchten, dass die Assembly kompatibel ist, wenden Sie das-Attribut an, und legen Sie dessen Wert auf `false` fest.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, für die das <xref:System.CLSCompliantAttribute?displayProperty=fullName>-Attribut angewendet wurde, das CLS-kompatibel deklariert.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Sprachen Unabhängigkeit und sprachunabhängige Komponenten](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
