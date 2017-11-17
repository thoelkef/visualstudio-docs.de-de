---
title: "CA1702 bei zusammengesetzten Begriffen: Bei zusammengesetzten Begriffen sollte werden Groß-/Kleinschreibung beachtet ordnungsgemäß | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c8606656b7ffe5f64c4c162b85d24bdbd9b1de0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn für Assemblys ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für Typparameter ausgelöst.|  
  
## <a name="cause"></a>Ursache  
 Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens ein Wort anscheinend ein zusammengesetztes Wort sein, das nicht ordnungsgemäß Groß-/Kleinschreibung beachtet wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Der Name des Bezeichners ist in Wörter aufgeteilt, die auf die Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination von zwei Wörtern aus, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek aktiviert ist. Wenn es erkannt wird, erzeugt der Bezeichner eine Verletzung der Regel an. Beispiele für zusammengesetzte Wörter, die dazu führen, eine Verletzung dass sind "CheckSum" und "MultiPart", "Checksum" und "Multipart", bzw. Groß-/Kleinschreibung beachtet werden sollten. Aufgrund von vorherigen häufig werden, sind einige Ausnahmen in der Regel integriert ist und mehrere einzelne Wörter gekennzeichnet sind, z. B. "Toolbar" und "Filename", sollte, Schreibweise als zwei unterschiedliche Wörter (in diesem Fall "ToolBar" und "FileName").  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Ändern Sie den Namen, damit es ordnungsgemäß Groß-/Kleinschreibung beachtet wird.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn beide Teile des zusammengesetztes Wort vom des Wörterbuchs erkannt werden und zwei Wörter verwendet wird.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Benennungsrichtlinien](/dotnet/standard/design-guidelines/naming-guidelines)   
 [Großschreibung Konventionen](/dotnet/standard/design-guidelines/capitalization-conventions)