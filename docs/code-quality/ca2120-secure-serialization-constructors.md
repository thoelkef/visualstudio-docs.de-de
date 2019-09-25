---
title: 'CA2120: Sichere Serialisierungskonstruktoren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38de3597d3693b072fec12f64211af4469851627
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232540"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Sichere Serialisierungskonstruktoren.

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Der-Typ implementiert <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> die-Schnittstelle, ist kein Delegat oder eine Schnittstelle und wird in einer Assembly deklariert, die teilweise vertrauenswürdige Aufrufer zulässt. Der-Typ verfügt über einen Konstruktor, <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> der ein- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Objekt und ein-Objekt (die Signatur des Serialisierungskonstruktors) annimmt. Dieser Konstruktor ist nicht durch eine Sicherheitsüberprüfung gesichert, aber ein oder mehrere der regulären Konstruktoren im Typ sind gesichert.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel ist für Typen relevant, die die benutzerdefinierte Serialisierung unterstützen. Ein Typ unterstützt die benutzerdefinierte Serialisierung, <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> wenn die-Schnittstelle implementiert wird. Der Serialisierungskonstruktor ist erforderlich und wird zum Deserialisieren oder erneuten Erstellen von Objekten verwendet, die mit der <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> -Methode serialisiert wurden. Da der Serialisierungskonstruktor Objekte zuordnet und initialisiert, müssen Sicherheitsüberprüfungen, die für reguläre Konstruktoren vorhanden sind, auch auf dem Serialisierungskonstruktor vorhanden sein. Wenn Sie gegen diese Regel verstoßen, können Aufrufer, die nicht anderweitig eine Instanz erstellen konnten, den Serialisierungskonstruktor verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, schützen Sie den Serialisierungskonstruktor mit Sicherheitsanforderungen, die mit denen identisch sind, die andere Konstruktoren schützen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keinen Verstoß gegen die Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt.

[!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>