---
title: "&#39;Xml&#39; (dynamische &#39;XElement&#39;-Eigenschaft) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "XElement.Xml"
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &#39;Xml&#39; (dynamische &#39;XElement&#39;-Eigenschaft)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ruft den unformatierten XML\-Inhalt des Elements ab.  
  
## Syntax  
  
```  
elem.Xml  
```  
  
## Eigenschaftswert\/Rückgabewert  
 <xref:System.String>, die den unformatierten XML\-Inhalt des Elements darstellt.  
  
## Hinweise  
 Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29>\-Methode der <xref:System.Xml.Linq.XNode?displayProperty=fullName>\-Klasse, wobei der `SaveOptions`\-Parameter auf <xref:System.Xml.Linq.SaveOptions> festgelegt ist.  
  
## Siehe auch  
 [Dynamische Eigenschaften der 'XElement'\-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Wert](../designers/value-xelement-dynamic-property.md)