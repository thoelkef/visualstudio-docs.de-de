---
title: "CA2229: Serialisierungskonstruktoren implementieren | Microsoft Docs"
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
  - "CA2229"
  - "ImplementSerializationConstructors"
helpviewer_keywords: 
  - "CA2229"
  - "ImplementSerializationConstructors"
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2229: Serialisierungskonstruktoren implementieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationConstructors|  
|CheckId|CA2229|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Der Typ implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>\-Schnittstelle, ist kein Delegat bzw. keine Schnittstelle, und eine der folgenden Bedingungen ist erfüllt:  
  
-   Der Typ verfügt über keinen Konstruktor, der ein <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>\-Objekt und ein <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>\-Objekt \(die Signatur des Serialisierungskonstruktors\) annimmt.  
  
-   Der Typ ist unversiegelt, und der Zugriffsmodifizierer für seinen Serialisierungskonstruktor ist nicht geschützt \(Familie\).  
  
-   Der Typ ist versiegelt, und der Zugriffsmodifizierer für seinen Serialisierungskonstruktor ist nicht privat.  
  
## Regelbeschreibung  
 Diese Regel ist relevant für Typen, die die benutzerdefinierte Serialisierung unterstützen.  Ein Typ unterstützt benutzerdefinierte Serialisierung, wenn durch ihn die <xref:System.Runtime.Serialization.ISerializable>\-Schnittstelle implementiert wird.  Der Serialisierungskonstruktor wird benötigt, um Objekte zu deserialisieren oder neu zu erstellen, die mit der <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>\-Methode serialisiert wurden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Serialisierungskonstruktor.  Definieren Sie den Konstruktor bei einer versiegelten Klasse als privaten Konstruktor. Definieren Sie ihn andernfalls als geschützten Konstruktor.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keinen Verstoß gegen diese Regel.  Der Typ ist dann nämlich nicht deserialisierbar und funktioniert in vielen Szenarien nicht.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der der Regel entspricht.  
  
 [!code-cs[FxCop.Usage.ISerializableCtor#1](../code-quality/codesnippet/CSharp/ca2229-implement-serialization-constructors_1.cs)]  
  
## Verwandte Regeln  
 [CA2237: Markieren von ISerializable\-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
## Siehe auch  
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>   
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>