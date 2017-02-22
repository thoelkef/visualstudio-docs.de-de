---
title: "CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen | Microsoft Docs"
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
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
helpviewer_keywords: 
  - "CA2236"
  - "CallBaseClassMethodsOnISerializableTypes"
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallBaseClassMethodsOnISerializableTypes|  
|CheckId|CA2236|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ wird von einem Typ abgeleitet, der die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>\-Schnittstelle implementiert, und eine der folgenden Bedingungen ist erfüllt:  
  
-   Der Typ implementiert den Serialisierungskonstruktor, d. h. einen Konstruktor mit der <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>\-Parametersignatur, ruft jedoch nicht den Serialisierungskonstruktor des Basistyps auf.  
  
-   Der Typ implementiert die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>\-Methode, ruft jedoch die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode des Basistyps nicht auf.  
  
## Regelbeschreibung  
 In einem benutzerdefinierten Serialisierungsprozess implementiert ein Typ die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode, um seine Felder zu serialisieren, sowie den Serialisierungskonstruktor, um die Felder zu deserialisieren.  Wenn der Typ von einem Typ abgeleitet wird, der die <xref:System.Runtime.Serialization.ISerializable>\-Schnittstelle implementiert, sollten die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode und der Serialisierungskonstruktor des Basistyps aufgerufen werden, um die Felder des Basistyps zu serialisieren\/deserialisieren.  Andernfalls wird der Typ nicht ordnungsgemäß serialisiert und deserialisiert.  Wenn der abgeleitete Typ keine neuen Felder hinzufügt, muss der Typ weder die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode noch den Serialisierungskonstruktor implementieren und auch keine Entsprechungen des Basistyps aufrufen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode oder den Serialisierungskonstruktor des Basistyps in der Methode oder dem Konstruktor des entsprechenden abgeleiteten Typs auf.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt einen abgeleiteten Typ, der der Regel entspricht, da der Serialisierungskonstruktor und die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode der Basisklasse aufgerufen werden.  
  
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-cs[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]  
  
## Verwandte Regeln  
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Markieren von ISerializable\-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)