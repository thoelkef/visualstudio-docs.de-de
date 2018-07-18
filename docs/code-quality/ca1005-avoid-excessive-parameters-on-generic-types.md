---
title: 'CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 302ecdfaf4c621f0a9a34b0a5cba79ff652990a9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898037"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden
|||
|-|-|
|TypeName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer generischen Typ verfügt über mehr als zwei Typparameter.

## <a name="rule-description"></a>Regelbeschreibung
 Je mehr Typparameter ein generischer Typ enthält, desto schwieriger ist es, zu wissen und zu behalten, was die einzelnen Typparameter darstellen. Ist in der Regel mit einem Typparameter, wie im offensichtlich `List<T>`, und in bestimmten Fällen mit zwei Typparametern, wie im `Dictionary<TKey, TValue>`. Wenn mehr als zwei Typparameter vorhanden sind, wird die Schwierigkeit zu groß für die meisten Benutzer (z. B. `TooManyTypeParameters<T, K, V>` in c# oder `TooManyTypeParameters(Of T, K, V)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf an nicht mehr als zwei Typparameter verwenden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, der Berichtsentwurf mehr als zwei Typparameter absolut erfordert. Bereitstellen von Generika in eine Syntax, die leicht zu verstehen und zu verwenden ist, verringert sich die Zeit, die ist erforderlich, um zu erfahren und erhöht die Annahme-Rate der neue Bibliotheken aus.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
 [Generika](/dotnet/csharp/programming-guide/generics/index)