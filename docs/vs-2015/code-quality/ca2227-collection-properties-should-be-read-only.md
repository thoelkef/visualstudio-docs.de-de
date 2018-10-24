---
title: 'CA2227: Auflistungseigenschaften sollten schreibgeschützt sein | Microsoft-Dokumentation'
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
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1db0ab6bae6a374726e953e505247896864c7f0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830443"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Auflistungseigenschaften sollten schreibgeschützt sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine extern sichtbare schreibbare Eigenschaft ist ein Typ, der implementiert <xref:System.Collections.ICollection?displayProperty=fullName>. Arrays, Indexer (Eigenschaften mit dem Namen "Item") und Berechtigungen werden von der Regel ignoriert.

## <a name="rule-description"></a>Regelbeschreibung
 Eine schreibbare Auflistungseigenschaft ermöglicht einen Benutzer, die Auflistung mit einer ganz anderen Sammlung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu. Ersetzen die Auflistung ist ein Ziel, das Entwurfsmuster, das eine Methode, um alle Elemente aus der Auflistung zu entfernen und eine Methode zum erneuten Auffüllen der Auflistung enthalten. Finden Sie unter den <xref:System.Collections.ArrayList.Clear%2A> und <xref:System.Collections.ArrayList.AddRange%2A> Methoden der <xref:System.Collections.ArrayList?displayProperty=fullName> -Klasse für ein Beispiel für dieses Muster.

 Sowohl binäre als auch XML-Serialisierung unterstützt schreibgeschützten Eigenschaften, die Auflistungen darstellen. Die <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> -Klasse verfügt über bestimmte Anforderungen für Typen, die implementieren <xref:System.Collections.ICollection> und <xref:System.Collections.IEnumerable?displayProperty=fullName> um serialisierbar sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie die Eigenschaft schreibgeschützt und wenn der Entwurf es erfordert, fügen Sie Methoden zum Deaktivieren und erneuten Auffüllen der Auflistung hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ mit eine schreibbare Auflistungseigenschaft und zeigt, wie die Auflistung direkt ersetzt werden kann. Darüber hinaus die bevorzugte Weise ersetzen Sie die Eigenschaft für eine schreibgeschützte Auflistung mit `Clear` und `AddRange` Methoden wird angezeigt.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md)



