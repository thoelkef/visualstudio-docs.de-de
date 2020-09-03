---
title: 'CA2236: Basisklassen Methoden für iserialisierbare Typen abrufen | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a03192ac8a5b59558dc39a32f55e8177dc249365
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545183"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ wird von einem Typ abgeleitet, der die <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> -Schnittstelle implementiert, und eine der folgenden Bedingungen ist erfüllt:

- Der-Typ implementiert den Serialisierungskonstruktor, d. h. einen Konstruktor mit der- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> Parameter Signatur, ruft jedoch nicht den Serialisierungskonstruktor des Basistyps auf.

- Der-Typ implementiert die- <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> Methode, ruft jedoch nicht die- <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode des Basistyps auf.

## <a name="rule-description"></a>Beschreibung der Regel
 Bei einem benutzerdefinierten Serialisierungsprozess implementiert ein Typ die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> -Methode, um seine Felder zu serialisieren, und der Serialisierungskonstruktor, um die Felder zu deserialisieren. Wenn der Typ von einem Typ abgeleitet wird, der die- <xref:System.Runtime.Serialization.ISerializable> Schnittstelle implementiert, sollten die Basistyp <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode und der Serialisierungskonstruktor aufgerufen werden, um die Felder des Basistyps zu serialisieren/deserialisieren. Andernfalls wird der Typ nicht serialisiert und deserialisiert. Beachten Sie Folgendes: Wenn der abgeleitete Typ keine neuen Felder hinzufügt, muss der Typ weder die <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode noch den Serialisierungskonstruktor implementieren oder die Basistyp Entsprechungen aufzurufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die Basistyp <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode oder den Serialisierungskonstruktor von der entsprechenden abgeleiteten Typmethode oder dem entsprechenden Konstruktor aufzurufen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird ein abgeleiteter Typ gezeigt, der die Regel erfüllt, indem der Serialisierungskonstruktor und die- <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Methode der Basisklasse aufgerufen werden.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2240: ISerializable ordnungsgemäß implementieren.](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Serialisierungsmethoden korrekt implementieren.](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Alle nicht serialisierbaren Felder markieren.](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Deserialisierungsmethoden für optionale Felder angeben.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren.](../code-quality/ca2120-secure-serialization-constructors.md)
