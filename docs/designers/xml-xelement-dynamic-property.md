---
title: Xml (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d58dea02a45ccc84e7829da2acdb479eb17dda3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931246"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (dynamische XElement-Eigenschaft)

Ruft den unformatierten XML-Inhalt des Elements ab.

## <a name="syntax"></a>Syntax

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

<xref:System.String>, die den unformatierten XML-Inhalt des Elements darstellt.

## <a name="remarks"></a>Hinweise

Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)>-Methode der <xref:System.Xml.Linq.XNode?displayProperty=fullName>-Klasse, wobei der `SaveOptions`-Parameter auf <xref:System.Xml.Linq.SaveOptions> festgelegt ist.

## <a name="see-also"></a>Siehe auch

- [Dynamische Eigenschaften der XElement-Klasse](../designers/xelement-class-dynamic-properties.md)
- [Wert](../designers/value-xelement-dynamic-property.md)