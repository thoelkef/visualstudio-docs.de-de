---
title: "Der XML-Kommentar enth&#228;lt ein Tag mit dem cref-Attribut &quot;&lt;Attribut&gt;&quot;, das nicht aufgel&#246;st werden konnte | Microsoft Docs"
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
  - "bc42309"
  - "vbc42309"
helpviewer_keywords: 
  - "BC42309"
ms.assetid: c9f3cfa5-565f-48bf-8616-cfb25d24f89e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der XML-Kommentar enth&#228;lt ein Tag mit dem cref-Attribut &quot;&lt;Attribut&gt;&quot;, das nicht aufgel&#246;st werden konnte
Der XML\-Kommentar enthält ein Tag mit dem cref\-Attribut "\<Attribut\>", das nicht aufgelöst werden konnte. Der XML\-Kommentar wird ignoriert.  
  
 Tags können über ein `cref`\-Attribut verfügen, das durch die Angabe des relativen Namens des Bezeichners einen Link zu einem anderen XML\-Element festlegt. Bei der Kompilierung ersetzt der Compiler den Wert durch den qualifizierten XML\-Bezeichner für den Wert, auf den der Benutzer zeigt. Der Compiler verwendet seine normalen Auflösungsregeln beim Suchen des Typs oder Members.  
  
 **Fehler\-ID:** BC42309  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass das `cref`\-Attribut auf ein gültiges Codeelement verweist.  
  
## Siehe auch  
 [How to: Create XML Documentation](../Topic/How%20to:%20Create%20XML%20Documentation%20in%20Visual%20Basic.md)   
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)