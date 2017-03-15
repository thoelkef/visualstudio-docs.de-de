---
title: "Ein Konstruktor muss als &#39;Sub&#39; und nicht als &#39;Function&#39; deklariert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30493"
  - "vbc30493"
helpviewer_keywords: 
  - "BC30493"
ms.assetid: bcacfd4b-cac0-4ad3-a6df-5fb37c189e8f
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Ein Konstruktor muss als &#39;Sub&#39; und nicht als &#39;Function&#39; deklariert werden.
Sie haben versucht, eine `Function New` zu deklarieren. Konstruktoren müssen als `Sub New` deklariert werden.  
  
 **Fehler\-ID:** BC30493  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie `Sub` anstelle von `Function`.  
  
## Siehe auch  
 [Sub Statement](/dotnet/visual-basic/language-reference/statements/sub-statement)