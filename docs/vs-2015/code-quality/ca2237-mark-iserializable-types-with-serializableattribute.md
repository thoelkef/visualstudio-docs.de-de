---
title: 'CA2237: Markieren von ISerializable-Typen mit SerializableAttribute | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 10a8fa5300241326f2af5df847974644bd4fe0d7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201486"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Markieren von ISerializable-Typen mit SerializableAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> -Schnittstelle und der Typ ist nicht mit markiert die <xref:System.SerializableAttribute?displayProperty=fullName> Attribut. Die Regel ignoriert die abgeleitete Typen, dessen Basistyp nicht serialisierbar ist.

## <a name="rule-description"></a>Regelbeschreibung
 Um die von der common Language Runtime als serialisierbar erkannt werden, müssen Typen mit markiert werden die <xref:System.SerializableAttribute> Attribut, selbst wenn der Typ durch die Implementierung der eine benutzerdefinierte Serialisierungsroutine verwendet die <xref:System.Runtime.Serialization.ISerializable> Schnittstelle.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden die <xref:System.SerializableAttribute> -Attribut auf den Typ.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel für Ausnahmeklassen nicht, da diese über Anwendungsdomänen hinweg ordnungsgemäße serialisierbar sein müssen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. Heben Sie die auskommentierung der <xref:System.SerializableAttribute> Attribut Zeile in der Regel entsprechen.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)



