---
title: 'CA1004: Generische Methoden müssen den Typparameter angeben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 458817ee19269735be181e08ed12ee1ecdee329f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68182623"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Generische Methoden müssen den Typparameter angeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Die Parametersignatur einer extern sichtbaren generische Methode enthält keine Typen, die die Typparameter der Methode entsprechen.

## <a name="rule-description"></a>Regelbeschreibung
 Mithilfe eines Rückschlusses wird das Typargument einer generischen Methode nach dem Typ des an die Methode übergebenen Arguments festgelegt, anstatt nach der expliziten Spezifikation des Typarguments. Um den Rückschluss zu aktivieren, muss die Parametersignatur einer generischen Methode einen Parameter einschließen, der vom selben Typ wie der Typparameter für die Methode ist. In diesem Fall muss das Typargument nicht angegeben werden. Wenn für alle Typparameter der Rückschluss verwendet wird, ist die Syntax zum Aufrufen von generischen und nicht generischen Instanzenmethoden identisch. Dies vereinfacht die Verwendung generischer Methoden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf, sodass die Parametersignatur der gleiche Typ für jeden Typparameter der Methode enthält.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Bereitstellen von Generika in einer Syntax, die einfach zu verstehen und einzusetzen, verkürzt die Zeit, die ist erforderlich, um zu erfahren und erhöht sich die Übernahmerate von neuen Bibliotheken.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Syntax zum Aufrufen von generischer Methoden. Das Typargument für `InferredTypeArgument` abgeleitet ist, und das Typargument für `NotInferredTypeArgument` muss explizit angegeben werden.

 [!code-csharp[FxCop.Design.Inference#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/cs/FxCop.Design.Inference.cs#1)]
 [!code-vb[FxCop.Design.Inference#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/vb/FxCop.Design.Inference.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member in generischen Typen nicht deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md)