---
title: 'CA1004: Generische Methoden müssen den Typparameter angeben.'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9a09d06a521c4751e3aea78b72b99a8126f4e7ff
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923247"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Generische Methoden müssen den Typparameter angeben.

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Die Parameter Signatur einer extern sichtbaren generischen Methode enthält keine Typen, die allen Typparametern der Methode entsprechen.

## <a name="rule-description"></a>Regelbeschreibung
Mithilfe eines Rückschlusses wird das Typargument einer generischen Methode nach dem Typ des an die Methode übergebenen Arguments festgelegt, anstatt nach der expliziten Spezifikation des Typarguments. Um den Rückschluss zu aktivieren, muss die Parametersignatur einer generischen Methode einen Parameter einschließen, der vom selben Typ wie der Typparameter für die Methode ist. In diesem Fall muss das Typargument nicht angegeben werden. Wenn Sie den Rückschluss für alle Typparameter verwenden, ist die Syntax zum Aufrufen von generischen und nicht generischen Instanzmethoden identisch. Dies vereinfacht die Verwendbarkeit generischer Methoden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf so, dass die Parameter Signatur denselben Typ für jeden Typparameter der Methode enthält.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel. Das Bereitstellen von Generika in einer Syntax, die leicht zu verstehen und zu verwenden ist, reduziert die Zeit, die erforderlich ist, um zu lernen und die Akzeptanz Rate neuer Bibliotheken zu erhöhen.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt die Syntax zum Aufrufen von zwei generischen Methoden. Das Typargument für `InferredTypeArgument` wird abgeleitet, und das Typargument für `NotInferredTypeArgument` muss explizit angegeben werden.

[!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
[!code-csharp[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1005: Übermäßige Parameter für generische Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Sammlungen sollten eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Generische Typen in Element Signaturen nicht Schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Generika ggf. verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
[Generika](/dotnet/csharp/programming-guide/generics/index)