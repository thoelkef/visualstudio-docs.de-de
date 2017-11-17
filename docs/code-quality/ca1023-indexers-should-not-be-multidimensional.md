---
title: 'CA1023: Indexer sollten nicht mehrdimensional sein | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IndexersShouldNotBeMultidimensional
- CA1023
helpviewer_keywords:
- CA1023
- IndexersShouldNotBeMultidimensional
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c3b677f4cde4a38b2e682e36090e7a86f68e4fc5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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