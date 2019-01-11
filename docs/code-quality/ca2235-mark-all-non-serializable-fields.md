---
title: 'CA2235: Alle nicht serialisierbaren Felder markieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 484755feac873be04648cfef936b2faa701bba2c
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154149"
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
 Ein serialisierbarer Typ mit gekennzeichnet ist, wird die <xref:System.SerializableAttribute?displayProperty=fullName> Attribut. Wenn der Typ serialisiert wird, eine <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> Ausnahme wird ausgelöst, wenn der Typ ein Instanzenfeld eines Typs enthält, die nicht serialisierbar ist.
 
 Eine Ausnahme ist, wenn der Typ, benutzerdefinierte Serialisierung, die über verwendet die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle. Typen implementieren diese Schnittstelle bieten, ihre eigene Serialisierungslogik und daher CA2235 für solche Typen nicht serialisierbaren Instanzfelder nicht ausgelöst wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden die <xref:System.NonSerializedAttribute?displayProperty=fullName> -Attribut auf das Feld, das nicht serialisierbar ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie nur eine Warnung dieser Regel auf, wenn eine <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> Typ wird deklariert, die Instanzen des Felds, das serialisiert und deserialisiert werden können.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt ein Typ, der gegen die Regel verstößt und ein Typ, der die Regel erfüllt.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2236: Aufrufen von Basisklassenmethoden auf ISerializable-Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)
