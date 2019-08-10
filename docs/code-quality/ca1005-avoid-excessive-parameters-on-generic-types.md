---
title: 'CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc94a04d708315cc143afd1556cb8a2f0072e91
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923298"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.

|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein extern sichtbarer generischer Typ weist mehr als zwei Typparameter auf.

## <a name="rule-description"></a>Regelbeschreibung
Je mehr Typparameter ein generischer Typ enthält, desto schwieriger ist es, zu wissen und zu behalten, was die einzelnen Typparameter darstellen. Es ist in der Regel mit einem Typparameter offensichtlich `List<T>`, wie in, und in bestimmten Fällen mit zwei Typparametern `Dictionary<TKey, TValue>`, wie in. Wenn mehr als zwei Typparameter vorhanden sind, wird die Schwierigkeit für die meisten Benutzer zu groß (z `TooManyTypeParameters<T, K, V>` . C# b `TooManyTypeParameters(Of T, K, V)` . [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]in oder in).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf so, dass er nicht mehr als zwei Typparameter verwendet.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel, es sei denn, der Entwurf erfordert unbedingt mehr als zwei Typparameter. Das Bereitstellen von Generika in einer Syntax, die leicht zu verstehen und zu verwenden ist, reduziert die Zeit, die erforderlich ist, um zu lernen und die Akzeptanz Rate neuer Bibliotheken zu erhöhen.

## <a name="related-rules"></a>Verwandte Regeln
[CA1010: Sammlungen sollten eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Generische Typen in Element Signaturen nicht Schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Generische Methoden sollten Typparameter bereitstellen.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Generika ggf. verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
[Generika](/dotnet/csharp/programming-guide/generics/index)