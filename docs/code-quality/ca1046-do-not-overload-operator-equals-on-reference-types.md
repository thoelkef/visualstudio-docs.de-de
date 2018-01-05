---
title: "CA1046: Gleichheitsoperator für Referenztypen nicht überladen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 87c9b1ca85eb7edaf1050da96356640b06b66e0c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Gleichheitsoperator für Referenztypen nicht überladen
|||  
|-|-|  
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder verschachtelter öffentlicher Verweistyp Überladen des Gleichheitsoperators.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Für Verweistypen ist die Standardimplementierung des Gleichheitsoperators fast immer zutreffend. Standardmäßig sind zwei Verweise nur dann gleich, wenn sie auf dasselbe Objekt zeigen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die Implementierung des Gleichheitsoperators.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn der Verweistyp wie eines integrierten Werttyps verhält. Wenn Additions- oder Subtraktionsoperator auf Instanzen des Typs sind von Bedeutung ist, ist es wahrscheinlich richtig, den Gleichheitsoperator zu implementieren und die Verletzung zu unterdrücken.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht das Standardverhalten beim Vergleich zweier Verweise.  
  
 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Die folgende Anwendung vergleicht einige Verweise.  
  
 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **eine neue (2,2) und b = = new (2,2) sind gleich? Nein**  
**c und a sind gleich? Ja**  
**b und a sind ==? Nein**  
**c und a sind ==? Ja**   
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)