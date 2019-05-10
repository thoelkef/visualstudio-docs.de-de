---
title: 'CA2236: Aufrufen von Basisklassenmethoden auf ISerializable-Typen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4ec8c14da5c691f6f9740c6df86cb38aeb9fac5e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60057640"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ abgeleitet wird, von einem Typ, der implementiert die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> Schnittstelle und eine der folgenden Bedingungen zutrifft:

- Der Typ implementiert den Serialisierungskonstruktor, d. h. einen Konstruktor mit der <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Parametersignatur, aber nicht den Serialisierungskonstruktor des Basistyps aufgerufen wird.

- Der Typ implementiert die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> Methode jedoch nicht auf die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode des Basistyps.

## <a name="rule-description"></a>Regelbeschreibung
 In einem Prozess benutzerdefinierte Serialisierung, ein Typ implementiert die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode, um die Felder und den Serialisierungskonstruktor deserialisiert die Felder serialisiert werden sollen. Wenn der Typ von einem Typ abgeleitet wird, implementiert die <xref:System.Runtime.Serialization.ISerializable> Schnittstelle, die den Basistyp <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode und der Serialisierungskonstruktor aufgerufen werden soll, zu serialisieren/Deserialisieren die Felder des Basistyps. Andernfalls, der Typ wird nicht werden serialisiert und deserialisiert ordnungsgemäß. Beachten Sie, dass wenn der abgeleitete Typ keine neuen Felder hinzugefügt wird, der Typ nicht zum Implementieren notwendigerweise der <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode noch den Serialisierungskonstruktor oder rufen Sie die Entsprechungen für Basistyp.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie den Basistyp <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode oder den Serialisierungskonstruktor Konstruktor aus der entsprechenden abgeleiteten Typmethode oder -Konstruktor.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen abgeleiteten Typ, der die Regel entspricht, durch Aufrufen des Serialisierungskonstruktors und <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode der Basisklasse.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2240: ISerializable ordnungsgemäß implementieren](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serialisierungskonstruktoren implementieren](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serialisierungsmethoden korrekt implementieren](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Alle nicht serialisierbaren Felder markieren](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Markieren von ISerializable-Typen mit SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Deserialisierungsmethoden für optionale Felder angeben](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren](../code-quality/ca2120-secure-serialization-constructors.md)
