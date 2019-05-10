---
title: 'CA2240: ISerializable ordnungsgemäß implementieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9ef3e012b3a818c60be23278fe622a40330f3b43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541479"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable ordnungsgemäß implementieren.

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein extern sichtbarer Typ zugewiesen werden, ist die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> -Schnittstelle und eine der folgenden Bedingungen zutrifft:

- Der Typ erbt, aber überschreibt nicht die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> -Methode und den Typ deklariert Instanzfelder, die nicht mit gekennzeichnet sind die <xref:System.NonSerializedAttribute?displayProperty=fullName> Attribut.

- Der Typ ist nicht versiegelt und implementiert eine <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode, die nicht extern sichtbar und überschreibbar ist.

## <a name="rule-description"></a>Regelbeschreibung
 Instanzfelder, die in einem Typ deklariert werden, erbt die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle sind nicht automatisch in den Serialisierungsprozess enthalten. Um Felder einzuschließen, der Typ muss implementieren die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode und den Serialisierungskonstruktor. Wenn die Felder nicht serialisiert werden sollen, wenden Sie die <xref:System.NonSerializedAttribute> -Attribut auf die Felder aus, um die Entscheidung explizit anzugeben.

 Typen, die nicht, Implementierungen von versiegelt sind die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> sollte die Methode extern sichtbar sein. Aus diesem Grund wird die Methode kann von abgeleiteten Typen aufgerufen werden und überschreibbar ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode sichtbar und überschreibbar, und stellen Sie sicher, dass alle Instanzenfelder in den Serialisierungsprozess einbezogen werden, oder explizit mit markiert die <xref:System.NonSerializedAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei serialisierbare Typen, die die Regel verletzen.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die zwei vorherigen Verstöße korrigiert durch eine überschreibbare Implementierung der <xref:System.Runtime.Serialization.ISerializable.GetObjectData> für die Buch-Klasse und durch eine Implementierung von `GetObjectData` für die Bibliothek-Klasse.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA2236: Aufrufen von Basisklassenmethoden auf ISerializable-Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)