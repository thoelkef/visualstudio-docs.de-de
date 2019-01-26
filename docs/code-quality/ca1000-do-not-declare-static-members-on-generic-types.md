---
title: 'CA1000: Statische Member nicht in generischen Typen deklarieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f15fc2bf7a8bc4e7e47efaad351ac33638195afd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971753"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Statische Member nicht in generischen Typen deklarieren.

|||
|-|-|
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein generischer extern sichtbarer Typ enthält eine `static` (`Shared` in Visual Basic) Member.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn eine `static` Member eines generischen Typs aufgerufen wird, muss das Typargument für den Typ angegeben werden. Wenn ein generischer Instanzmember, der keine Unterstützung für Rückschlüsse bietet, aufgerufen wird, muss das Typargument für den Member angegeben werden. Die Syntax zum Angeben des Typarguments in diesen beiden Fällen ist unterschiedlich und leicht zu verwechseln, wie die folgenden Aufrufe zeigen:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

 Beide vorherigen Deklarationen sollten im Allgemeinen vermieden werden, damit das Typargument nicht angegeben werden, wenn der Member aufgerufen wird. Dies führt eine Syntax zum Aufrufen von Membern in Generika, die die Syntax für nicht generische Typen nicht unterscheidet. Weitere Informationen finden Sie unter [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den statischen Member aus, oder ändern Sie ihn in ein Instanzmember.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Bereitstellen von Generika in einer Syntax, die einfach zu verstehen und einzusetzen, verkürzt die Zeit, die ist erforderlich, um zu erfahren und erhöht sich die Übernahmerate von neuen Bibliotheken.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
 [Generika](/dotnet/csharp/programming-guide/generics/index)