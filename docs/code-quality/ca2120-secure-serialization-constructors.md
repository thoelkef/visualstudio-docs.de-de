---
title: "CA2120: Sichere Serialisierungskonstruktoren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2120"
  - "SecureSerializationConstructors"
helpviewer_keywords: 
  - "CA2120"
  - "SecureSerializationConstructors"
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2120: Sichere Serialisierungskonstruktoren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecureSerializationConstructors|  
|CheckId|CA2120|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Typ implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>\-Schnittstelle, ist kein Delegat und keine Schnittstelle, und ist in einer Assembly deklariert, in der nicht voll vertrauenswürdige Aufrufer zulässig sind.  Der Typ weist einen Konstruktor auf, der neben dem <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>\-Objekt auch das <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>\-Objekt \(die Signatur des Serialisierungskonstruktors\) annimmt.  Dieser Konstruktor ist nicht durch eine Sicherheitsüberprüfung gesichert. Dagegen ist mindestens einer der normalen Konstruktoren des Typs gesichert.  
  
## Regelbeschreibung  
 Diese Regel ist relevant für Typen, die die benutzerdefinierte Serialisierung unterstützen.  Ein Typ unterstützt benutzerdefinierte Serialisierung, wenn durch ihn die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>\-Schnittstelle implementiert wird.  Der Serialisierungskonstruktor ist erforderlich und wird eingesetzt für die Deserialisierung oder Neuerstellung von Objekten, die mit der <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>\-Methode serialisiert wurden.  Der Serialisierungskonstruktor ordnet Objekte zu und initialisiert sie. Sicherheitsüberprüfungen, die bei normalen Konstruktoren durchgeführt werden, müssen deshalb auch bei Serialisierungskonstruktoren durchgeführt werden.  Bei einem Verstoß gegen diese Regel könnten Aufrufer, die auf andere Weise keine Instanz erstellen konnten, den Serialisierungskonstruktor dazu verwenden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, schützen Sie den Serialisierungskonstruktor mit den gleichen Sicherheitsanforderungen wie die anderen Konstruktoren.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keinen Verstoß gegen diese Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  
  
 [!code-cs[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]  
  
## Verwandte Regeln  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2237: Markieren von ISerializable\-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## Siehe auch  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>