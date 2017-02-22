---
title: "CA2237: Markieren von ISerializable-Typen mit SerializableAttribute | Microsoft Docs"
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
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
helpviewer_keywords: 
  - "CA2237"
  - "MarkISerializableTypesWithSerializable"
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2237: Markieren von ISerializable-Typen mit SerializableAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein extern sichtbarer Typ implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>\-Schnittstelle, der Typ ist jedoch nicht mit dem <xref:System.SerializableAttribute?displayProperty=fullName>\-Attribut markiert.  Abgeleitete Typen, deren Basistyp nicht serialisierbar ist, werden von der Regel ignoriert.  
  
## Regelbeschreibung  
 Damit Typen von der Common Language Runtime als serialisierbar erkannt werden, müssen sie mit dem <xref:System.SerializableAttribute>\-Attribut markiert werden, auch wenn der Typ durch die Implementierung der <xref:System.Runtime.Serialization.ISerializable>\-Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie das <xref:System.SerializableAttribute>\-Attribut auf den Typ an.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie bei Ausnahmeklassen keine Warnung dieser Regel, da diese Klassen serialisierbar sein müssen, wenn sie in verschiedenen Anwendungsdomänen einwandfrei funktionieren sollen.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  Heben Sie die Auskommentierung der <xref:System.SerializableAttribute>\-Attributzeile auf, damit die Regel erfüllt wird.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-cs[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## Verwandte Regeln  
 [CA2236: Basisklassenmethoden auf ISerializable\-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)