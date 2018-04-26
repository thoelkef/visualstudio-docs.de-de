---
title: Value (dynamische XAttribute-Eigenschaft)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 19808b10c64b469d3d9191fa2e4fc282d7696c5f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="value-xattribute-dynamic-property"></a>Value (dynamische XAttribute-Eigenschaft)

Ruft den Wert des XML-Attributs ab oder legt ihn fest.

## <a name="syntax"></a>Syntax

```
attrib.Value
```

## <a name="property-valuereturn-value"></a>Eigenschaftswert/Rückgabewert

Ein <xref:System.String>-Objekt, das den Wert dieses Attributs enthält.

## <a name="exceptions"></a>Ausnahmen

|Ausnahmetyp|Bedingung|
|--------------------|---------------|
|<xref:System.ArgumentNullException>|Wenn dieser Ausnahmetyp festgelegt wird, ist `value` `null`.|

## <a name="remarks"></a>Hinweise

Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XAttribute.Value%2A>-Eigenschaft der <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>-Klasse, wobei diese dynamische Eigenschaft auch Änderungsbenachrichtigungen unterstützt.

## <a name="see-also"></a>Siehe auch

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [Dynamische Eigenschaften der XAttribute-Klasse](../designers/xattribute-class-dynamic-properties.md)
- [Attribut](../designers/attribute-xelement-dynamic-property.md)