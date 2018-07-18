---
title: 'CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad1a25f33ce91fba7b2be8723b86067afe81632c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900085"
---
# <a name="ca1043-use-integral-or-string-argument-for-indexers"></a>CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden
|||
|-|-|
|TypeName|UseIntegralOrStringArgumentForIndexers|
|CheckId|CA1043|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält einen öffentlichen oder geschützten Indexer, der einen Indextyp außer verwendet <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName>, oder <xref:System.String?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 Indexer, d. h. indizierte Eigenschaften sollten Ganzzahl- oder Zeichenfolgentypen für den Index verwenden. Diese Typen werden i. d. r. zum Indizieren von Datenstrukturen verwendet und erweitern den Einsatzbereich der Bibliothek. Verwenden der <xref:System.Object> Typ sollten auf die Fälle, in dem der spezifische Ganzzahlen- oder Zeichenfolgenindex-Typ kann nicht zur Entwurfszeit angegeben werden, eingeschränkt werden. Wenn der Entwurf andere Typen für den Index erfordert, überdenken Sie, ob der Typ einen logischen Datenspeicher darstellt. Wenn sie keinen logischen Datenspeicher darstellt, verwenden Sie eine Methode an.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Index in eine ganze Zahl oder Zeichenfolge-Typ oder verwenden Sie eine Methode anstelle des Indexers zu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel erst nach dem die Notwendigkeit der nicht dem Standard entsprechende Indexer sorgfältig abwägen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Indexer, der verwendet ein <xref:System.Int32> Index.

 [!code-csharp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1023: Indexer sollten nicht mehrdimensional sein](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)

 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)