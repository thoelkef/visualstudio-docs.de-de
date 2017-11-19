---
title: "CA1701: Zusammengesetzte Begriffen in Ressourcenzeichenfolgen sollte werden Groß-/Kleinschreibung beachtet ordnungsgemäß | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ResourceStringCompoundWordsShouldBeCasedCorrectly
- CA1701
helpviewer_keywords:
- CA1701
- ResourceStringCompoundWordsShouldBeCasedCorrectly
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4dee5b21724944ea26e89c2cd1ace556f1377848
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1701-resource-string-compound-words-should-be-cased-correctly"></a>CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden
|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Ressourcenzeichenfolge enthält ein zusammengesetztes Wort, das nicht angezeigt wird, beachtet werden.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Jedes Wort in der Ressourcenzeichenfolge wird in einzelne Token unterteilt, die auf die Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft-Bibliothek überprüft. Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß. Beispiele für zusammengesetzte Wörter, die dazu führen, eine Verletzung dass sind "CheckSum" und "MultiPart", "Checksum" und "Multipart", bzw. Groß-/Kleinschreibung beachtet werden sollten. Aufgrund von vorherigen allgemeine Verwendung einige Ausnahmen sind in der Regel integriert und mehrere einzelne Wörter gekennzeichnet sind, z. B. "Toolbar" und "Filename", die als zwei unterschiedliche Wörter Groß-/Kleinschreibung beachtet werden sollten. In diesem Beispiel würde "ToolBar" und "FileName" gekennzeichnet werden.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Ändern Sie das Wort, sodass es die richtige Groß-/Kleinschreibung ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn beide Teile des zusammengesetztes Wort vom des Wörterbuchs erkannt werden und zwei Wörter verwendet wird.  
  
 Sie können auch ein benutzerdefiniertes Wörterbuch für die Rechtschreibprüfung zusammengesetzte Wörter hinzufügen. Wörter im Benutzerwörterbuch werden keine Verletzungen verursacht. Weitere Informationen finden Sie unter [wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Großschreibung Konventionen](/dotnet/standard/design-guidelines/capitalization-conventions)   
 [Benennungsrichtlinien](/dotnet/standard/design-guidelines/naming-guidelines)