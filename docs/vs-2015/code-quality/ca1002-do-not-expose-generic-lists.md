---
title: 'CA1002: generische Listen nicht verfügbar machen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6fcc4ae2a07eb7b1f155d6c65020e2c1a9ddc9f2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546847"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Generische Listen nicht verfügbar machen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ enthält einen extern sichtbaren Member, bei dem es sich um einen <xref:System.Collections.Generic.List%601?displayProperty=fullName> Typ handelt, der einen-Typ zurückgibt <xref:System.Collections.Generic.List%601?displayProperty=fullName> oder dessen Signatur einen- <xref:System.Collections.Generic.List%601?displayProperty=fullName> Parameter enthält.

## <a name="rule-description"></a>Beschreibung der Regel
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>ist eine generische Auflistung, die für die Leistung und nicht Vererbung konzipiert ist. <xref:System.Collections.Generic.List%601?displayProperty=fullName>enthält keine virtuellen Member, die das Ändern des Verhaltens einer geerbten Klasse vereinfachen. Die folgenden generischen Auflistungen sind für Vererbung konzipiert und sollten anstelle von verfügbar gemacht werden <xref:System.Collections.Generic.List%601?displayProperty=fullName> .

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den <xref:System.Collections.Generic.List%601?displayProperty=fullName> Typ in eine der generischen Auflistungen, die für Vererbung entworfen wurden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, die Assembly, die diese Warnung auslöst, ist keine wiederverwendbare Bibliothek. Beispielsweise wäre es sicher, diese Warnung in einer leistungsoptimierten Anwendung zu unterdrücken, bei der der Leistungsvorteil durch die Verwendung generischer Listen erzielt wurde.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Nach Möglichkeit Generics verwenden.](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Weitere Informationen
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
