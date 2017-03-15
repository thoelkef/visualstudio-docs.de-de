---
title: "Der XML-Kommentar kann nicht mehrere Male auf einen teilweisen &lt;Typ&gt; angewendet werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42314"
  - "vbc42314"
helpviewer_keywords: 
  - "BC42314"
ms.assetid: 23c76238-843a-44fe-88b7-25e604ee924b
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der XML-Kommentar kann nicht mehrere Male auf einen teilweisen &lt;Typ&gt; angewendet werden.
Der XML\-Kommentar kann nicht mehrere Male auf einen teilweisen \<Typ\> angewendet werden. XML\-Kommentare für \<Typ\> werden ignoriert.  
  
 Ein XML\-Kommentarblock kann nur oberhalb eines Teils eines partiellen Typs angezeigt werden.  
  
 Wenn ein XML\-Kommentarblock über mehr als einem Teil eines partiellen Typs angezeigt wird, wird diese Warnung für jeden Kommentarblock erstellt, und der XML\-Kommentar der obersten Ebene wird ignoriert.  
  
 **Fehler\-ID:** BC42314  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die überflüssigen Kommentarblöcke.  
  
## Siehe auch  
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)