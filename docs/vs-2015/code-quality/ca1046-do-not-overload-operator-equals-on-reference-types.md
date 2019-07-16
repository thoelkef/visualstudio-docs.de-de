---
title: 'CA1046: Gleichheitsoperator für Referenztypen nicht überladen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c2d9e301b842e0cbd84e23b58310c6afad276b4a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696766"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Gleichheitsoperator für Referenztypen nicht überladen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder verschachtelter öffentlicher Verweistyp überlädt den Equality-Operator.

## <a name="rule-description"></a>Regelbeschreibung
 Für Verweistypen ist die Standardimplementierung des Gleichheitsoperators fast immer zutreffend. Standardmäßig sind zwei Verweise nur dann gleich, wenn sie auf dasselbe Objekt zeigen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die Implementierung des Gleichheitsoperators.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher ist, eine Warnung dieser Regel zu unterdrücken, wenn sich der Verweistyp wie eines integrierten Werttyps verhält. Wenn es für die Addition oder Subtraktion auf Instanzen des Typs ist von Bedeutung ist, ist es wahrscheinlich richtig ist, den Gleichheitsoperator zu implementieren und den Regelverstoß zu unterdrücken.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht das Standardverhalten für den Vergleich zwei Verweise.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefTypesNoEqualityOp/cs/FxCop.Design.RefTypesNoEqualityOp.cs#1)]

## <a name="example"></a>Beispiel
 Folgende Anwendungen werden einige Verweise verglichen.

 [!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefTypesNoEqualityOp/cs/FxCop.Design.TestRefTypesNoEqualityOp.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **eine = neue (2,2) und b = neue (2,2) gleich sind? Keine**
**c und a sind gleich? Ja**
**b und a sind ==? Keine**
**c und a sind ==? "Ja"**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Object.Equals%2A?displayProperty=fullName> [Gleichheitsoperatoren](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
