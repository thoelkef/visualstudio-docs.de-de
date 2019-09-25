---
title: 'CA2239: Deserialisierungsmethoden für optionale Felder angeben.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cf2e30956879c0c61bb57d65b89445962f34959a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237895"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Deserialisierungsmethoden für optionale Felder angeben.

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein Typ verfügt über ein Feld, das mit dem <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> -Attribut markiert ist, und der-Typ stellt keine deserialisierungsereignisbehandlungsmethoden bereit.

## <a name="rule-description"></a>Regelbeschreibung
Das <xref:System.Runtime.Serialization.OptionalFieldAttribute> -Attribut hat keine Auswirkung auf die Serialisierung. ein mit dem-Attribut gekennzeichnetes Feld wird serialisiert. Das Feld wird bei der Deserialisierung jedoch ignoriert und behält den dem Typ zugeordneten Standardwert bei. Die Deserialisierungsereignishandler müssen deklariert werden, um das Feld während des Deserialisierungsprozesses festzulegen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, fügen Sie dem Typ deserialisierungsereignisbehandlungsmethoden hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn das Feld während des Deserialisierungsprozesses ignoriert werden soll.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ mit optionalen Ereignis Behandlungsmethoden für Feld und Deserialisierung.

[!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
[!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2236: Abrufen von Basisklassen Methoden für iserialisierbare Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Implementieren Sie iserialisierbar ordnungsgemäß.](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Serialisierungsmethoden ordnungsgemäß implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)