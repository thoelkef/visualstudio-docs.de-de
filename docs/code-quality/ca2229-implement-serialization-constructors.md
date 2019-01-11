---
title: 'CA2229: Serialisierungskonstruktoren implementieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2228f25c344e7471c0ee8ff252d88a5454345999
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840303"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serialisierungskonstruktoren implementieren

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Der Typ implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle, keinen Delegaten oder eine Schnittstelle, und eine der folgenden Bedingungen gilt:

- Der Typ keinen Konstruktor, akzeptiert eine <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> Objekt und ein <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Objekt (die Signatur des Serialisierungskonstruktors).

- Der Typ ist nicht versiegelte und der Zugriffsmodifizierer für seinen Serialisierungskonstruktor nicht geschützt (Familie).

- Der Typ ist versiegelt, und der Zugriffsmodifizierer für die Serialisierungskonstruktor ist nicht privat.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel gilt für Typen, die benutzerdefinierte Serialisierung unterstützen. Ein Typ unterstützt die benutzerdefinierte Serialisierung, wenn er implementiert die <xref:System.Runtime.Serialization.ISerializable> Schnittstelle. Der Serialisierungskonstruktor ist erforderlich, um zu deserialisieren, Objekte oder neu erstellt, die mit serialisiert wurden die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> Methode.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keinen Verstoß gegen die Regel. Der Typ wird nicht deserialisierbar und funktionieren nicht in vielen Szenarien.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der die Regel erfüllt.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>