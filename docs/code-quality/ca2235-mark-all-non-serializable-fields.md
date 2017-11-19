---
title: 'CA2235: Alle nicht serialisierbaren Felder markieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b6489cf400dd2f67c08ff4dba3bf6a1eda4ec46e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Alle nicht serialisierbaren Felder markieren
|||  
|-|-|  
|TypeName|MarkAllNonSerializableFields|  
|CheckId|CA2235|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Ein serialisierbarer Typ ist eine, die mit der <xref:System.SerializableAttribute?displayProperty=fullName> Attribut. Wenn der Typ serialisiert wird, eine <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> Ausnahme wird ausgelöst, wenn ein Typ ein Instanzenfeld eines Typs enthält, die nicht serialisierbar ist.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, gelten die <xref:System.NonSerializedAttribute?displayProperty=fullName> -Attribut auf das Feld, das nicht serialisierbar ist.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn eine <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> Typ wird deklariert, mit der Instanzen des Felds, das serialisiert und deserialisiert werden.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird ein Typ, der die Regel verletzt und ein Typ, der die Regel erfüllt.  
  
 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)  
  
 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)