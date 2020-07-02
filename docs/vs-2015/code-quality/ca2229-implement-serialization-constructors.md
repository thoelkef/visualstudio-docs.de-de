---
title: 'CA2229: Serialisierungskonstruktoren implementieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ba654496d80654f0d9790a01bbc41326f7a5f13e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85540490"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serialisierungskonstruktoren implementieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Der-Typ implementiert die- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle, ist kein Delegat oder eine Schnittstelle, und eine der folgenden Bedingungen ist true:

- Der-Typ verfügt über keinen Konstruktor, der ein <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> -Objekt und ein- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Objekt (die Signatur des Serialisierungskonstruktors) annimmt.

- Der Typ ist nicht versiegelt, und der Zugriffsmodifizierer für den Serialisierungskonstruktor ist nicht geschützt (Family).

- Der Typ ist versiegelt, und der Zugriffsmodifizierer für den Serialisierungskonstruktor ist nicht privat.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel ist für Typen relevant, die die benutzerdefinierte Serialisierung unterstützen. Ein Typ unterstützt die benutzerdefinierte Serialisierung, wenn die- <xref:System.Runtime.Serialization.ISerializable> Schnittstelle implementiert wird. Der Serialisierungskonstruktor ist erforderlich, um Objekte zu deserialisieren oder neu zu erstellen, die mit der-Methode serialisiert wurden <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keinen Verstoß gegen die Regel. Der Typ ist nicht deserialisierbar und funktioniert in vielen Szenarios nicht.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der die Regel erfüllt.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
