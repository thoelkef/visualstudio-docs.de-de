---
title: "CA2240: ISerializable ordnungsgem&#228;&#223; implementieren | Microsoft Docs"
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
  - "CA2240"
  - "ImplementISerializableCorrectly"
helpviewer_keywords: 
  - "CA2240"
  - "ImplementISerializableCorrectly"
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2240: ISerializable ordnungsgem&#228;&#223; implementieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementISerializableCorrectly|  
|CheckId|CA2240|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein extern sichtbarer Typ kann der <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>\-Schnittstelle zugewiesen werden, und eine der folgenden Bedingungen trifft zu:  
  
-   Der Typ erbt die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>\-Methode, überschreibt sie aber nicht, und der Typ deklariert Instanzenfelder, die nicht mit dem <xref:System.NonSerializedAttribute?displayProperty=fullName>\-Attribut markiert sind.  
  
-   Der Typ ist nicht versiegelt und implementiert eine <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode, die nicht extern sichtbar und überschreibbar ist.  
  
## Regelbeschreibung  
 Instanzenfelder, die in einem Typ deklariert werden, der die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>\-Schnittstelle erbt, werden nicht automatisch in den Serialisierungsvorgang aufgenommen.  Damit die Felder aufgenommen werden, muss der Typ die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode und den Serialisierungskonstruktor implementieren.  Wenn die Felder nicht serialisiert werden sollen, weisen Sie den Feldern das Attribut <xref:System.NonSerializedAttribute> zu, um diese Entscheidung explizit anzugeben.  
  
 In nicht versiegelten Typen sollten Implementierungen der <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode extern sichtbar sein.  Deshalb kann die Methode von abgeleiteten Typen aufgerufen werden und ist überschreibbar.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie sicher, dass die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A>\-Methode sichtbar und überschreibbar ist und dass alle Instanzenfelder in den Serialisierungsprozess einbezogen werden oder explizit mit dem <xref:System.NonSerializedAttribute>\-Attribut markiert sind.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei serialisierbare Typen veranschaulicht, die gegen die Regel verstoßen.  
  
 [!code-cs[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]  
  
## Beispiel  
 Im folgenden Beispiel werden die zwei zuvor dargestellten Verstöße korrigiert, indem eine überschreibbare Implementierung von [ISerializable.GetObjectData](assetId:///ISerializable.GetObjectData?qualifyHint=False&autoUpgrade=False) in der Book\-Klasse und eine Implementierung von assetId:///ISerializable.GetObjectData?qualifyHint=False&autoUpgrade=False in der Library\-Klasse bereitgestellt werden.  
  
 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
 [!code-cs[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]  
  
## Verwandte Regeln  
 [CA2236: Basisklassenmethoden auf ISerializable\-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Markieren von ISerializable\-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)