---
title: 'CA2240: ISerializable ordnungsgemäß implementieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd13bb09e8e9e3338ed37723f74ca42b09fdeb3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920811"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable ordnungsgemäß implementieren
|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ zugeordnet werden kann, wird die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle und eine der folgenden Bedingungen "true" ist:

-   Der Typ erbt, aber nicht außer Kraft setzen die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> -Methode und den Typ deklariert Instanzfelder, die nicht mit markiert sind die <xref:System.NonSerializedAttribute?displayProperty=fullName> Attribut.

-   Der Typ ist nicht versiegelt und implementiert eine <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode, die nicht extern sichtbar und überschreibbar ist.

## <a name="rule-description"></a>Regelbeschreibung
 Instanzenfelder, die in einem Typ deklariert werden, erbt die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle nicht automatisch in den Serialisierungsprozess einbezogen. Um Felder einzuschließen, muss der Typ implementiert die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode und den Serialisierungskonstruktor. Wenn die Felder nicht serialisiert werden sollen, gelten die <xref:System.NonSerializedAttribute> -Attribut auf die Felder an, diese Entscheidung explizit anzugeben.

 Typen, die nicht, Implementierungen von versiegelt sind die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode extern sichtbar sein sollte. Aus diesem Grund wird die Methode von abgeleiteten Typen aufgerufen werden kann und überschreibbar ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode sichtbar und überschreibbar, und stellen Sie sicher, dass alle Instanzenfelder in den Serialisierungsprozess einbezogen werden, oder explizit mit markiert die <xref:System.NonSerializedAttribute> Attribut.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei serialisierbare Typen, die die Regel verletzen.

 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Beispiel
 Im folgende Beispiel wird die zwei vorherigen Verstöße korrigiert, durch eine überschreibbare Implementierung der <xref:System.Runtime.Serialization.ISerializable.GetObjectData> Book-Klasse und durch eine Implementierung von `GetObjectData` für die Bibliothek-Klasse.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md) [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md) [ CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md) [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) [CA2239: bieten Deserialisierungsmethoden für optionale Felder](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)
