---
title: 'CA2120: Sichere Serialisierungskonstruktoren | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0032e2a20c90d11db33c94397e8c8b8cadbd86db
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Sichere Serialisierungskonstruktoren
|||  
|-|-|  
|TypeName|SecureSerializationConstructors|  
|CheckId|CA2120|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Der Typ implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> -Schnittstelle, ist kein Delegat oder Schnittstelle, und wird in einer Assembly, die teilweise vertrauenswürdige Aufrufer zulässt deklariert. Der Typ verfügt über einen Konstruktor, akzeptiert eine <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> Objekt und ein <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Objekt (die Signatur des Serialisierungskonstruktors). Dieser Konstruktor ist nicht durch eine sicherheitsüberprüfung gesichert, aber eine oder mehrere der normalen Konstruktoren im Typ geschützt ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel ist relevant für Typen, die benutzerdefinierte Serialisierung unterstützen. Ein Typ unterstützt die benutzerdefinierte Serialisierung, wenn er implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle. Der Serialisierungskonstruktor ist erforderlich und wird verwendet, um deserialisiert werden, oder erstellen Sie erneut die Objekte, die mit serialisiert wurden die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> Methode. Da der Serialisierungskonstruktor belegt und Objekte initialisiert werden, müssen sicherheitsüberprüfungen, die auf normalen Konstruktoren vorhanden sind, auch auf den Serialisierungskonstruktor vorhanden sein. Wenn Sie diese Regel verletzen, konnte Aufrufern, die andernfalls keine Instanz erstellt werden konnte zu diesem Zweck den Serialisierungskonstruktor verwenden.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, schützen Sie den Serialisierungskonstruktor mit sicherheitsforderungen, die mit den anderen Konstruktoren schützen identisch sind.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keinen Verstoß gegen diese Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt.  
  
 [!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>