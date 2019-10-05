---
title: 'CA2235: Alle nicht serialisierbaren Felder markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238104"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Alle nicht serialisierbaren Felder markieren.

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert.

## <a name="rule-description"></a>Regelbeschreibung

Ein serialisierbarer Typ ist ein Typ, der mit <xref:System.SerializableAttribute?displayProperty=fullName> dem-Attribut markiert ist. Wenn der Typ serialisiert wird, wird <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> eine-Ausnahme ausgelöst, wenn der Typ ein Instanzfeld eines Typs enthält, der nicht serialisierbar ist *und* die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> -Schnittstelle nicht implementiert.

> [!TIP]
> CA2235 wird für Instanzfelder von Typen, die implementieren <xref:System.Runtime.Serialization.ISerializable> , nicht ausgelöst, da Sie Ihre eigene Serialisierungslogik bereitstellen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, wenden <xref:System.NonSerializedAttribute?displayProperty=fullName> Sie das-Attribut auf das Feld an, das nicht serialisierbar ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrückt nur eine Warnung aus dieser Regel, <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> wenn ein Typ deklariert wird, mit dem Instanzen des Felds serialisiert und deserialisiert werden können.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt zwei Typen: einen, der gegen die Regel verstößt, und einen, der die Regel erfüllt.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Hinweise

Rule CA2235 analysiert keine Typen, die die <xref:System.Runtime.Serialization.ISerializable> -Schnittstelle implementieren (es sei denn, Sie sind auch mit dem <xref:System.SerializableAttribute> -Attribut gekennzeichnet). Dies liegt daran, dass [rule CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) bereits die Markierung von Typen <xref:System.Runtime.Serialization.ISerializable> empfiehlt, die <xref:System.SerializableAttribute> die-Schnittstelle mit dem-Attribut implementieren

## <a name="related-rules"></a>Verwandte Regeln

- [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Abrufen von Basisklassen Methoden für iserialisierbare Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Serialisierungsmethoden ordnungsgemäß implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Deserialisierungsmethoden für optionale Felder bereitstellen](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Implementieren Sie iserialisierbar ordnungsgemäß.](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)