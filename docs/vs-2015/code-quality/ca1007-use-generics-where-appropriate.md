---
title: 'CA1007 nach Möglichkeit: Generika verwenden | Microsoft-Dokumentation'
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
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 198cd516819e9753c81449cb708514ac47c62c6e
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47524995"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Nach Möglichkeit Generika verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1007 nach Möglichkeit: nach Möglichkeit Generika verwenden](https://docs.microsoft.com/visualstudio/code-quality/ca1007-use-generics-where-appropriate).

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine extern sichtbare Methode enthält einen Verweisparameter vom Typ <xref:System.Object?displayProperty=fullName>, und die Ziele der enthaltenden Assembly [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Regelbeschreibung
 Ein Verweisparameter ist ein Parameter, die mithilfe von geändert wird die `ref` (`ByRef` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) Schlüsselwort. Der Argumenttyp, der für einen Verweisparameter bereitgestellt werden muss genau dem Typ des Verweisparameters übereinstimmen. Um einen Typ zu verwenden, der von dem Typ des Verweisparameters abgeleitet ist, muss der Typ zuerst umwandeln und eine Variable vom Typ Verweisparameters zugewiesen werden. Verwenden einer generischen Methode kann alle Typen mit gewissen Einschränkungen an die Methode übergeben werden, ohne zunächst den Typ auf den Parametertyp Verweis umzuwandeln.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, die Sie eine generische Methode, und Ersetzen Sie die <xref:System.Object> Parameter mit einem Typparameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine allgemeine Swap-Routine, die als nicht generische und generische Methoden implementiert wird. Beachten Sie, wie effizient die Zeichenfolgen ausgetauscht werden, mithilfe der generischen Methode, die im Vergleich zu nicht generischen Methode.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Siehe auch
 [Generika](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)



