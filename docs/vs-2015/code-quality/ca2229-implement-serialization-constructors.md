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
ms.openlocfilehash: 56d53717afc8cd966903e75f77e1745de0031745
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662844"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Serialisierungskonstruktoren implementieren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Der Typ implementiert die Schnittstelle "<xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>", ist kein Delegat oder eine Schnittstelle, und eine der folgenden Bedingungen ist "true":

- Der-Typ verfügt über keinen Konstruktor, der ein <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> Objekt und ein <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>-Objekt (die Signatur des Serialisierungskonstruktors) annimmt.

- Der Typ ist nicht versiegelt, und der Zugriffsmodifizierer für den Serialisierungskonstruktor ist nicht geschützt (Family).

- Der Typ ist versiegelt, und der Zugriffsmodifizierer für den Serialisierungskonstruktor ist nicht privat.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel ist für Typen relevant, die die benutzerdefinierte Serialisierung unterstützen. Ein Typ unterstützt die benutzerdefinierte Serialisierung, wenn die <xref:System.Runtime.Serialization.ISerializable>-Schnittstelle implementiert wird. Der Serialisierungskonstruktor ist erforderlich, um Objekte zu deserialisieren oder neu zu erstellen, die mit der <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>-Methode serialisiert wurden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor. Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keinen Verstoß gegen die Regel. Der Typ ist nicht deserialisierbar und funktioniert in vielen Szenarios nicht.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der die Regel erfüllt.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
