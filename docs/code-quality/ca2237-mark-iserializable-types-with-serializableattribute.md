---
title: 'CA2237: Markieren von ISerializable-Typen mit SerializableAttribute | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9b4c0d05e972b4cf9a84677ccbc7d15d117c3f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Markieren von ISerializable-Typen mit SerializableAttribute
|||  
|-|-|  
|TypeName|MarkISerializableTypesWithSerializable|  
|CheckId|CA2237|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein extern sichtbarer Typ implementiert den <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle und der Typ ist nicht mit markiert die <xref:System.SerializableAttribute?displayProperty=fullName> Attribut. Die Regel ignoriert abgeleitete Typen, dessen Basistyp nicht serialisierbar ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Um die von der common Language Runtime als serialisierbar erkannt werden, müssen mit dem Typen gekennzeichnet werden die <xref:System.SerializableAttribute> Attribut, selbst wenn der Typ eine benutzerdefinierte Serialisierungsroutine Implementierung verwendet die <xref:System.Runtime.Serialization.ISerializable> Schnittstelle.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, gelten die <xref:System.SerializableAttribute> -Attribut auf den Typ.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel für Ausnahmeklassen, da diese ordnungsgemäß funktioniert über Anwendungsdomänen hinweg serialisierbar sein müssen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der die Regel verletzt. Heben Sie die auskommentierung der <xref:System.SerializableAttribute> -Attribut Zeile auf die Regel erfüllen.  
  
 [!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
 [!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)  
  
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)  
  
 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)  
  
 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)  
  
 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)  
  
 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)  
  
 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)