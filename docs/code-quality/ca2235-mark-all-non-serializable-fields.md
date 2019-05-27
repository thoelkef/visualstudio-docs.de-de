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
ms.openlocfilehash: 5ebfa5e9b90951acf59c8214941b93adae76d06e
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177384"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Alle nicht serialisierbaren Felder markieren.

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert.

## <a name="rule-description"></a>Regelbeschreibung

Ein serialisierbarer Typ mit gekennzeichnet ist, wird die <xref:System.SerializableAttribute?displayProperty=fullName> Attribut. Wenn der Typ serialisiert wird, eine <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> Ausnahme wird ausgelöst, wenn der Typ ein Instanzenfeld eines Typs enthält, die nicht serialisierbar ist *und* implementiert nicht die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle.

> [!TIP]
> CA2235 wird nicht ausgelöst, z. B. Felder von Typen, die implementieren <xref:System.Runtime.Serialization.ISerializable> da sie ihre eigene Serialisierungslogik bereitstellen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, wenden die <xref:System.NonSerializedAttribute?displayProperty=fullName> -Attribut auf das Feld, das nicht serialisierbar ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie nur eine Warnung dieser Regel auf, wenn eine <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> Typ wird deklariert, die Instanzen des Felds, das serialisiert und deserialisiert werden können.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt zwei Typen: eine, die gegen die Regel und eine, die die Regel erfüllt.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Hinweise

CA2235 analysiert keine Typen, die implementiert Regel die <xref:System.Runtime.Serialization.ISerializable> Schnittstelle (es sei denn, sie sind auch mit markiert die <xref:System.SerializableAttribute> Attribut). Grund hierfür ist, [Regel CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) bereits empfiehlt Markieren von Typen, implementieren die <xref:System.Runtime.Serialization.ISerializable> eine Verbindung mit der <xref:System.SerializableAttribute> Attribut.

## <a name="related-rules"></a>Verwandte Regeln

- [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Aufrufen von Basisklassenmethoden auf ISerializable-Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)