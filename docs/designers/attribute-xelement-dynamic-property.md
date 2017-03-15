---
title: "&#39;Attribute&#39; (dynamische &#39;XElement&#39;-Eigenschaft) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# &#39;Attribute&#39; (dynamische &#39;XElement&#39;-Eigenschaft)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sucht nach einem Indexer, der zum Abrufen der Attributinstanz verwendet wird, die dem angegebenen erweiterten Namen entspricht.  
  
## Syntax  
  
```  
elem.Attribute[{namespaceName}attribName]  
```  
  
## Eigenschaftswert\/Rückgabewert  
 Indexer des Typs `XAttribute Item(String expandedName)`.Dieser Indexer nimmt den erweiterten Namen des angegebenen Attributs und gibt das zugehörige <xref:System.Xml.Linq.XAttribute> zurück. Wenn kein Attribut mit dem angegebenen Namen existiert, wird `null` zurückgegeben.  
  
## Hinweise  
 Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XElement.Attribute%2A>\-Methode der <xref:System.Xml.Linq.XElement?displayProperty=fullName>\-Klasse.  
  
## Siehe auch  
 <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>   
 [Dynamische Eigenschaften der 'XElement'\-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Wert](../designers/value-xattribute-dynamic-property.md)