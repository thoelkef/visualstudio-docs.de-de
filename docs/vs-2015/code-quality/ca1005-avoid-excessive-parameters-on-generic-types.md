---
title: 'CA1005: übermäßige Parameter für generische Typen vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56c69badf76a05351b37a7c8a41a9cacf54f9974
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539723"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer generischer Typ weist mehr als zwei Typparameter auf.

## <a name="rule-description"></a>Beschreibung der Regel
 Je mehr Typparameter ein generischer Typ enthält, desto schwieriger ist es, zu wissen und zu behalten, was die einzelnen Typparameter darstellen. Es ist in der Regel mit einem Typparameter offensichtlich, wie in `List<T>` , und in bestimmten Fällen mit zwei Typparametern, wie in `Dictionary<TKey, TValue>` . Wenn mehr als zwei Typparameter vorhanden sind, wird die Schwierigkeit für die meisten Benutzer zu groß (z `TooManyTypeParameters<T, K, V>` . b. in c# oder `TooManyTypeParameters(Of T, K, V)` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf so, dass er nicht mehr als zwei Typparameter verwendet.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, der Entwurf erfordert unbedingt mehr als zwei Typparameter. Das Bereitstellen von Generika in einer Syntax, die leicht zu verstehen und zu verwenden ist, reduziert die Zeit, die erforderlich ist, um zu lernen und die Akzeptanz Rate neuer Bibliotheken zu erhöhen.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Nach Möglichkeit Generics verwenden.](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Weitere Informationen
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
