---
title: Element (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Element
apitype: Assembly
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bf8d964a41193d1db845a608749b0ca671dd9349
ms.sourcegitcommit: db680e8fa8066f905e7f9240342ece7ab9259308
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2018
ms.locfileid: "37924052"
---
# <a name="element-xelement-dynamic-property"></a>Element (dynamische XElement-Eigenschaft)

Ermittelt einen Indexer, der zum Abrufen der Instanz des untergeordneten Elements verwendet wird, die dem angegebenen erweiterten Namen entspricht.

## <a name="syntax"></a>Syntax

```xaml
elem.Element[{namespaceName}localName]
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Indexer des Typs `XElement Item(String expandedName)`. Dieser Indexer nimmt einen erweiterten Namensparameter und gibt das zugehörige <xref:System.Xml.Linq.XElement> oder, wenn kein Element mit dem angegebenen Namen existiert, `null` zurück.

## <a name="remarks"></a>Hinweise

Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XContainer.Element%2A>-Methode der <xref:System.Xml.Linq.XContainer?displayProperty=fullName>-Klasse.

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>
- [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)
- [Elemente](../designers/elements-xelement-dynamic-property.md)