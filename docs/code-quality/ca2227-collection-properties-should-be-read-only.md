---
title: 'CA2227: Sammlungseigenschaften sollten schreibgeschützt sein.'
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: b6aae7d2f6ed730dc0ac7198a43167dd09976037
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037472"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Sammlungseigenschaften sollten schreibgeschützt sein.

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine extern sichtbare schreibbare Eigenschaft ist ein Typ, der implementiert <xref:System.Collections.ICollection?displayProperty=fullName>. Mit dieser Regel wird ignoriert, Arrays, Indexer (Eigenschaften mit dem Namen "Item") und Berechtigungssätze.

## <a name="rule-description"></a>Regelbeschreibung

Eine schreibbare Auflistungseigenschaft ermöglicht einen Benutzer, die Auflistung mit einer ganz anderen Sammlung zu ersetzen. Eine schreibgeschützte Eigenschaft beendet die Auflistung ersetzt wird, kann jedoch trotzdem die einzelnen Mitglieder festgelegt werden. Ersetzen die Auflistung ist ein Ziel, das Entwurfsmuster bestehend aus einer Methode, um alle Elemente aus der Auflistung zu entfernen und eine Methode, um der Auflistung neu auffüllen. Finden Sie unter den <xref:System.Collections.ArrayList.Clear%2A> und <xref:System.Collections.ArrayList.AddRange%2A> Methoden der <xref:System.Collections.ArrayList?displayProperty=fullName> -Klasse für ein Beispiel für dieses Muster.

Sowohl binäre als auch XML-Serialisierung unterstützt schreibgeschützten Eigenschaften, die Auflistungen darstellen. Die <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> -Klasse verfügt über bestimmte Anforderungen für Typen, die implementieren <xref:System.Collections.ICollection> und <xref:System.Collections.IEnumerable?displayProperty=fullName> um serialisierbar sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die Eigenschaft schreibgeschützt. Wenn der Entwurf es erfordert, fügen Sie Methoden zum Deaktivieren und erneutes Auffüllen der Auflistung hinzu.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Sie können die Warnung unterdrücken, wenn die Eigenschaft Teil ist eine [Data Transfer Object (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10)) Klasse.

Andernfalls, unterdrücken Sie Warnungen, die von dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typ mit eine schreibbare Auflistungseigenschaft und zeigt, wie die Auflistung direkt ersetzt werden kann. Darüber hinaus zeigt die bevorzugte Weise ersetzen Sie die Eigenschaft für eine schreibgeschützte Auflistung mit `Clear` und `AddRange` Methoden.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1819: Eigenschaften sollten keine Arrays zurückgeben.](../code-quality/ca1819-properties-should-not-return-arrays.md)