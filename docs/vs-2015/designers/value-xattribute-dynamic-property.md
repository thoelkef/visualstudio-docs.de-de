---
title: Value (dynamische XAttribute-Eigenschaft) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e9a31b4c4182ed67a3e67d3c25c2c5ccf50e083f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664048"
---
# <a name="value-xattribute-dynamic-property"></a>Value (dynamische XAttribute-Eigenschaft)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName> [Attribut](../designers/attribute-xelement-dynamic-property.md) für [dynamische Eigenschaften der XAttribute-Klasse](../designers/xattribute-class-dynamic-properties.md)
