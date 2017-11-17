---
title: "CA1715: Bezeichner sollten korrektes Präfix aufweisen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1715
- IdentifiersShouldHaveCorrectPrefix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectPrefix
- CA1715
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8e16e5cf4049ed2bf813cad20fa1be16f8f95dd8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1715-identifiers-should-have-correct-prefix"></a>CA1715: Bezeichner sollten ein korrektes Präfix aufweisen
|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn auf Schnittstellen ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für generische Typparameter ausgelöst.|  
  
## <a name="cause"></a>Ursache  
 Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit einem Großbuchstaben 'I'.  
  
 - oder -   
  
 Der Name eines generischen Typparameters für einen extern sichtbaren Typ oder Methode beginnt nicht mit einem Großbuchstaben ' t '.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Starten gemäß der Konvention werden die Namen bestimmter Programmierelemente mit einem bestimmten Präfix ein.  
  
 Schnittstellennamen sollten mit Großbuchstaben 'I' gefolgt von einem weiteren Großbuchstaben beginnen. Diese Regel wird berichtet, Verstöße für Schnittstellennamen wie "MyInterface" und "IsolatedInterface".  
  
 Generischer Typparameternamen sollten beginnen mit einem großen ' t ' und optional durch eine andere Großbuchstaben gefolgt werden kann. Diese Regel wird berichtet, Verstöße für Parameternamen wie z. B. "V" und "Type" generischer Typ.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Benennen Sie den Bezeichner, damit es ordnungsgemäß vorangestellt ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 **Das folgende Beispiel zeigt eine falsch benannte Schnittstelle.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## <a name="example"></a>Beispiel  
 **Im folgende Beispiel wird der vorherige Verstoß, indem Sie die Schnittstelle 'I' voranstellen korrigiert.**  
  
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## <a name="example"></a>Beispiel  
 **Das folgende Beispiel zeigt einen falsch benannte generischen Typparameter.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]  
  
## <a name="example"></a>Beispiel  
 **Im folgenden Beispiel wird der vorherige Verstoß, indem Sie die generischen Typparameter mit ' t voranstellen korrigiert ".**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-csharp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1722: Bezeichner sollten kein falsches Präfix aufweisen](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)