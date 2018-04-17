---
title: 'CA2227: Auflistungseigenschaften sollten schreibgeschützt sein | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
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
ms.workload:
- multiple
ms.openlocfilehash: 0884b2fc15a08584052fb69dca9980964b2fd374
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Auflistungseigenschaften sollten schreibgeschützt sein
|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine extern sichtbare schreibbare Eigenschaft ist ein Typ, der implementiert <xref:System.Collections.ICollection?displayProperty=fullName>. Arrays, Indexer (Eigenschaften mit dem Namen "Item") und Berechtigungssätze werden von der Regel ignoriert.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Eine schreibbare Auflistungseigenschaft ermöglicht einem Benutzer auf die Auflistung durch eine vollkommen andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu. Ersetzen die Auflistung ist ein Ziel, das Entwurfsmuster, eine Methode, um alle Elemente aus der Auflistung zu entfernen und eine Methode zum erneuten Auffüllen der Auflistung enthalten. Finden Sie unter der <xref:System.Collections.ArrayList.Clear%2A> und <xref:System.Collections.ArrayList.AddRange%2A> Methoden die <xref:System.Collections.ArrayList?displayProperty=fullName> Klasse für ein Beispiel für dieses Muster.  
  
 Binär- und XML-Serialisierung unterstützen schreibgeschützten Eigenschaften, die Auflistungen sind. Die <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> Klasse gelten bestimmte Anforderungen für Typen, die implementieren <xref:System.Collections.ICollection> und <xref:System.Collections.IEnumerable?displayProperty=fullName> um serialisierbar sein.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, machen Sie die Eigenschaft schreibgeschützt, und wenn der Entwurf erforderlich ist, fügen Sie Methoden zum Löschen und erneuten Auffüllen der Auflistung.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typen mit eine schreibbare Auflistungseigenschaft und zeigt, wie die Auflistung direkt ersetzt werden kann. Darüber hinaus die bevorzugte Methode des Ersetzens Eigenschaft für eine schreibgeschützte Auflistung mit `Clear` und `AddRange` Methoden wird angezeigt.  
  
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md)