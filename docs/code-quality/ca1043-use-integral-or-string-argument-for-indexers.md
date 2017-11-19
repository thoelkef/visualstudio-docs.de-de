---
title: "CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
helpviewer_keywords:
- CA1043
- UseIntegralOrStringArgumentForIndexers
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aeaaf07dd3590e4dd703cfa239c48cb7e86b7f43
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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