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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2b83e4a208553b0ad732cfe927aec02b47e389dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187507"
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
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Dynamische Eigenschaften der XAttribute-Klasse](../designers/xattribute-class-dynamic-properties.md)   
 [Attribut](../designers/attribute-xelement-dynamic-property.md)
