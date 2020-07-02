---
title: 'CA1010: Auflistungen müssen eine generische Schnittstelle implementieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b141d755c717ad6650d2a49c98c2b26547066b7a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545521"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName> -Schnittstelle, implementiert aber nicht die <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> -Schnittstelle und die enthaltenden assemblyziele [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] . Diese Regel ignoriert Typen, die implementieren <xref:System.Collections.IDictionary?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 Um die Verwendbarkeit einer Auflistung zu erweitern, implementieren Sie eine der generischen Auflistungsschnittstellen. Anschließend kann die Auflistung verwendet werden, um generische Auflistungs Typen wie die folgenden aufzufüllen:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie eine der folgenden generischen Auflistungs Schnittstellen implementieren:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Allerdings wird die Verwendung der Sammlung eingeschränkt.

## <a name="example-violation"></a>Beispiel Verstoß

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird eine Klasse (Verweistyp) gezeigt, die von der nicht generischen- `CollectionBase` Klasse abgeleitet wird, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericViolation/cs/FxCop.Design.CollectionsGenericViolation.cs#1)]

### <a name="comments"></a>Kommentare
 Um einen Verstoß gegen diese Verletzung zu beheben, sollten Sie entweder die generischen Schnittstellen implementieren oder die Basisklasse in einen Typ ändern, der bereits sowohl die generischen als auch die nicht generischen Schnittstellen implementiert, z. b. die- `Collection<T>` Klasse.

## <a name="fix-by-base-class-change"></a>Korrektur durch Basisklassen Änderung

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird die Verletzung durch Ändern der-Basisklasse der-Auflistung von der nicht generischen- `CollectionBase` Klasse in die generische- `Collection<T>` `Collection(Of T)` Klasse (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) korrigiert.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericBase/cs/FxCop.Design.CollectionsGenericBase.cs#1)]

### <a name="comments"></a>Kommentare
 Das Ändern der Basisklasse einer bereits freigegebenen Klasse wird als Breaking Change für vorhandene Consumer angesehen.

## <a name="fix-by-interface-implementation"></a>Korrektur nach Schnittstellen Implementierung

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird die Verletzung durch Implementieren dieser generischen Schnittstellen korrigiert: `IEnumerable<T>` , `ICollection<T>` und `IList<T>` ( `IEnumerable(Of T)` , `ICollection(Of T)` und `IList(Of T)` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CollectionsGenericInterface/cs/FxCop.Design.CollectionsGenericInterface.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden.](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Nach Möglichkeit Generics verwenden.](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Weitere Informationen
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
