---
title: 'CA1006: Generische Typen in Membersignaturen nicht schachteln.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 45ff4831875150df02d04553e75cebcab9a9f572
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236508"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Generische Typen in Membersignaturen nicht schachteln.

|||
|-|-|
|TypeName|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein extern sichtbares Element verfügt über eine Signatur, die ein arsted Type-Argument enthält.

## <a name="rule-description"></a>Regelbeschreibung
Ein geschachteltes Typargument ist ein Typargument, das auch ein generischer Typ ist. Um einen Member aufzurufen, dessen Signatur ein geschachteltes Typargument enthält, muss der Benutzer einen generischen Typ instanziieren und diesen an den Konstruktor eines zweiten generischen Typs übergeben. Die erforderliche Prozedur und die Syntax sind komplex, und diese Vorgehensweise sollte daher vermieden werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf so, dass er das Argument des Typs "netsted" entfernt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel. Das Bereitstellen von Generika in einer Syntax, die leicht zu verstehen und zu verwenden ist, reduziert die Zeit, die erforderlich ist, um zu lernen und die Akzeptanz Rate neuer Bibliotheken zu erhöhen.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt, sowie die Syntax, die erforderlich ist, um die Verletzung der Methode aufzurufen.

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1005: Übermäßige Parameter für generische Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Sammlungen sollten eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004: Generische Methoden sollten Typparameter bereitstellen.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Generika ggf. verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
[Generics](/dotnet/csharp/programming-guide/generics/index)