---
title: 'CA2240: iserialisierbares Element ordnungsgemäß implementieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 217f95b7d3658db107fc482040686eea9ee47604
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543662"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: ISerializable ordnungsgemäß implementieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ kann der <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> -Schnittstelle zugewiesen werden, und eine der folgenden Bedingungen ist erfüllt:

- Der Typ erbt <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> , überschreibt die-Methode jedoch nicht, und der Typ deklariert Instanzfelder, die nicht mit dem-Attribut markiert sind <xref:System.NonSerializedAttribute?displayProperty=fullName> .

- Der Typ ist nicht versiegelt, und der Typ implementiert eine <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode, die nicht extern sichtbar und über schreibbar ist.

## <a name="rule-description"></a>Beschreibung der Regel
 Instanzfelder, die in einem Typ deklariert werden, der die-Schnittstelle erbt, <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> werden nicht automatisch in den Serialisierungsprozess eingeschlossen. Um die Felder einzuschließen, muss der Typ die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode und den Serialisierungskonstruktor implementieren. Wenn die Felder nicht serialisiert werden sollen, wenden Sie das- <xref:System.NonSerializedAttribute> Attribut auf die Felder an, um die Entscheidung explizit anzugeben.

 In nicht versiegelten Typen sollten Implementierungen der- <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode extern sichtbar sein. Daher kann die-Methode von abgeleiteten Typen aufgerufen werden und ist über schreibbar.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, machen <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Sie die Methode sichtbar und über schreibbar, und stellen Sie sicher, dass alle Instanzfelder in den Serialisierungsprozess eingeschlossen oder explizit mit dem-Attribut markiert sind <xref:System.NonSerializedAttribute> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei serialisierbare Typen, die gegen die Regel verstoßen.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die beiden vorherigen Verstöße korrigiert, indem eine über schreibbare Implementierung von [iserialisierung. GetObjectData] bereitgestellt wird (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) für die Book-Klasse und durch Bereitstellen einer Implementierung von <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> in der Library-Klasse.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serialisierungsmethoden korrekt implementieren.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Alle nicht serialisierbaren Felder markieren.](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Deserialisierungsmethoden für optionale Felder angeben.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren.](../code-quality/ca2120-secure-serialization-constructors.md)
