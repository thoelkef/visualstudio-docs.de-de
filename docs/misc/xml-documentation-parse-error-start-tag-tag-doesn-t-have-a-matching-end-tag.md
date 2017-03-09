---
title: "Analysefehler in XML-Dokumentation: F&#252;r das Starttag &quot;&lt;Tag&gt;&quot; ist kein entsprechendes Endtag vorhanden. | Microsoft Docs"
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
  - "vbc42316"
  - "BC42316"
helpviewer_keywords: 
  - "BC42316"
ms.assetid: 45b68176-ebf6-43af-820e-6801aabb6c57
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Analysefehler in XML-Dokumentation: F&#252;r das Starttag &quot;&lt;Tag&gt;&quot; ist kein entsprechendes Endtag vorhanden.
Analysefehler in XML\-Dokumentation: Für das Starttag "\<Tag\>" ist kein entsprechendes Endtag vorhanden. Der XML\-Kommentar wird ignoriert.  
  
 Der XML\-Kommentar enthält ein Starttag, jedoch keine entsprechendes Endtag.  
  
 **Fehler\-ID:** BC42316  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie ein Endtag hinzu, das dem Starttag entspricht.  
  
     Oder...  
  
-   Wenn das Tag keinen inneren Text \(z. B. [\<seealso\>](../Topic/%3Cseealso%3E%20\(Visual%20Basic\).md)\) enthält, geben Sie vor der schließenden Winkelklammer einen Schrägstrich ein.  
  
## Siehe auch  
 [XML Comment Tags](/dotnet/visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments)   
 [Documenting Your Code with XML](/dotnet/visual-basic/programming-guide/program-structure/documenting-your-code-with-xml)