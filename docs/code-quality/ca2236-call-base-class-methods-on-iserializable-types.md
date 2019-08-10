---
title: 'CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3f0075a6296e839030448c0209c77f1717a5fcb1
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920126"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
Ein Typ wird von einem Typ abgeleitet, der <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> die-Schnittstelle implementiert, und eine der folgenden Bedingungen ist erfüllt:

- Der-Typ implementiert den Serialisierungskonstruktor, d. h. einen Konstruktor <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> mit der <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>-Parameter Signatur, ruft jedoch nicht den Serialisierungskonstruktor des Basistyps auf.

- Der-Typ implementiert <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> die-Methode, ruft jedoch <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nicht die-Methode des Basistyps auf.

## <a name="rule-description"></a>Regelbeschreibung
Bei einem benutzerdefinierten Serialisierungsprozess implementiert ein <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Typ die-Methode, um seine Felder zu serialisieren, und der Serialisierungskonstruktor, um die Felder zu deserialisieren. Wenn der Typ von einem Typ abgeleitet wird, der <xref:System.Runtime.Serialization.ISerializable> die-Schnittstelle implementiert <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> , sollten die Basistyp Methode und der Serialisierungskonstruktor aufgerufen werden, um die Felder des Basistyps zu serialisieren/deserialisieren. Andernfalls wird der Typ nicht serialisiert und deserialisiert. Beachten Sie Folgendes: Wenn der abgeleitete Typ keine neuen Felder hinzufügt, muss der Typ weder die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode noch den Serialisierungskonstruktor implementieren oder die Basistyp Entsprechungen aufzurufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Basistyp Methode oder den Serialisierungskonstruktor von der entsprechenden abgeleiteten Typmethode oder dem entsprechenden Konstruktor aufzurufen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird ein abgeleiteter Typ gezeigt, der die Regel erfüllt, indem der Serialisierungskonstruktor und die- <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode der Basisklasse aufgerufen werden.

[!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
[!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2240: Implementieren Sie iserialisierbar ordnungsgemäß.](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Serialisierungsmethoden ordnungsgemäß implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239: Deserialisierungsmethoden für optionale Felder bereitstellen](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)