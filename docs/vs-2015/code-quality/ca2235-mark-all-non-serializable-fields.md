---
title: 'CA2235: alle nicht serialisierbaren Felder markieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fab79fd4daab98c6cade9271b32c45b5ae4b4332
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545196"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Alle nicht serialisierbaren Felder markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Instanzenfeld eines Typs, der nicht serialisierbar ist, ist in einem serialisierbaren Typ deklariert.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein serialisierbarer Typ ist ein Typ, der mit dem-Attribut markiert ist <xref:System.SerializableAttribute?displayProperty=fullName> . Wenn der Typ serialisiert wird, wird eine-Ausnahme ausgelöst, <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> Wenn ein Typ ein Instanzfeld eines Typs enthält, der nicht serialisierbar ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden <xref:System.NonSerializedAttribute?displayProperty=fullName> Sie das-Attribut auf das Feld an, das nicht serialisierbar ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt nur eine Warnung aus dieser Regel, wenn ein <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> Typ deklariert wird, mit dem Instanzen des Felds serialisiert und deserialisiert werden können.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt, und einen Typ, der die Regel erfüllt.

 [!code-csharp[FxCop.Usage.MarkNonSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/cs/FxCop.Usage.MarkNonSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkNonSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkNonSerializable/vb/FxCop.Usage.MarkNonSerializable.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable ordnungsgemäß implementieren.](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serialisierungsmethoden korrekt implementieren.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Deserialisierungsmethoden für optionale Felder angeben.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren.](../code-quality/ca2120-secure-serialization-constructors.md)
