---
title: "CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Literals should be spelled correctly"
  - "CA2204"
  - "LiteralsShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA2204"
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode gibt ein Zeichenfolgenliteral weiter, das in einem Parameter oder einer Eigenschaft verwendet wird, der bzw. die eine lokalisierte Zeichenfolge erfordert, und die Literalzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung der Microsoft\-Bibliothek nicht erkannt wird.  
  
## Regelbeschreibung  
 Diese Regel überprüft eine Literalzeichenfolge, die als Wert an einen Parameter oder eine Eigenschaft übergeben wird, wenn mindestens einer der folgenden Fälle wahr ist:  
  
-   Das <xref:System.ComponentModel.LocalizableAttribute>\-Attribut des Parameters oder der Eigenschaft ist auf "true" festgelegt.  
  
-   Der Parameter oder Eigenschaftenname enthält "Text", "Meldung" oder "Beschriftung".  
  
-   Der Name des Zeichenfolgenparameters, der an eine Console.Write\-Methode oder eine Console.WriteLine\-Methode übergeben wird, ist entweder "Wert" oder "Format".  
  
 Diese Regel analysiert die Literalzeichenfolge in Wörter, versieht zusammengesetzte Wörter mit einem Token und prüft die Rechtschreibung jedes einzelnen Worts\/Tokens.  Informationen über den Analysealgorithmus finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Standardmäßig wird die englische Version \(EN\) der Rechtschreibprüfung verwendet.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibung des Wortes oder fügen es einem benutzerdefinierten Wörterbuch hinzu.  Informationen zum Verwenden von benutzerdefinierten Wörterbüchern finden Sie unter [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Durch fehlerfreie Begriffe wird der Lernaufwand für neue Softwarebibliotheken verringert.  
  
## Verwandte Regeln  
 [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)