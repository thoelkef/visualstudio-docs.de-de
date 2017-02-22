---
title: "CA2238: Serialisierungsmethoden korrekt implementieren | Microsoft Docs"
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
  - "ImplementSerializationMethodsCorrectly"
  - "CA2238"
helpviewer_keywords: 
  - "CA2238"
  - "ImplementSerializationMethodsCorrectly"
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2238: Serialisierungsmethoden korrekt implementieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementSerializationMethodsCorrectly|  
|CheckId|CA2238|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Unterbrechend – Wenn die Methode außerhalb der Assembly sichtbar ist.<br /><br /> Nicht unterbrechend – Wenn die Methode nicht außerhalb der Assembly sichtbar ist.|  
  
## Ursache  
 Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit.  
  
## Regelbeschreibung  
 Einer Methode wird ein Serialisierungsereignishandler zugewiesen, indem eines der folgenden Serialisierungsereignisattribute angewendet wird:  
  
-   <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>  
  
-   <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>  
  
 Serialisierungsereignishandler nehmen einen einzelnen Parameter des Typs <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> an, geben `void` zurück, und haben `private`\-Sichtbarkeit.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, den Rückgabetyp oder die Sichtbarkeit des Serialisierungsereignishandlers.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt ordnungsgemäß deklarierte Serialisierungsereignishandler.  
  
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
 [!code-cs[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]  
  
## Verwandte Regeln  
 [CA2236: Basisklassenmethoden auf ISerializable\-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Markieren von ISerializable\-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)