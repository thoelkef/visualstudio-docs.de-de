---
title: "&#39;Element&#39; (dynamische &#39;XElement&#39;-Eigenschaft) | Microsoft Docs"
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
  - "XElement.Element"
apitype: "Assembly"
ms.assetid: c6c25b8d-a1da-41ff-aeff-867ff1dcf749
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &#39;Element&#39; (dynamische &#39;XElement&#39;-Eigenschaft)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ermittelt einen Indexer, der zum Abrufen der Instanz des untergeordneten Elements verwendet wird, die dem angegebenen erweiterten Namen entspricht.  
  
## Syntax  
  
```  
elem.Element[{namespaceName}localName]  
```  
  
## Eigenschaftswert\/Rückgabewert  
 Indexer des Typs `XElement Item(String expandedName)`.Dieser Indexer nimmt einen erweiterten Namensparameter und gibt das zugehörige <xref:System.Xml.Linq.XElement> oder, wenn kein Element mit dem angegebenen Namen existiert, `null` zurück.  
  
## Hinweise  
 Diese Eigenschaft entspricht der <xref:System.Xml.Linq.XContainer.Element%2A>\-Methode der <xref:System.Xml.Linq.XContainer?displayProperty=fullName>\-Klasse.  
  
## Siehe auch  
 <xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=fullName>   
 [Dynamische Eigenschaften der 'XElement'\-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)