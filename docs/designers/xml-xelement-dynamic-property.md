---
title: Xml (dynamische XElement-Eigenschaft)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a69245a875d0c1df1942af12afaacc5a9ffc34b
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39080836"
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