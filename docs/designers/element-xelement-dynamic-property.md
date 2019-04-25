---
title: Element (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dbd197082174bcd23ab6b47d64eb4eb0f7944ca2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62845541"
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
- [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)
- [Elemente](../designers/elements-xelement-dynamic-property.md)