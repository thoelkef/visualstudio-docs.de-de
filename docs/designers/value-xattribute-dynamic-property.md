---
title: "&#39;Value&#39; (dynamische &#39;XAttribute&#39;-Eigenschaft) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XAttribute.Value"
apitype: "Assembly"
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# &#39;Value&#39; (dynamische &#39;XAttribute&#39;-Eigenschaft)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ruft den Wert des XML\-Attributs ab oder legt ihn fest.  
  
## Syntax  
  
```  
attrib.Value   
```  
  
## Eigenschaftswert\/Rückgabewert  
 Eine <xref:System.String>, die den Wert dieses Attributs enthält.  
  
## Ausnahmen  
  
|Ausnahmetyp|Bedingung|  
|-----------------|---------------|  
|<xref:System.ArgumentNullException>|Wenn dieser Ausnahmetyp festgelegt wird, ist `value``null`.|  
  
## Hinweise  
 Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XAttribute.Value%2A>\-Eigenschaft der <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>\-Klasse, wobei diese dynamische Eigenschaft auch Änderungsbenachrichtigungen unterstützt.  
  
## Siehe auch  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [Dynamische Eigenschaften der 'Xattribute'\-Klasse](../designers/xattribute-class-dynamic-properties.md)   
 [Attribut](../designers/attribute-xelement-dynamic-property.md)