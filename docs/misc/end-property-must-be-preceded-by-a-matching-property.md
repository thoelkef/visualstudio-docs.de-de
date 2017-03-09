---
title: "&#39;End Property&#39; muss ein entsprechendes &#39;Property&#39; voranstehen. | Microsoft Docs"
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
  - "vbc30431"
  - "bc30431"
helpviewer_keywords: 
  - "BC30431"
ms.assetid: b1e02d97-b38a-4acf-b351-1726f17a0051
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;End Property&#39; muss ein entsprechendes &#39;Property&#39; voranstehen.
Eine `End Property`\-Anweisung tritt ohne die entsprechende vorangehende `Property`\-Deklaration in Ihrem Code auf.  
  
 **Fehler\-ID:** BC30431  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die `End Property`\-Anweisung, falls sie redundant ist.  
  
-   Geben Sie die fehlende `Property`\-Prozedur an, falls diese fehlt.  
  
-   Verschieben Sie `End Property` an die entsprechende Stelle im Code.  
  
## Siehe auch  
 [NICHT IM BUILD: Eigenschaften und Eigenschaftenprozeduren](http://msdn.microsoft.com/de-de/23e2a1ec-7e9d-4109-8940-c703d981077b)   
 [End \<keyword\> Statement](../Topic/End%20%3Ckeyword%3E%20Statement%20\(Visual%20Basic\).md)