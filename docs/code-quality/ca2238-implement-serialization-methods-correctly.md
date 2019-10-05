---
title: 'CA2238: Serialisierungsmethoden korrekt implementieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b0bbe31f0431b259f60c1fe68a8d9edeffc572d9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237909"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Serialisierungsmethoden korrekt implementieren.

|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Unterbrechung: Wenn die Methode außerhalb der Assembly sichtbar ist.<br /><br /> Nicht unterbrechend: Wenn die Methode außerhalb der Assembly nicht sichtbar ist.|

## <a name="cause"></a>Ursache
Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit.

## <a name="rule-description"></a>Regelbeschreibung
Eine Methode wird als Serialisierungsereignishandler festgelegt, indem eines der folgenden Serialisierungsereignisattribute angewendet wird:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Serialisierungsereignishandler verwenden einen einzelnen Parameter vom <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>Typ, `void`geben zurück und `private` haben Sichtbarkeit.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, den Rückgabetyp oder die Sichtbarkeit des Serialisierungsereignishandlers.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt korrekt deklarierte Serialisierungsereignis-Handler.

[!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
[!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2236: Abrufen von Basisklassen Methoden für iserialisierbare Typen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Implementieren Sie iserialisierbar ordnungsgemäß.](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239: Deserialisierungsmethoden für optionale Felder bereitstellen](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)