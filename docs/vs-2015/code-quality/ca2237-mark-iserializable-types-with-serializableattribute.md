---
title: 'CA2237: Markieren von iserialisierbaren Typen mit SerializableAttribute | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d8778b0bfa035c782cf35d205fc59d463112196c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545157"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: ISerializable-Typen mit SerializableAttribute markieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> -Schnittstelle, und der Typ ist nicht mit dem- <xref:System.SerializableAttribute?displayProperty=fullName> Attribut gekennzeichnet. Die Regel ignoriert abgeleitete Typen, deren Basistyp nicht serialisierbar ist.

## <a name="rule-description"></a>Beschreibung der Regel
 Um vom Common Language Runtime als serialisierbar erkannt zu werden, müssen die Typen mit dem-Attribut markiert werden, <xref:System.SerializableAttribute> auch wenn der Typ durch die Implementierung der-Schnittstelle eine benutzerdefinierte Serialisierungsroutine verwendet <xref:System.Runtime.Serialization.ISerializable> .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, wenden <xref:System.SerializableAttribute> Sie das-Attribut auf den Typ an.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel nicht für Ausnahme Klassen, da sie serialisierbar sein müssen, damit Sie über Anwendungs Domänen hinweg ordnungsgemäß funktioniert.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt. Kommentieren Sie die <xref:System.SerializableAttribute> Attribut Zeile aus, um die Regel zu erfüllen.

 [!code-csharp[FxCop.Usage.MarkSerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/cs/FxCop.Usage.MarkSerializable.cs#1)]
 [!code-vb[FxCop.Usage.MarkSerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.MarkSerializable/vb/FxCop.Usage.MarkSerializable.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable ordnungsgemäß implementieren.](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serialisierungsmethoden korrekt implementieren.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Alle nicht serialisierbaren Felder markieren.](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2239: Deserialisierungsmethoden für optionale Felder angeben.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren.](../code-quality/ca2120-secure-serialization-constructors.md)
