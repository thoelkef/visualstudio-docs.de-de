---
title: 'CA2227: Sammlungs Eigenschaften sollten schreibgeschützt sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 17c4e2336a5c8bd8905d857dc8189a11f9fb6181
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540529"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Sammlungseigenschaften sollten schreibgeschützt sein.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine extern sichtbare beschreibbare Eigenschaft ist ein Typ, der implementiert <xref:System.Collections.ICollection?displayProperty=fullName> . Arrays, Indexer (Eigenschaften mit dem Namen "Item") und Berechtigungs Sätze werden von der Regel ignoriert.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine beschreibbare Auflistungs Eigenschaft ermöglicht es einem Benutzer, die Sammlung durch eine vollkommen andere Auflistung zu ersetzen. Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu. Wenn das Ersetzen der Auflistung ein Ziel ist, besteht das bevorzugte Entwurfsmuster darin, eine Methode zum Entfernen aller Elemente aus der Auflistung und eine Methode zum erneuten Auffüllen der Auflistung einzuschließen. Ein Beispiel für dieses Muster finden Sie unter den <xref:System.Collections.ArrayList.Clear%2A> -und- <xref:System.Collections.ArrayList.AddRange%2A> Methoden der- <xref:System.Collections.ArrayList?displayProperty=fullName> Klasse.

 Sowohl die binäre als auch die XML-Serialisierung unterstützen schreibgeschützte Eigenschaften, die Sammlungen sind. Die <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> -Klasse verfügt über bestimmte Anforderungen für Typen, die implementieren, <xref:System.Collections.ICollection> und <xref:System.Collections.IEnumerable?displayProperty=fullName> , um serialisierbar zu sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie die-Eigenschaft als schreibgeschützt fest, und wenn der Entwurf dies erfordert, fügen Sie Methoden hinzu, um die Auflistung zu löschen und erneut aufzufüllen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ mit einer beschreibbaren Auflistungs Eigenschaft und zeigt, wie die Auflistung direkt ersetzt werden kann. Außerdem wird die bevorzugte Art, eine schreibgeschützte Auflistungs Eigenschaft mithilfe von `Clear` -und-Methoden zu ersetzen, `AddRange` angezeigt.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1819: Eigenschaften sollten keine Arrays zurückgeben.](../code-quality/ca1819-properties-should-not-return-arrays.md)
