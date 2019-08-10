---
title: 'CA2237: ISerializable-Typen mit SerializableAttribute markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4a047ec190652e3559e8bf83fe14834ed95d8a69
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920109"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: ISerializable-Typen mit SerializableAttribute markieren.

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
Ein extern sichtbarer Typ implementiert <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> die-Schnittstelle, und der Typ ist <xref:System.SerializableAttribute?displayProperty=fullName> nicht mit dem-Attribut gekennzeichnet. Die Regel ignoriert abgeleitete Typen, deren Basistyp nicht serialisierbar ist.

## <a name="rule-description"></a>Regelbeschreibung
Um vom Common Language Runtime als serialisierbar erkannt zu werden, müssen die Typen mit dem <xref:System.SerializableAttribute> -Attribut markiert werden, auch wenn der Typ durch die Implementierung <xref:System.Runtime.Serialization.ISerializable> der-Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, wenden <xref:System.SerializableAttribute> Sie das-Attribut auf den Typ an.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie eine Warnung dieser Regel nicht für Ausnahme Klassen, da sie serialisierbar sein müssen, damit Sie über Anwendungs Domänen hinweg ordnungsgemäß funktioniert.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. Kommentieren Sie die <xref:System.SerializableAttribute> Attribut Zeile aus, um die Regel zu erfüllen.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2236: Abrufen von Basisklassen Methoden für iserialisierbare Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Implementieren Sie iserialisierbar ordnungsgemäß.](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Serialisierungsmethoden ordnungsgemäß implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239: Deserialisierungsmethoden für optionale Felder bereitstellen](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)