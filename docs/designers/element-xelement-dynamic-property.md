---
title: Element (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 08b2f7f008c1522c5f65b5ee7a58c3ed98e8a845
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637323"
---
# <a name="element-xelement-dynamic-property"></a>Element (dynamische XElement-Eigenschaft)

Ermittelt einen Indexer, der zum Abrufen der Instanz des untergeordneten Elements verwendet wird, die dem angegebenen erweiterten Namen entspricht.

## <a name="syntax"></a>Syntax

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Indexer des Typs `XElement Item(String expandedName)`. Dieser Indexer nimmt einen erweiterten Namensparameter und gibt das zugehörige <xref:System.Xml.Linq.XElement> oder, wenn kein Element mit dem angegebenen Namen existiert, `null` zurück.

## <a name="remarks"></a>Anmerkungen

Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XContainer.Element%2A>-Methode der <xref:System.Xml.Linq.XContainer?displayProperty=fullName>-Klasse.

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Dynamische Eigenschaften der XElement-Klasse](../designers/attribute-xelement-dynamic-property.md)
- [Elemente](../designers/elements-xelement-dynamic-property.md)