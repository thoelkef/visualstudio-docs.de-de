---
title: 'CA2204: Literale sollten korrekt geschrieben werden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords: CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ad1fb951f17d223f248c678738070d1c5b70ae7d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen
|||  
|-|-|  
|TypeName|LiteralsShouldBeSpelledCorrectly|  
|CheckId|CA2204|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Eine Methode übergibt ein die Zeichenfolgenliteral, das verwendet wird, in einem Parameter oder eine Eigenschaft, die eine lokalisierte Zeichenfolge und der literalen Zeichenfolge erfordert enthält mindestens ein Wort, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek nicht erkannt werden.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel wird überprüft, ob eine literale Zeichenfolge, die als Wert übergeben wird, um einen Parameter oder eine Eigenschaft, wenn Sie eine oder mehrere der folgenden Fälle zutrifft:  
  
-   Die <xref:System.ComponentModel.LocalizableAttribute> Attribut des Parameters oder der Eigenschaft ist festgelegt auf "true".  
  
-   Der Parameter oder die Eigenschaft Name enthält "Text", "Message" oder "Caption".  
  
-   Der Name des Parameters, der an eine Console.Write oder Console.WriteLine-Methode übergeben wird, ist "Value" oder "format".  
  
 Diese Regel analysiert das Zeichenfolgenliteral in Wörter, versehen zusammengesetzte Wörter und die Rechtschreibung in jeder Word-Token. Informationen zum Analysieren Algorithmus finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Standardmäßig wird die Englisch (En) Version der Rechtschreibprüfung verwendet.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Schreibweise des Worts oder eines Benutzerwörterbuchs fügen Sie das Wort hinzu. Informationen zur Verwendung von benutzerdefinierten Wörterbüchern finden Sie unter [wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel. Geschriebene Wörter verringert der Lernaufwand für neue Softwarebibliotheken.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)