---
title: 'CA1043: ganzzahliges Argument oder Zeichen folgen Argument für Indexer verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 528b3a1f301544ccb20cfa6bddc31c0a5c50d1ca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668303"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält einen öffentlichen oder geschützten Indexer, der einen anderen Indextyp als "<xref:System.Int32?displayProperty=fullName>", "<xref:System.Int64?displayProperty=fullName>", "<xref:System.Object?displayProperty=fullName>" oder "<xref:System.String?displayProperty=fullName>" verwendet.

## <a name="rule-description"></a>Regelbeschreibung
 Indexer, d. h. indizierte Eigenschaften, sollten ganzzahlige Typen oder Zeichen folgen Typen für den Index verwenden. Diese Typen werden in der Regel zum Indizieren von Datenstrukturen und zur Verbesserung der Benutzerfreundlichkeit der Bibliothek verwendet. Die Verwendung des <xref:System.Object> Typs sollte auf die Fälle beschränkt werden, in denen der jeweilige ganzzahlige Typ oder der Typ der Zeichenfolge zur Entwurfszeit nicht angegeben werden kann. Wenn der Entwurf andere Typen für den Index erfordert, überdenken Sie, ob der Typ einen logischen Datenspeicher darstellt. Wenn Sie keinen logischen Datenspeicher darstellt, verwenden Sie eine-Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Index in einen ganzzahligen oder Zeichen Folgentyp, oder verwenden Sie eine Methode anstelle des Indexers.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel nur, nachdem sorgfältig geprüft wurde, dass es sich nicht um einen Standardindexer handelt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Indexer, der einen <xref:System.Int32> Index verwendet.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1023: Indexer sollten nicht mehrdimensional sein](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)
