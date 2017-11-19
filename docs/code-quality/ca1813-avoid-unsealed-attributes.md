---
title: 'CA1813: Nicht versiegelte Attribute vermeiden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5aec235494b29a21eb5a3c2de39a6933e04b0ebe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Nicht versiegelte Attribute vermeiden
|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher Typ erbt von <xref:System.Attribute?displayProperty=fullName>, ist nicht abstrakt und ist nicht versiegelt (`NotInheritable` in Visual Basic).  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]-Klassenbibliothek stellt Methoden zum Abrufen benutzerdefinierter Attribute bereit. Standardmäßig Durchsuchen dieser Methoden die Attributvererbungshierarchie; z. B. <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> sucht nach dem Typ des angegebenen Attributs oder ein beliebiger Attribut, das den Typ des angegebenen Attributs erweitert. Versiegeln das Attribut wird das Durchsuchen der Vererbungshierarchie befindet und kann die Leistung verbessern.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, versiegeln Sie den Typ des Attributs aus, oder machen Sie ihn abstrakt.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel. Sie sollten so vorgehen, nur dann, wenn Sie eine Attributhierarchie definieren und können nicht versiegeln das Attribut oder den Zugriff darauf abstrakte.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt ein benutzerdefiniertes Attribut, das mit dieser Regel erfüllt.  
  
 [!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1019: Zugriffsmethoden für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: Attribute mit AttributeUsageAttribute markieren](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Attribute](/dotnet/standard/design-guidelines/attributes)