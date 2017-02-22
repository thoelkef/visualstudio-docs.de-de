---
title: "CA2239: Deserialisierungsmethoden f&#252;r optionale Felder angeben | Microsoft Docs"
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
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
helpviewer_keywords: 
  - "CA2239"
  - "ProvideDeserializationMethodsForOptionalFields"
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2239: Deserialisierungsmethoden f&#252;r optionale Felder angeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideDeserializationMethodsForOptionalFields|  
|CheckId|CA2239|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ verfügt über ein Feld, das mit dem <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName>\-Attribut gekennzeichnet ist, und der Typ gibt keine Methoden für die Deserialisierungsereignisbehandlung an.  
  
## Regelbeschreibung  
 Das <xref:System.Runtime.Serialization.OptionalFieldAttribute>\-Attribut hat keine Auswirkungen auf die Serialisierung. Ein mit dem Attribut gekennzeichnetes Feld wird serialisiert.  Das Feld wird bei der Deserialisierung jedoch ignoriert und behält den seinem Typ zugeordneten Standardwert bei.  Deserialisierungsereignishandler sollten so deklariert werden, dass das Feld während der Deserialisierung festgelegt wird.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie dem Typ Methoden für die Deserialisierungsereignisbehandlung hinzu.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn das Feld während der Deserialisierung ignoriert werden soll.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ mit einem optionalen Feld und Methoden für die Deserialisierungsereignisbehandlung veranschaulicht.  
  
 [!code-cs[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]  
  
## Verwandte Regeln  
 [CA2236: Basisklassenmethoden auf ISerializable\-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2237: Markieren von ISerializable\-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)