---
title: 'CA1023: Indexer sollten nicht mehrdimensional sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3864cbef5a5ba6c013d05112af46d641aa3c1634
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1023-indexers-should-not-be-multidimensional"></a>CA1023: Indexer sollten nicht mehrdimensional sein
|||
|-|-|
|TypeName|IndexersShouldNotBeMultidimensional|
|CheckId|CA1023|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ enthält einen öffentlichen oder geschützten Indexer, der mehr als einen Index verwendet.

## <a name="rule-description"></a>Regelbeschreibung
 Indexer, d. h. indizierte Eigenschaften sollten einen einzelnen Index verwenden. Mehrdimensionaler Indexer können die Verwendbarkeit der Bibliothek deutlich abnehmen. Wenn der Entwurf mehrere Indizes erfordert, überdenken Sie, ob der Typ einen logischen Datenspeicher darstellt. Wenn dies nicht der Fall ist, verwenden Sie eine Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf an einen Ganzzahl- oder Zeichenfolgenindex verwenden, oder verwenden Sie eine Methode anstelle des Indexers.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel erst nach dem die Notwendigkeit der nicht dem Standard entsprechende Indexer sorgfältig abwägen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ `DayOfWeek03`, mit einem mehrdimensionalen Indexer, der die Regel verletzt. Der Indexer kann als eine Art der Konvertierung betrachtet werden und daher besser als eine Methode bereitgestellt. Der Typ wird umgestaltet `RedesignedDayOfWeek03` auf die Regel erfüllen.

 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-csharp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)

 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)