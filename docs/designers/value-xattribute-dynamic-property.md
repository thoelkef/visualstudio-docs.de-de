---
title: Value (dynamische XAttribute-Eigenschaft)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5ab4711d0165511aaf5934eeab1a81308fc3084
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031119"
---
# <a name="value-xattribute-dynamic-property"></a>Value (dynamische XAttribute-Eigenschaft)

Ruft den Wert des XML-Attributs ab oder legt ihn fest.

## <a name="syntax"></a>Syntax

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein <xref:System.String>-Objekt, das den Wert dieses Attributs enthält.

## <a name="exceptions"></a>Ausnahmen

|Ausnahmetyp|Bedingung|
| - |---------------|
|<xref:System.ArgumentNullException>|Wenn dieser Ausnahmetyp festgelegt wird, ist `value` `null`.|

## <a name="remarks"></a>Hinweise

Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XAttribute.Value%2A>-Eigenschaft der <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>-Klasse, wobei diese dynamische Eigenschaft auch Änderungsbenachrichtigungen unterstützt.

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Dynamische Eigenschaften der XAttribute-Klasse](../designers/xattribute-class-dynamic-properties.md)
- [Attribut](../designers/attribute-xelement-dynamic-property.md)