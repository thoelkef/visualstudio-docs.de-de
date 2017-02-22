---
title: "CA1043: Ganzzahliges Argument oder Zeichenfolgenargument f&#252;r Indexer verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
helpviewer_keywords: 
  - "CA1043"
  - "UseIntegralOrStringArgumentForIndexers"
ms.assetid: d7f14b9e-2220-4f80-b6b8-48c655a05701
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1043: Ganzzahliges Argument oder Zeichenfolgenargument f&#252;r Indexer verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseIntegralOrStringArgumentForIndexers|  
|CheckId|CA1043|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ enthält einen öffentlichen oder geschützten Indexer mit einem anderen Indextyp als <xref:System.Int32?displayProperty=fullName>, <xref:System.Int64?displayProperty=fullName>, <xref:System.Object?displayProperty=fullName> oder <xref:System.String?displayProperty=fullName>.  
  
## Regelbeschreibung  
 Indexer, d. h. indizierte Eigenschaften, sollten ganzzahlige Typen oder Zeichenfolgentypen für den Index verwenden.  Diese Typen werden i. d. R. zum Indizieren von Datenstrukturen verwendet und erhöhen die Brauchbarkeit der Bibliothek.  Die Verwendung des <xref:System.Object>\-Typs sollte auf die Fälle beschränkt werden, in denen der spezielle Integer\- oder Zeichenfolgentyp zur Entwurfszeit nicht angegeben werden kann.  Wenn der Entwurf andere Typen für den Index erfordert, müssen Sie sich überlegen, ob der Typ einen logischen Datenspeicher darstellt.  Wenn er keinen logischen Datenspeicher darstellt, verwenden Sie eine Methode.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu behandeln, ändern Sie den Index in einen Integer\- oder Zeichenfolgentyp, oder verwenden Sie eine Methode statt des Indexers.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel erst, nachdem Sie den Bedarf für einen nicht dem Standard entsprechenden Indexer sorgfältig geprüft haben.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Indexer, der einen <xref:System.Int32>\-Index verwendet, veranschaulicht.  
  
 [!code-cs[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CSharp/ca1043-use-integral-or-string-argument-for-indexers_1.cs)]
 [!code-cpp[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/CPP/ca1043-use-integral-or-string-argument-for-indexers_1.cpp)]
 [!code-vb[FxCop.Design.IntegralOrStringIndexers#1](../code-quality/codesnippet/VisualBasic/ca1043-use-integral-or-string-argument-for-indexers_1.vb)]  
  
## Verwandte Regeln  
 [CA1023: Indexer sollten nicht mehrdimensional sein](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)  
  
 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)