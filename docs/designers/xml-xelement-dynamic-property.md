---
title: Xml (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c93aaf3b43a930fe88020738460ec131972a205a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633525"
---
# <a name="xml-xelement-dynamic-property"></a>Xml (dynamische XElement-Eigenschaft)

Ruft den unformatierten XML-Inhalt des Elements ab.

## <a name="syntax"></a>Syntax

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

<xref:System.String>, die den unformatierten XML-Inhalt des Elements darstellt.

## <a name="remarks"></a>Anmerkungen

Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)>-Methode der <xref:System.Xml.Linq.XNode?displayProperty=fullName>-Klasse, wobei der `SaveOptions`-Parameter auf <xref:System.Xml.Linq.SaveOptions> festgelegt ist.

## <a name="see-also"></a>Siehe auch

- [Dynamische Eigenschaften der XElement-Klasse](../designers/attribute-xelement-dynamic-property.md)
- [Wert](../designers/value-xelement-dynamic-property.md)