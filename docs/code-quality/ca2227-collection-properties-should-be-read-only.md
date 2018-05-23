---
title: 'CA2227: Auflistungseigenschaften sollten schreibgeschützt sein'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: aa1d8644049f78eccfda7402360bdbc930b61601
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Auflistungseigenschaften sollten schreibgeschützt sein

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine extern sichtbare schreibbare Eigenschaft ist ein Typ, der implementiert <xref:System.Collections.ICollection?displayProperty=fullName>. Mit dieser Regel wird ignoriert, Arrays, Indexer (Eigenschaften mit dem Namen "Item") und Berechtigungssätze.

## <a name="rule-description"></a>Regelbeschreibung

Eine schreibbare Auflistungseigenschaft ermöglicht einem Benutzer auf die Auflistung durch eine vollkommen andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft der Sammlung ersetzt wird beendet, lässt aber dennoch das Festlegen einzelner Member zu werden. Ersetzen die Auflistung ist ein Ziel, das Entwurfsmuster, z. B. eine Methode, um alle Elemente aus der Auflistung entfernt und eine Methode, um der Auflistung neu auffüllen. Finden Sie unter der <xref:System.Collections.ArrayList.Clear%2A> und <xref:System.Collections.ArrayList.AddRange%2A> Methoden die <xref:System.Collections.ArrayList?displayProperty=fullName> Klasse für ein Beispiel für dieses Muster.

Binär- und XML-Serialisierung unterstützen schreibgeschützten Eigenschaften, die Auflistungen sind. Die <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Klasse gelten bestimmte Anforderungen für Typen, die implementieren <xref:System.Collections.ICollection> und <xref:System.Collections.IEnumerable?displayProperty=fullName> um serialisierbar sein.

## <a name="how-to-fix-violations"></a>Behandlung von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die Eigenschaft schreibgeschützt. Wenn der Entwurf erforderlich ist, fügen Sie Methoden zum Deaktivieren und erneut Auffüllen der auflistungs hinzu.

## <a name="when-to-suppress-warnings"></a>Wenn Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt einen Typen mit eine schreibbare Auflistungseigenschaft und zeigt, wie die Auflistung direkt ersetzt werden kann. Darüber hinaus die bevorzugte Methode des Ersetzens Eigenschaft für eine schreibgeschützte Auflistung mit `Clear` und `AddRange` Methoden wird angezeigt.

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md)