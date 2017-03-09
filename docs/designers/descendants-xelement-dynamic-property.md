---
title: "&#39;Descendants&#39; (dynamische &#39;XElement&#39;-Eigenschaft) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9611d00f-23bf-444b-ab0c-f30701bfc13d
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &#39;Descendants&#39; (dynamische &#39;XElement&#39;-Eigenschaft)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sucht nach einem Indexer, der zum Abrufen aller Nachfolgerelemente des aktuellen Elements verwendet wird, die dem angegebenen erweiterten Namen entsprechen.  
  
## Syntax  
  
```  
elem.Descendants[{namespaceName}localName]  
```  
  
## Eigenschaftswert\/Rückgabewert  
 Indexer des Typs `IEnumerable<XElement> Item(String expandedName)`.Dieser Indexer nimmt den erweiterten Namen der angegebenen Nachfolgerelemente und gibt die passenden untergeordneten Elemente in einer <xref:System.Collections.IEnumerable>`<`<xref:System.Xml.Linq.XElement>`>`\-Auflistung zurück.  
  
## Hinweise  
 Diese Eigenschaft ist identisch mit der <xref:System.Xml.Linq.XContainer.Descendants%28System.Xml.Linq.XName%29?displayProperty=fullName>\-Methode der <xref:System.Xml.Linq.XContainer>\-Klasse.  
  
 Die Elemente in der zurückgegebenen Auflistung sind in derselben Reihenfolge aufgeführt wie im XML\-Quelldokument.  
  
 Diese Eigenschaft verwendet die verzögerte Ausführung.  
  
## Siehe auch  
 [Dynamische Eigenschaften der 'XElement'\-Klasse](../designers/xelement-class-dynamic-properties.md)   
 [Elements](../designers/elements-xelement-dynamic-property.md)