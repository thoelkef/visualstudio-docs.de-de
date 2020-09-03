---
title: 'CA2238: Serialisierungsmethoden ordnungsgemäß implementieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 98e825fd5543b928569b99218c9054aff666e0fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545144"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Serialisierungsmethoden korrekt implementieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA2238: Implementieren Sie Serialisierungsmethoden ordnungsgemäß](/visualstudio/code-quality/ca2238-implement-serialization-methods-correctly).

|Element|value|
|-|-|
|TypName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Unterbrechung: Wenn die Methode außerhalb der Assembly sichtbar ist.<br /><br /> Nicht unterbrechend: Wenn die Methode außerhalb der Assembly nicht sichtbar ist.|

## <a name="cause"></a>Ursache
 Eine Methode, die ein Serialisierungsereignis behandelt, verfügt nicht über die richtige Signatur, den richtigen Rückgabetyp oder die richtige Sichtbarkeit.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine Methode wird als Serialisierungsereignishandler festgelegt, indem eines der folgenden Serialisierungsereignisattribute angewendet wird:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Serialisierungsereignishandler verwenden einen einzelnen Parameter vom Typ <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> , geben zurück `void` und haben `private` Sichtbarkeit.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Signatur, den Rückgabetyp oder die Sichtbarkeit des Serialisierungsereignishandlers.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt korrekt deklarierte Serialisierungsereignis-Handler.

 [!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/cs/FxCop.Usage.SerializationEventHandlers.cs#1)]
 [!code-vb[FxCop.Usage.SerializationEventHandlers#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.SerializationEventHandlers/vb/FxCop.Usage.SerializationEventHandlers.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2236: Basisklassenmethoden auf ISerializable-Typen aufrufen.](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: ISerializable ordnungsgemäß implementieren.](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Serialisierungskonstruktoren implementieren.](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2235: Alle nicht serialisierbaren Felder markieren.](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: ISerializable-Typen mit SerializableAttribute markieren.](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Deserialisierungsmethoden für optionale Felder angeben.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Sichere Serialisierungskonstruktoren.](../code-quality/ca2120-secure-serialization-constructors.md)
