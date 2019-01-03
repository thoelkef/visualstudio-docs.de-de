---
title: 'CA1004: Generische Methoden müssen den Typparameter angeben.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2fe40093253cb57d60c2a06239b47b5f3141f76c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53825343"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Generische Methoden müssen den Typparameter angeben.

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

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Bereitstellen von Generika in einer Syntax, die einfach zu verstehen und einzusetzen, verkürzt die Zeit, die ist erforderlich, um zu erfahren und erhöht sich die Übernahmerate von neuen Bibliotheken.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Syntax zum Aufrufen von generischer Methoden. Das Typargument für `InferredTypeArgument` abgeleitet ist, und das Typargument für `NotInferredTypeArgument` muss explizit angegeben werden.

 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member in generischen Typen nicht deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: NACH MÖGLICHKEIT Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
 [Generika](/dotnet/csharp/programming-guide/generics/index)