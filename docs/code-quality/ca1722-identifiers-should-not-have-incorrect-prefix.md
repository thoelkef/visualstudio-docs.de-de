---
title: "CA1722: Bezeichner sollten kein falsches Präfix aufweisen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 84cf14fc28a3de1d6ff5bff9e40216953d5d1461
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Bezeichner sollten kein falsches Präfix aufweisen
|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein Bezeichner weist ein falsches Präfix.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen.  
  
 Typnamen müssen sich nicht auf ein bestimmtes Präfix und sollte nicht mit einem "C" als Präfix verwendet werden. Diese Regel meldet Verstöße für Typnamen wie "CMyClass" und gibt keine Auskunft über Verstöße für Typnamen wie "Cache".  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Entfernen Sie das Präfix, aus dem Bezeichner.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1715: Bezeichner sollten ein korrektes Präfix aufweisen](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)