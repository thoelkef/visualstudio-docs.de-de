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
ms.openlocfilehash: 1a6d9acc3a74505f766fbf9cfe26fc6878fdbb4b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920051"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable ordnungsgemäß implementieren.

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein extern sichtbarer Typ kann der <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> -Schnittstelle zugewiesen werden, und eine der folgenden Bedingungen ist erfüllt:

- Der Typ erbt, überschreibt die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> -Methode jedoch nicht, und der Typ deklariert Instanzfelder, die nicht mit dem <xref:System.NonSerializedAttribute?displayProperty=fullName> -Attribut markiert sind.

- Der Typ ist nicht versiegelt, und der Typ implementiert <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> eine Methode, die nicht extern sichtbar und über schreibbar ist.

## <a name="rule-description"></a>Regelbeschreibung
Instanzfelder, die in einem Typ deklariert werden, der <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> die-Schnittstelle erbt, werden nicht automatisch in den Serialisierungsprozess eingeschlossen. Um die Felder einzuschließen, muss der Typ die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode und den Serialisierungskonstruktor implementieren. Wenn die Felder nicht serialisiert werden sollen, wenden Sie <xref:System.NonSerializedAttribute> das-Attribut auf die Felder an, um die Entscheidung explizit anzugeben.

In nicht versiegelten Typen sollten Implementierungen der <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode extern sichtbar sein. Daher kann die-Methode von abgeleiteten Typen aufgerufen werden und ist über schreibbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, machen <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Sie die Methode sichtbar und über schreibbar, und stellen Sie sicher, dass alle Instanzfelder in den Serialisierungsprozess eingeschlossen oder explizit mit dem <xref:System.NonSerializedAttribute> -Attribut markiert sind.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt zwei serialisierbare Typen, die gegen die Regel verstoßen.

[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Beispiel
Im folgenden Beispiel werden die beiden vorherigen Verstöße korrigiert, indem eine über schreibbare Implementierung <xref:System.Runtime.Serialization.ISerializable.GetObjectData> von für die Book-Klasse bereitgestellt und eine `GetObjectData` Implementierung von für die Library-Klasse bereitgestellt wird.

[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA2236: Abrufen von Basisklassen Methoden für iserialisierbare Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Serialisierungsmethoden ordnungsgemäß implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: Deserialisierungsmethoden für optionale Felder bereitstellen](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)