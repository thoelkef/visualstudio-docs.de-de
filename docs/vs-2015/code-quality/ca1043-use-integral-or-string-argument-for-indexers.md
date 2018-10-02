---
title: 'CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9fb73f52e2b3f74b5c76cb2218baa5a6cd170706
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589200"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1043: ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden](https://docs.microsoft.com/visualstudio/code-quality/ca1043-use-integral-or-string-argument-for-indexers).

|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält einen öffentlichen oder geschützten Indexer mit einem Indextyp außer <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, oder <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 Indexer, d. h. indizierte Eigenschaften sollten ganze Zahl oder Zeichenfolgentypen für den Index verwenden. Diese Typen werden i. d. r. zum Indizieren von Datenstrukturen verwendet, und erweitern den Einsatzbereich der Bibliothek. Verwenden der <xref:System.Object> Typ Fälle, in dem der spezifische Typ für ganze Zahl oder Zeichenfolge kann nicht zur Entwurfszeit angegeben werden kann, eingeschränkt werden soll. Wenn der Entwurf andere Typen für den Index erfordert, überdenken Sie, ob der Typ einen logischen Datenspeicher darstellt. Wenn sie einen logischen Datenspeicher keine darstellt, verwenden Sie eine Methode an.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Index in eine ganze Zahl oder Zeichenfolge-Typ, oder verwenden Sie eine Methode anstelle des Indexers.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel erst nach den Bedarf für den Indexer nicht dem Standard entsprechende sorgfältig geprüft.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Indexer, der verwendet eine <xref:System.Int32> Index.

 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cpp/FxCop.Design.IntegralOrStringIndexers.cpp#1)]
 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/cs/FxCop.Design.IntegralOrStringIndexers.cs#1)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.IntegralOrStringIndexers/vb/FxCop.Design.IntegralOrStringIndexers.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1023: Indexer sollten nicht mehrdimensional sein](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)



