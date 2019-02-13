---
title: Attribute (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ec27fe2d7824ca32cbf97dbabac8b7ea6c4aed6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948497"
---
# <a name="attribute-xelement-dynamic-property"></a>Attribute (dynamische XElement-Eigenschaft)

Sucht nach einem Indexer, der zum Abrufen der Attributinstanz verwendet wird, die dem angegebenen erweiterten Namen entspricht.

## <a name="syntax"></a>Syntax

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Indexer des Typs `XAttribute Item(String expandedName)`. Dieser Indexer nimmt den erweiterten Namen des angegebenen Attributs und gibt das zugehörige <xref:System.Xml.Linq.XAttribute> zurück. Wenn kein Attribut mit dem angegebenen Namen existiert, wird `null` zurückgegeben.

## <a name="remarks"></a>Hinweise

Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XElement.Attribute%2A>-Methode der <xref:System.Xml.Linq.XElement?displayProperty=fullName>-Klasse.

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)
- [Wert](../designers/value-xattribute-dynamic-property.md)