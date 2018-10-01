---
title: 'CA1702 bei: Bei zusammengesetzten Begriffen sollte sein Groß-/Kleinschreibung korrekt | Microsoft-Dokumentation'
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
- CA1702
- CompoundWordsShouldBeCasedCorrectly
helpviewer_keywords:
- CA1702
- CompoundWordsShouldBeCasedCorrectly
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9a5e532391937963108d405178571d02687d1af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511478"
---
# <a name="ca1702-compound-words-should-be-cased-correctly"></a>CA1702: Bei zusammengesetzten Begriffen sollte die Groß-/Kleinschreibung beachtet werden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter [CA1702 bei: Bei zusammengesetzten Begriffen sollte sein Groß-/Kleinschreibung korrekt](https://docs.microsoft.com/visualstudio/code-quality/ca1702-compound-words-should-be-cased-correctly) auf docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn ausgelöst von Assemblys.<br /><br /> Nicht unterbrechend – Wenn ausgelöst von Typparametern.|  
  
## <a name="cause"></a>Ursache  
 Der Name eines Bezeichners enthält mehrere Begriffe ein, und mindestens eines der Wörter ist anscheinend ein zusammengesetztes Wort, das nicht beachtet wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Der Name des Bezeichners ist in Wörter unterteilt, die auf die Groß-/Kleinschreibung basieren. Jede zusammenhängende Kombination von zwei Wörtern, die von der Rechtschreibprüfung aus der Microsoft-Bibliothek aktiviert ist. Der Bezeichner erzeugt, wenn es erkannt wird, einen Verstoß gegen die Regel. Beispiele für zusammengesetzte Wörter, die dazu führen, einen Verstoß dass sind "CheckSum" und "MultiPart", die als "Checksum" und "Multipart", bzw. Groß-/Kleinschreibung beachtet werden sollten. Aufgrund von vorherigen gängige Nutzungsform werden einige Ausnahmen in der Regel erstellt, und es werden mehrere einzelne Wörter gekennzeichnet, z. B. "Toolbar" und "Filename", sollten werden Groß-/Kleinschreibung als zwei unterschiedliche Wörter (in diesem Fall "ToolBar" und "FileName").  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Ändern Sie den Namen, damit sie die richtige Groß-/Kleinschreibung ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn beide Teile der zusammengesetzte Begriff von der Wörterbuch erkannt werden und die Absicht ist, verwenden Sie zwei Wörter.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Bei Bezeichnern sollte die Groß-/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß-/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Benennungsrichtlinien](http://msdn.microsoft.com/library/fc076d66-9b5f-42d3-aa65-61d970c794a3)   
 [Konventionen für die Groß-/Kleinschreibung](http://msdn.microsoft.com/library/4c4ea526-9203-486f-b72d-29d61c5b3c6d)

