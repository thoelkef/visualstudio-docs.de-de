---
title: "CA2235: Alle nicht serialisierbaren Felder markieren | Microsoft Docs"
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
  - "CA2235"
  - "MarkAllNonSerializableFields"
helpviewer_keywords: 
  - "CA2235"
  - "MarkAllNonSerializableFields"
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2235: Alle nicht serialisierbaren Felder markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert.  
  
## Regelbeschreibung  
 Ein serialisierbarer Typ wird mit dem <xref:System.SerializableAttribute?displayProperty=fullName>\-Attribut markiert.  Wenn der Typ serialisiert ist, wird eine <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName>\-Ausnahme ausgelöst, falls ein Typ ein Instanzenfeld eines nicht serialisierbaren Typs enthält.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie das <xref:System.NonSerializedAttribute?displayProperty=fullName>\-Attribut auf das nicht serialisierbare Feld an.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie nur dann eine Warnung dieser Regel, wenn ein <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName>\-Typ deklariert wird, der die Serialisierung und Deserialisierung von Instanzen des Felds zulässt.  
  
## Beispiel  
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt, und einen Typ, der der Regel entspricht.  
  
 [!code-cs[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## Verwandte Regeln  
 [CA2236: Basisklassenmethoden auf ISerializable\-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: Markieren von ISerializable\-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)