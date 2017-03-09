---
title: "&#39;End Function&#39; muss ein entsprechendes &#39;Function&#39; voranstehen. | Microsoft Docs"
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
  - "bc30430"
  - "vbc30430"
helpviewer_keywords: 
  - "BC30430"
ms.assetid: de66a6b4-0321-45c2-aca0-87d2b4244b31
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Function&#39; muss ein entsprechendes &#39;Function&#39; voranstehen.
Im Code befindet sich eine `End Function`\-Anweisung ohne entsprechende vorhergehende `Function`\-Prozedurdefinition.  
  
 **Fehler\-ID:** BC30430  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die `End Function`\-Anweisung, falls sie redundant ist.  
  
2.  Geben Sie die fehlende `Function`\-Prozedur an, falls diese fehlt.  
  
3.  Verschieben Sie `End Function` an die entsprechende Stelle im Code.  
  
## Siehe auch  
 [Function\-Prozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/function-procedures)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)